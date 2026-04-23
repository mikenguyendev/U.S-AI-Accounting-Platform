# Massachusetts (MA) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/MA.md#section-id}}` directives.**

**State:** Massachusetts
**Tax Authority:** Massachusetts Department of Revenue (DOR), Department of Unemployment Assistance (DUA), MA Paid Family and Medical Leave (PFML)
**Last Updated:** 2026-04-22

> **⚠️ MILLIONAIRE TAX (2023):** MA added 4% surtax on income >$1M (effective Jan 2023). Combined với 5% flat = 9% on income >$1M (Schedule 4% adds to base). High burden cho high-income owners.

---

## tax-obligations

### Key Massachusetts Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **MA Corporate Excise Tax (C-Corp)** | 8% on net income + $2.60 per $1,000 net worth (min $456) | DOR | March 15 / April 15 |
| **MA Personal Income Tax** | 5% flat | DOR | April 15 (Form 1) |
| **MA Millionaire Tax** | 4% surtax on income >$1,000,000 | DOR | April 15 (Schedule 4%) |
| **MA Sales & Use Tax** | 6.25% statewide (uniform) | DOR | Monthly/Quarterly |
| **MA SUI (Unemployment)** | 0.94%–14.37% on first $15,000 | DUA | Quarterly (DUA-1) |
| **MA PFML (Paid Family & Medical Leave)** | 0.88% combined (employer + employee splits) on $168,600 cap | DFML | Quarterly |
| **MA Workforce Training Fund** | 0.056% | DUA | Quarterly |
| **MA Health Insurance Responsibility** | $0 (penalty for individuals not having coverage — varies) | DOR | At return |
| **Workers' Compensation** | MANDATORY for all employers (1+ employee) | DIA | Per pay period |

> **⚠️ MA PFML mandatory** since 2019 — premium 0.88% (for 2025; 2026 rate may adjust). Split: typically employer pays 60% medical leave portion, employee pays family leave portion.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 MA SUI return | DUA-1 |
| **March 15** | MA S-Corp / Partnership return | Form 355S, Form 3 |
| **April 15** | MA C-Corp Corporate Excise Tax | Form 355 |
| **April 15** | MA Personal Income Tax (Form 1) | Form 1 |
| **April 30** | Q1 MA SUI return + PFML | DUA-1 |
| **June 15** | Q2 MA personal estimated tax | Form 1-ES |
| **July 31** | Q2 MA SUI return + PFML | DUA-1 |
| **September 15** | Q3 MA personal estimated tax | Form 1-ES |
| **October 31** | Q3 MA SUI return + PFML | DUA-1 |
| **January 15** | Q4 MA personal estimated tax | Form 1-ES |

**Sales tax filing:** Monthly (most), Quarterly (smaller).
**Sales tax due:** 20th/30th of month following filing period (depends on liability).

---

## upcoming-deadlines

**Next 12 months MA-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 personal estimated (prior year) |
| Jan 31 | Q4 DUA-1 |
| **Mar 15** | MA S-Corp / Partnership |
| **Apr 15** | MA C-Corp + Personal Income |
| Apr 30 | Q1 DUA-1 + PFML |
| Jun 15 | Q2 personal estimated |
| Jul 31 | Q2 DUA-1 + PFML |
| Sep 15 | Q3 personal estimated |
| Oct 31 | Q3 DUA-1 + PFML |

---

## critical-reminders

