# 📅 COMPLIANCE CALENDAR GENERATOR

> **Mục đích:** Protocol cho AI Agent generate cá nhân hóa compliance calendar dựa trên `_BUSINESS_CONFIG.json`. Output: ICS calendar file + markdown deadline list cho instance folder.

**Version:** 1.0.0
**Last Updated:** 2026-04-22
**Companion docs:** [_MODULES/entity/](entity/), [_MODULES/state/](state/)

---

## 🎯 PURPOSE

Mỗi business mới onboarded có unique compliance calendar based on:
- Entity type (entity module deadlines)
- State of operation (state module deadlines)
- Has employees? (payroll filings)
- Multi-state nexus? (additional state filings)
- Fiscal year (calendar vs custom)
- Election status (PTE, S-election, etc.)

Manual tracking → easy to miss. Calendar generator solves this.

---

## 📋 INPUT

Read from `_INSTANCES/{instance_id}/_BUSINESS_CONFIG.json`:

```json
{
  "company": {
    "entity_type": "S-Corp",
    "industry": "Service"
  },
  "operations": {
    "state_of_operation": "CA",
    "additional_states": ["TX"]
  },
  "fiscal_year": {
    "year": 2026,
    "start_date": "2026-01-01",
    "is_calendar_year": true
  },
  "employees": [/* if non-empty → payroll deadlines */],
  "compliance_status": {
    "ein_obtained": true,
    "boi_filed": true
  }
}
```

---

## 📤 OUTPUT

### File 1: `_INSTANCES/{instance_id}/COMPLIANCE_CALENDAR_FY{year}.md`

Markdown file with:
- Year-at-a-glance table
- Monthly deadline breakdown
- Color-coded urgency (🔴 critical, 🟡 important, ⚪ informational)
- Filing checklist with checkboxes

### File 2: `_INSTANCES/{instance_id}/COMPLIANCE_CALENDAR_FY{year}.ics` (optional)

iCalendar file importable to Google Calendar / Outlook / Apple Calendar:
- Each deadline = calendar event
- Reminder 7 days before + 1 day before
- All-day events
- Categorized by tag (Federal, State, Payroll, Sales Tax)

---

## 🔄 GENERATION ALGORITHM

### Step 1: Build Master Deadline List

```
deadlines = []

# Federal deadlines from entity module
deadlines += parse_entity_module(config.entity_type)#federal-deadlines

# Federal payroll deadlines (if has employees)
if config.employees.length > 0 OR config.compliance_status.payroll_provider != null:
    deadlines += {
        "Apr 30: Form 941 Q1",
        "Jul 31: Form 941 Q2",
        "Oct 31: Form 941 Q3",
        "Jan 31: Form 941 Q4 + W-2 + W-3 + 1099 + Form 940"
    }

# Primary state deadlines from state module
deadlines += parse_state_module(config.state_of_operation)#deadlines

# Additional states (multi-state nexus)
for state in config.additional_states:
    deadlines += parse_state_module(state)#deadlines (filtered to non-payroll)

# Compliance setup deadlines (one-time, only if not yet done)
if !config.compliance_status.ein_obtained:
    deadlines += "ASAP: Apply for EIN (Form SS-4)"
if !config.compliance_status.boi_filed AND entity_type IN ['Corp', 'LLC']:
    deadlines += "Within 90 days of formation: File FinCEN BOI Report"
```

### Step 2: Compute Specific Dates

For each deadline, resolve date for current fiscal year:
```
today = TODAY
fy_year = config.fiscal_year.year
prior_fy = fy_year - 1

# Examples:
"March 15" → March 15, fy_year (or skipped if past)
"April 30" → April 30, fy_year
"Jan 31 (next year)" → Jan 31, fy_year + 1
```

### Step 3: Apply Filters

Skip deadlines where:
- Date is in past (>30 days ago)
- Not applicable to entity (vd: Form 1120 cho S-Corp)
- Not applicable to current setup (vd: payroll deadlines if no employees)

