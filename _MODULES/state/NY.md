# New York (NY) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/NY.md#section-id}}` directives.**

**State:** New York
**Tax Authority:** NY Department of Taxation and Finance, NY Department of Labor (NYSDOL), NY State Insurance Fund
**Last Updated:** 2026-04-22

> **⚠️ HIGH-COMPLEXITY STATE:** NY có nhiều layered taxes (state + city + Metropolitan Commuter Transportation Mobility Tax). NYC adds significant additional burden. Most complex state for payroll + entity tax planning.

---

## tax-obligations

### Key New York Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **NY Corporation Franchise Tax (C-Corp)** | 6.5% (general) or 7.25% (>$5M income) | DTF | March/April (Form CT-3) |
| **NY S-Corp Franchise Tax** | Fixed dollar minimum: $25–$4,500 (based on receipts) | DTF | March 15 (Form CT-3-S) |
| **NY LLC Filing Fee** | $25–$4,500 (based on gross income) | DTF | March 15 (Form IT-204-LL) |
| **NYC Business Corporation Tax** | 8.85% on entire net income (NYC business) | NYC Dept of Finance | April (Form NYC-2) |
| **NYC General Corporation Tax (S-Corps)** | 8.85% (NYC doesn't recognize S-Corp election) | NYC Dept of Finance | March (Form NYC-3L) |
| **NYC Unincorporated Business Tax (UBT)** | 4% on income >$95K (sole prop, partnership) | NYC Dept of Finance | April (Form NYC-202) |
| **NY State Income Tax (Personal)** | Progressive 4%–10.9% | DTF | April 15 (Form IT-201) |
| **NYC Personal Income Tax** | Progressive 3.078%–3.876% (additional, on top of NY state) | NYC | April 15 |
| **NY Sales Tax** | 4% state + up to 4.875% local (max 8.875% NYC) | DTF | Quarterly/Monthly |
| **NY State Income Tax Withholding** | Per IT-2104 | DTF | Per pay period |
| **NY SDI (Disability)** | $0.60/week max ($31.20/year) — employer can split with employee | NYSDOL | Per pay period |
| **NY PFL (Paid Family Leave)** | 0.388% of wages, max ~$354/year (2026) | NYSDOL | Per pay period (employee pays) |
| **NY SUTA (Unemployment)** | 0.525%–7.825% on first $12,500 wages (2026) | NYSDOL | Quarterly (NYS-45) |
| **NYC MCTMT** | 0.34% on payroll if NYC payroll >$312,500/quarter | DTF | Quarterly |

> **⚠️ CRITICAL:** NY has an **annual MTA Mobility Tax** if business operates in NYC metro area + has >$312,500 quarterly payroll.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 NY payroll return | NYS-45 |
| **March 15** | NY S-Corp / Partnership return | CT-3-S, IT-204 |
| **March 15** | NYC General Corp Tax (S-Corp) | NYC-3L |
| **April 15** | NY C-Corp tax return | CT-3 |
| **April 15** | NYC Business Corp Tax | NYC-2 |
| **April 15** | NY LLC Filing Fee | IT-204-LL |
| **April 15** | NYC UBT (sole prop, partnership) | NYC-202 |
| **April 15** | NY personal income tax | IT-201 |
| **April 30** | Q1 NY payroll return | NYS-45 |
| **June 15** | Q2 NY/NYC estimated tax | CT-400 (corp), IT-2105 (personal) |
| **July 31** | Q2 NY payroll return | NYS-45 |
| **September 15** | Q3 NY/NYC estimated tax | CT-400, IT-2105 |
| **October 31** | Q3 NY payroll return | NYS-45 |
| **December 15** | Q4 NY/NYC estimated tax (corp) | CT-400 |
| **January 15** | Q4 personal estimated tax | IT-2105 |

**Sales tax filing:** Quarterly default; Monthly if liability >$300K/quarter; Annual if <$3K/year.

---

## upcoming-deadlines

**Next 12 months NY-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 NYS-45 |
| **Mar 15** | NY S-Corp / Partnership returns |
| **Apr 15** | NY C-Corp + NYC Business Corp + LLC Fee + UBT + Personal IT-201 |
| Apr 30 | Q1 NYS-45 |
| Jun 15 | Q2 estimated tax (corp + personal) |
| Jul 31 | Q2 NYS-45 |
| Sep 15 | Q3 estimated tax |
| Oct 31 | Q3 NYS-45 |
| Dec 15 | Q4 corp estimated tax |
| Jan 15 (next yr) | Q4 personal estimated tax |

---

## critical-reminders

- ⚠️ **NYC adds 8.85% on top of NY state tax** — total entity tax can reach ~16% federal + state + city
- ⚠️ **NYC does NOT recognize S-Corp election** — NYC taxes S-Corps as C-Corps (NYC-3L, 8.85%)
- ⚠️ **MCTMT (Metro Commuter Mobility Tax)** if NYC payroll >$312,500/quarter — extra 0.34%
- ⚠️ **NY LLC Filing Fee mandatory** ($25-$4,500) on TOP of any income tax — annual
- ⚠️ **Pass-Through Entity Tax (PTET) election** — strongly recommended for SALT cap workaround (saves federal tax)
- ⚠️ **NYC UBT** — Sole Props and partnerships in NYC pay 4% on income >$95K
- ⚠️ **Sales tax in NYC = 8.875%** (4% state + 4.5% NYC + 0.375% MCTD)
- ⚠️ **NY Paid Family Leave** mandatory (0.388% of wages, employee pays via paycheck deduction)
- ⚠️ **NY Workers' Comp** — MANDATORY for any employer (no opt-out like TX)
- ⚠️ **NY State minimum wage** — $16.50/hour NYC + Long Island + Westchester (2025); $15.50 elsewhere — verify 2026 rates
- ⚠️ **NY Sick Leave** — 40-56 hours/year required, paid (depends on employer size)
- ⚠️ **NY HERO Act** — employer >10 employees must have airborne infectious disease prevention plan
- ⚠️ **Tax warrant** issued quickly for unpaid NY taxes — file lien against business + personal assets
- ⚠️ **Telecommuter rule (Convenience of Employer):** NY taxes income of remote workers if they work for NY-based employer (unless required by employer to work elsewhere)

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ S-Corp operating in NYC không file NYC-3L → NYC treats as C-Corp anyway, owes 8.85%
- ⚠️ LLC Fee (Form IT-204-LL) not filed by April 15 → $50/month penalty per K-1 partner
- ⚠️ Total NYC payroll >$312,500/quarter → MCTMT due (often missed)
- ⚠️ PTET election deadline: Federal extension deadline → MUST elect by Mar 15 of following year (annually)
- ⚠️ Sales tax permit not obtained → operating illegally in NY
- ⚠️ Workers' Comp not in place → automatic stop work order + per-day fines
- ⚠️ NYC employee but not paying NYC withholding → tax warrant
- ⚠️ Out-of-state remote worker for NY-based employer → "Convenience of Employer" rule applies (NY taxes wages)
- ⚠️ Multi-state nexus: $500K sales into NY → economic nexus, must file
- ⚠️ Tipped wages below minimum → check NY tip credit rules (varies by job category)
- ⚠️ NY sick leave not provided → fines $1,000+ per violation
- ⚠️ NY State Insurance Fund (SIF) audit issues — high risk for misclassified workers

---

## validation-rules

### NY-Specific Validation

- **PTET election deadline:** Must elect annually by March 15
- **NYC vs NY State:** Verify entity has NYC nexus before NYC filings (some entities only NY state)
- **Multi-state apportionment:** NY uses single sales factor for most industries
- **Convenience of Employer rule:** Remote workers for NY employer = NY-source wages (unless employer requires offsite)
- **NYC UBT:** Applies to unincorporated business income in NYC >$95K (sole prop + partnership)
- **Minimum wage by region:** NYC/LI/Westchester higher than rest of state — verify worksite
- **Tip credit:** Different by job (food service vs other)
- **Reciprocity:** NY does NOT have income tax reciprocity (CT, NJ, PA workers must file NY non-resident)

---

## sales-tax

**New York Sales & Use Tax**

- **Authority:** NY Department of Taxation and Finance
- **Base rate:** 4% state
- **Local taxes:** Up to 4.875% additional (NYC: 4.5% + 0.375% MCTD)
- **Total NYC rate:** 8.875%
- **Total range:** 7%–8.875% statewide
- **Permit required:** Certificate of Authority từ NY DTF (free, online)
- **What's taxable:**
  - Tangible personal property
  - Some services (telecom, hotels, parking, repair)
  - Prepared food (restaurants)
  - Digital goods (since 2008)
- **What's NOT taxable:**
  - Most professional services (legal, medical, consulting — careful exceptions)
  - Groceries (unprepared)
  - Prescription drugs
  - Clothing/footwear under $110/item
- **Filing frequency:**
  - Monthly: liability >$300K/quarter
  - Quarterly: default
  - Annual: <$3,000/year
- **Due date:** 20th of month following filing period

**Important:** Many services in NY ARE taxable — NOT typical "services exempt" assumption. Verify each service line.

---

## estimated-tax

### NY State Entity-Level Estimated Tax

**Required for entities owing >$1,000 NY tax:**

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | March 15 (S-Corp) / April 15 (C-Corp) | CT-400 |
| Q2 | June 15 | CT-400 |
| Q3 | September 15 | CT-400 |
| Q4 | December 15 | CT-400 |

**Calculation:** Generally 25% of expected annual tax each quarter.

### Personal Estimated Tax (Owner-Level)

- **Form IT-2105** quarterly: April 15, June 15, September 15, January 15
- Combined: NY state + NYC (if NYC resident)
- Safe harbor: 100% of prior year (110% if AGI >$150K)

### PTET (Pass-Through Entity Tax) Election — IMPORTANT

NY allows pass-through entities (S-Corp, partnership, LLC-multi) to elect entity-level state tax.
- Saves federal tax via SALT cap workaround
- Members get NY tax credit for entity-paid tax
- **MUST elect annually by March 15**
- Quarterly entity-level payments via Form CT-7-PT
- Generally beneficial for partnerships/S-Corps with NY-resident members

**AI MUST when processing `estimated-tax` form for NY:**
1. Check if PTET election made (changes payment routing)
2. C-Corp: file CT-400 quarterly
3. S-Corp/Partnership without PTET: members file IT-2105 personally
4. S-Corp/Partnership WITH PTET: entity files CT-7-PT quarterly
5. NYC residents: include NYC tax in personal estimates
6. Recommend CPA for any NY filing >$10K

---

## withholding-form

**NY Employee State Withholding Form: IT-2104**

- **Purpose:** Determines NY state income tax withholding (and NYC if applicable)
- **When required:** Every NY employee, signed at hire
- **NYC residents:** Same form, includes NYC withholding
- **Yonkers residents:** Same form, includes Yonkers tax
- **Default if no IT-2104:** Single, 0 allowances
- **Update:** Employee can submit anytime

**Companion forms required at hire:**
- Federal W-4
- I-9 (within 3 days)
- New Hire Reporting via NYSDOL within 20 days

---

## withholding-tables

**NY Withholding Calculation:**

Use NYS-50-T-NYS (state) and NYS-50-T-NYC (city) — annual updates.

- Progressive brackets: 4%–10.9% (NY state)
- Additional NYC: 3.078%–3.876%
- Yonkers: 16.75% of NY state withholding

**Tools:**
- NY DTF Withholding Estimator
- IT-2104 Worksheet
- Most payroll software handles NY + NYC + Yonkers automatically

**Special situations:**
- Bonuses: Aggregate method or supplemental rate (11.7% NY + city if applicable)
- Stock options: Special rules
- Out-of-state remote workers: Convenience of Employer rule applies

---

## payroll-taxes

### Employer-Side NY Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **NY SUI** | 0.525%–7.825% | First $12,500 (2026) | New employer ~3.4% |
| **NY Re-employment Service Fund** | 0.075% | First $12,500 | All employers |
| **NY SDI (Disability)** | $0.60/week max ($31.20/yr) | All wages | Employer can deduct from employee |
| **NY PFL (Paid Family Leave)** | 0.388% of wages | $89,343 cap (2025) — verify 2026 | EMPLOYEE pays via deduction |
| **NY State Income Tax PIT** | Per IT-2104 (4%-10.9%) | All wages | Employer withholds |
| **NYC PIT** (if NYC resident) | 3.078%-3.876% | All wages | Employer withholds |
| **MCTMT** | 0.34% | If quarterly NYC payroll >$312,500 | Employer pays |

### New Employer Default Rates
- New employer SUI: ~3.4% Year 1 (then experience-rated)
- Workers' Comp: based on classification + payroll

### Quarterly Reporting
- **Form NYS-45** — Combined Withholding, Wage Reporting, and Unemployment Insurance Return
- Due: Last day of month after quarter end (Apr 30, Jul 31, Oct 31, Jan 31)

### E-file
- Required for employers with 100+ employees
- Strongly recommended (NY DTF online services)

### Other NY Employment Requirements
- New Hire Reporting via NYSDOL (within 20 days)
- Workers' Comp: MANDATORY (NY State Insurance Fund or private)
- Wage Theft Prevention Act: Annual notice + wage statement requirements
- NY HERO Act: Airborne disease prevention plan (employer >10)

---

## entity-specific-tax

### S-Corporation in NY
- **NY Franchise Tax (CT-3-S):** Fixed dollar minimum based on NY receipts ($25-$4,500)
- **NYC:** 8.85% General Corp Tax (NYC doesn't recognize S-Corp election!) — Form NYC-3L
- **Members:** Personal income tax on K-1 (NY state + NYC if resident)
- **PTET election strongly recommended** (saves federal tax)

### C-Corporation in NY
- **NY State:** 6.5% income tax (or 7.25% if income >$5M)
- **NYC:** 8.85% Business Corp Tax — Form NYC-2
- **MTA surcharge:** Additional 30% surcharge on NY state tax for entities in MCTD area

### LLC in NY
- **NY LLC Filing Fee:** $25-$4,500 based on gross income (Form IT-204-LL) — annual
- **Income tax:** Pass-through to members (Form IT-204 partnership return + K-1s)
- **NYC LLC:** Subject to NYC UBT (4% on income >$95K)
- **Publication requirement:** New LLCs must publish formation in 2 newspapers (cost $1K+ in NYC)

### Partnership in NY
- **NY Partnership Return:** Form IT-204 (informational)
- **LLC fee:** Same as LLC if registered as LP/LLP
- **NYC:** UBT applies (4% on income >$95K)
- **PTET election available**

### Sole Proprietor in NY
- **No entity tax filing**
- **NYC UBT:** 4% on income >$95K (after exemption)
- **NY personal income tax** via IT-201
- **NYC personal income tax** if resident