- ⚠️ **Millionaire Tax (4% surtax) on income >$1M** — added 2023, total can be 9% on top dollar
- ⚠️ **MA Corporate Excise = 8% income + $2.60 per $1,000 net worth** — dual base
- ⚠️ **PFML mandatory since 2019** — 0.88% combined premium, complex split
- ⚠️ **Sick Time Law** — 40 hours/year mandatory (no exemption for small employers)
- ⚠️ **MA minimum wage $15.00/hour (2024)** — verify 2026; tipped $6.75 (2024)
- ⚠️ **Workers' Comp mandatory** for any employer (1+ employee)
- ⚠️ **Sales tax uniform 6.25%** statewide (no local additions)
- ⚠️ **MA Wage Act** has triple damages + attorney's fees for wage violations — extremely employee-friendly
- ⚠️ **Independent Contractor ABC test** — strictest in nation (all 3 prongs must pass)
- ⚠️ **PTE Excise Tax election** available — SALT cap workaround
- ⚠️ **Boston has additional 0.75% local meals tax** (state 6.25% + local = 7%)
- ⚠️ **Property tax** lower than NJ but still significant

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Millionaire Tax not calculated for income >$1M → underpayment + penalty
- ⚠️ MA employer not registered with PFML → uncollected premiums + employee benefit issues
- ⚠️ Worker classified as 1099 doesn't pass ABC test (very strict in MA) → reclassify + back wages + treble damages
- ⚠️ MA Sick Time Law not honored → DOL complaint + back pay
- ⚠️ MA Wage Act violation → triple damages + attorney's fees automatic
- ⚠️ Sales tax permit missing → operating illegally
- ⚠️ Workers' Comp lapsed → criminal penalties + civil liability
- ⚠️ PTE Excise election deadline missed → no SALT workaround
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into MA → economic nexus
- ⚠️ Boston meals tax not collected → city tax violation
- ⚠️ MA minimum wage updates not applied Jan 1 → wage theft + penalties

---

## validation-rules

### MA-Specific Validation

- **Personal income tax:** 5% flat on all income (excluding capital gains 12% short-term, 5% long-term)
- **Millionaire Tax:** Add 4% to income >$1M (calculated via Schedule 4%)
- **Corporate Excise dual base:** Greater of (8% × net income) OR ($2.60 per $1,000 net worth)
- **Min Corporate Excise:** $456
- **PTE Excise election:** Annual, by extended due date of partnership return
- **MA ABC test (worker classification):** All 3 must be true:
  - (A) Free from control
  - (B) Service outside usual course of business
  - (C) Independently established trade
- **Sales tax exemptions:** Clothing under $175 (no tax), groceries (no tax), prescriptions, manufacturing
- **Sales tax sourcing:** Destination-based

---

## sales-tax

**Massachusetts Sales & Use Tax**

- **Authority:** MA Department of Revenue
- **Rate:** **6.25% uniform statewide** (no local sales tax)
- **Permit required:** Sales Tax Vendor Registration from DOR (free, online)
- **What's taxable:**
  - Tangible personal property
  - Some services (telecom, accommodations, security)
  - Prepared food (restaurants) — Boston adds 0.75% meal tax
  - Software (canned)
- **What's NOT taxable:**
  - Most professional services
  - Clothing under $175 per item (MA-unique exemption)
  - Groceries (unprepared)
  - Prescription drugs
  - Newspapers, periodicals
  - Manufacturing machinery (with certificate)
- **Filing frequency:**
  - Monthly: liability >$1,200/year
  - Quarterly: $100-$1,200/year
  - Annual: <$100/year
- **Due date:** 20th of month following filing period (most); 30th for monthly with EFT

---

## estimated-tax

### MA Corporate Excise Tax (C-Corp)

For C-Corps owing >$1,000 in MA tax:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | March 15 | Form 355-7004 |
| Q2 | June 15 | Form 355-7004 |
| Q3 | September 15 | Form 355-7004 |
| Q4 | December 15 | Form 355-7004 |

### MA Personal Income Tax

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1-ES |
| Q2 | June 15 | Form 1-ES |
| Q3 | September 15 | Form 1-ES |
| Q4 | January 15 | Form 1-ES |

### PTE Excise Election

- MA pass-through entities can elect PTE Excise Tax (5%)
- SALT cap workaround
- Election made annually
- Quarterly entity-level estimated payments