### Step 4: Categorize & Prioritize

Each deadline tagged:
- **Category:** Federal | State | Payroll | Sales Tax | Setup | One-Time
- **Urgency:** 🔴 (≤7 days), 🟡 (8-30 days), ⚪ (>30 days, future)

### Step 5: Render Markdown

Output structure:
```markdown
# 📅 Compliance Calendar — {Company Name} FY{year}

**Generated:** {today}
**Entity:** {entity_type}
**State(s):** {state_of_operation} {+ additional}
**Status:** {compliance_summary}

---

## 🚨 Critical Next 30 Days

| Date | Days Away | Deadline | Action |
|------|:---------:|----------|--------|
| ... | ... | ... | ... |

---

## 📊 Year-at-a-Glance

| Month | Federal | State | Payroll | Sales Tax |
|-------|---------|-------|---------|-----------|
| Jan | W-2/W-3/1099, Form 940, Q4 941 | (state-specific) | Q4 SUTA | Monthly filing |
| Feb | — | — | — | Monthly filing |
| Mar | Form 1120-S/1065 + K-1s | (state-specific) | — | Monthly filing |
| ... | ... | ... | ... | ... |

---

## 📋 Detailed Monthly Breakdown

### January {year}
- [ ] **Jan 15** — Q4 personal estimated tax (1040-ES, prior year)
- [ ] **Jan 31** — Issue W-2 to employees, W-3 to SSA
- [ ] **Jan 31** — Issue 1099-NEC to contractors (>$600)
- [ ] **Jan 31** — Form 940 (FUTA annual)
- [ ] **Jan 31** — Form 941 (Q4 payroll)
- [ ] **Jan 31** — {State-specific Q4 deadlines}

### February {year}
- [ ] {Sales tax filing if monthly}

### March {year}
- [ ] **Mar 15** — Form 1120-S + K-1s (if S-Corp)
- [ ] **Mar 15** — Form 1065 + K-1s (if Partnership/LLC-multi)
- [ ] **Mar 15** — {State equivalents}
- [ ] {Sales tax filing}

... (continue all 12 months)

---

## ⚠️ Compliance Setup Checklist (One-Time)

- [{✅ if EIN obtained}] EIN obtained (Form SS-4)
- [{✅ if BOI filed}] FinCEN BOI Report filed
- [{✅ if state registered}] State registration completed
- [{✅ if WC insurance}] Workers' Comp insurance
- ...

---

## 🔗 Reference Links

- [Entity Module](../../_MODULES/entity/{entity_type}.md)
- [State Module](../../_MODULES/state/{state}.md)
- [State Matrix CSV](../../_MODULES/state/_state_matrix.csv)
- [IRS Forms](https://www.irs.gov/forms-instructions)
- [{State} DOR](state-specific link)

---

*Generated by AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
```

---

## 📅 ICS FILE FORMAT (Optional)

For users who want calendar import:

```
BEGIN:VCALENDAR
VERSION:2.0
PRODID:-//AI Accounting Template//Compliance Calendar//EN
CALSCALE:GREGORIAN
METHOD:PUBLISH

BEGIN:VEVENT
UID:{unique-id}@aiaccounting.template
DTSTART;VALUE=DATE:20260315
DTEND;VALUE=DATE:20260316
SUMMARY:🔴 Form 1120-S + K-1s due
DESCRIPTION:S-Corporation income tax return + Schedule K-1s to shareholders. File via IRS e-Services or paper. Late penalty: $220/shareholder/month.
CATEGORIES:Federal,Tax,Critical
BEGIN:VALARM
TRIGGER:-P7D
ACTION:DISPLAY
DESCRIPTION:Form 1120-S due in 7 days
END:VALARM
BEGIN:VALARM
TRIGGER:-P1D
ACTION:DISPLAY
DESCRIPTION:Form 1120-S due tomorrow
END:VALARM
END:VEVENT

... (repeat for each deadline)

END:VCALENDAR
```