**AI MUST when processing `estimated-tax` form for MA:**
1. Distinguish entity type
2. C-Corp: Form 355-7004 quarterly
3. Pass-through: depends on PTE election
4. Owners: Form 1-ES quarterly (include Millionaire Tax if income >$1M)
5. Verify PTE election status

---

## withholding-form

**MA Employee State Withholding Form: M-4**

- **Purpose:** Determines MA state income tax withholding
- **Default if no M-4:** Single, 0 exemptions
- **Update:** Employee can submit anytime
- **Companion form:** Federal W-4

**Required at hire:**
- Federal W-4 + MA M-4
- I-9 (within 3 days)
- New Hire Reporting via MA New Hire Reporting Center within 14 days

---

## withholding-tables

**MA Withholding Calculation:**

- Flat 5% on wages above exemption
- Plus 4% Millionaire Tax surtax on cumulative wages >$1M (rare for typical employees)
- Standard deduction varies

**Tools:**
- MA DOR Circular M (annually updated)
- Most payroll software handles automatically (MA + PFML + SUI)

**Special situations:**
- Bonuses: 5% supplemental (most cases)
- Out-of-state remote workers for MA employer: MA generally taxes wages of remote workers if employer is MA-based (subject to challenges and rule changes)

---

## payroll-taxes

### Employer-Side MA Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **MA SUI (Unemployment)** | 0.94%–14.37% | First $15,000 | New employer 1.45%-2.42% |
| **MA Workforce Training Fund** | 0.056% | First $15,000 | Mandatory all employers |
| **Employer Medical Assistance Contribution (EMAC)** | 0.34% | First $15,000 | New employers EMAC waived first 3 yrs |
| **MA PFML (Medical Leave portion)** | Varies (~0.42%) | First $168,600 (2026) | Employer pays 60% (most) |
| **MA PFML (Family Leave portion)** | Varies (~0.46%) | First $168,600 (2026) | EMPLOYEE pays 100% (typical) |
| **MA Income Tax PIT** | 5% flat | All wages above exemption | Employer withholds |

### New Employer Default Rates
- New employer SUI: ~1.45% Year 1 (some industries higher)
- MA minimum wage: $15.00/hour (2024) — verify 2026

### Quarterly Reporting
- **Form DUA-1** — Quarterly Wage Report (combined)
- **PFML report** through MassTaxConnect
- Due: Last day of month after quarter end

### E-file
- Required for all MA employers
- Use MassTaxConnect (DOR) + EOLWD (DUA)

### Other MA Employment Requirements
- New Hire Reporting: 14 days
- Workers' Comp: MANDATORY (any employer)
- Sick Time Law: 40 hours/year accrued
- PFML: Up to 26 weeks combined
- Wage Act compliance: triple damages risk

---

## entity-specific-tax

### S-Corporation in MA
- **MA Corporate Excise Tax** — even pass-through S-Corps pay min $456 + property factor
- S-Corp pays 8% on net income (gross receipts >$9M) OR per receipt size
- Federal Form 1120-S still required
- Shareholders: 5% personal tax on K-1 (+ 4% if >$1M)

### C-Corporation in MA
- **MA Corporate Excise: 8% income + $2.60 per $1,000 net worth**
- Min: $456
- Form 355 due April 15

### LLC in MA
- If single-member: pass-through, no corp filing
- If multi-member: Form 3 (informational, no entity tax)
- LLC formation: $500 (highest in nation; MA Secretary of State)
- Annual Report: $500 (also high)
- Federal Form 1065/Schedule C

### Partnership in MA
- **No entity-level income tax** (pass-through)
- Federal Form 1065 + K-1s
- MA Form 3 informational

### Sole Proprietor in MA
- No entity tax filing
- MA personal income tax via Form 1
- Just federal Schedule C

### Out-of-State Entities Operating in MA
- Subject to MA Corporate Excise based on apportionment
- Sales tax nexus rules apply
- Foreign Qualification required (Form FA in MA)