---

## 🤖 AI AGENT INVOCATION

**User trigger:** "Generate compliance calendar cho {company}"

**AI Agent response:**
1. Read `_INSTANCES/{instance_id}/_BUSINESS_CONFIG.json`
2. Load entity module (`_MODULES/entity/{entity_type}.md`)
3. Load primary state module (`_MODULES/state/{state}.md`)
4. Load additional state modules if multi-state
5. Build master deadline list per algorithm
6. Render markdown calendar to `_INSTANCES/{instance_id}/COMPLIANCE_CALENDAR_FY{year}.md`
7. Optionally render ICS file
8. Report summary to user:
   ```
   ✅ Compliance Calendar Generated

   File: _INSTANCES/{instance_id}/COMPLIANCE_CALENDAR_FY{year}.md
   Total deadlines tracked: {N}

   🚨 Critical next 30 days:
   - {Deadline 1} on {date} ({days} days)
   - {Deadline 2} on {date} ({days} days)

   ⚠️ Compliance gaps:
   - {Gap 1}
   - {Gap 2}

   Recommend: Review file + import ICS to your calendar.
   ```

---

## 🔄 REGENERATION TRIGGERS

User should regenerate calendar when:
- Start of new fiscal year (annual refresh)
- After config changes (new entity, new state, new employees)
- After major deadline missed (shift forward)
- Tax law changes (annual update of state/entity modules)

**Idempotency:** Same config → same output (within same day; TODAY changes daily).

---

## 📚 EXAMPLE — S-Corp in CA, Calendar Year FY2026

Sample output excerpt cho S-Corp / CA / FY2026:

```markdown
# 📅 Compliance Calendar — Acme Service Group FY2026

**Generated:** 2026-04-22
**Entity:** S-Corp
**State(s):** CA
**Status:** EIN obtained ✅, BOI filed ✅, no employees yet 🟡

---

## 🚨 Critical Next 30 Days

| Date | Days Away | Deadline | Action |
|------|:---------:|----------|--------|
| Apr 30, 2026 | 8 | Form 941 Q1 (if employer) | N/A — no employees |
| May 15, 2026 | 23 | None | — |

---

## 📊 Year-at-a-Glance

(This was past for 2026 deadlines: Mar 15 Form 1120-S already passed)

---

## 📋 Remaining 2026 Deadlines

### June 2026
- [ ] **Jun 15** — Q2 Federal Estimated Tax (1040-ES) for shareholders
- [ ] **Jun 15** — Q2 CA Estimated Tax (Form 540-ES) for shareholders

### September 2026
- [ ] **Sep 15** — Q3 Federal Estimated Tax (1040-ES)
- [ ] **Sep 15** — Q3 CA Estimated Tax
- [ ] **Sep 15** — Form 1120-S extended (if extension filed)

### December 2026
- [ ] **Dec 15** — Q4 CA Estimated Tax (Form 100-ES for entities)

### January 2027
- [ ] **Jan 15** — Q4 Federal Estimated Tax (1040-ES)
- [ ] **Jan 31** — W-2/1099/Form 940/941 Q4 (if hired employees)

### March 2027
- [ ] **Mar 15** — **Form 1120-S FY2026 + K-1s**
- [ ] **Mar 15** — CA Form 100-S FY2026

### April 2027
- [ ] **Apr 15** — **CA $800 Franchise Tax FY2027**
- [ ] **Apr 15** — Q1 Estimated Tax (federal + CA)

---

## ⚠️ Compliance Setup Checklist

- [x] EIN obtained
- [x] FinCEN BOI Report filed
- [ ] State registration (CA Secretary of State)
- [ ] Workers' Comp insurance (if hiring)
- [ ] Sales tax permit (if applicable)
```

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
