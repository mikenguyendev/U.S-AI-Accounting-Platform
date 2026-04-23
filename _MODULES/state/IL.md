# Illinois (IL) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/IL.md#section-id}}` directives.**

**State:** Illinois
**Tax Authority:** Illinois Department of Revenue (IDOR), Illinois Department of Employment Security (IDES), Illinois Workers' Compensation Commission
**Last Updated:** 2026-04-22

> **⚠️ DOUBLE-LAYER CORPORATE TAX:** Illinois corps/S-corps pay both **Corporate Income Tax (4.95% personal / 7% corporate)** AND **Replacement Tax (1.5% on partnerships/S-corps; 2.5% on C-corps)**. Total tax burden higher than rate suggests.

---

## tax-obligations

### Key Illinois Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **IL Corporate Income Tax (C-Corp)** | 7% on net income | IDOR | March 15 / April 15 |
| **IL Personal Property Replacement Tax (C-Corp)** | 2.5% on net income | IDOR | Same as Corp Tax |
| **IL Replacement Tax (S-Corp/Partnership/LLC)** | 1.5% on net income | IDOR | March 15 |
| **IL Personal Income Tax** | 4.95% flat | IDOR | April 15 |
| **IL Sales & Use Tax** | 6.25% state + up to 4.75% local (Chicago 10.25%) | IDOR | Monthly/Quarterly |
| **IL SUI (Unemployment)** | 0.85%–8.65% on first $13,500 wages (2026) | IDES | Quarterly (UI-3/40) |
| **No SDI** | N/A | N/A | N/A |
| **Workers' Compensation** | MANDATORY for all employers (1+ employee) | IL WC Commission | Per pay period |
| **Chicago: Personal Property Lease Tax** | 9% (Chicago only — on leased software, equipment) | Chicago Dept of Finance | Monthly |
| **Chicago: Bottled Water Tax** | $0.05/bottle | Chicago | At sale |

> **⚠️ KEY:** Illinois is one of few states where **even pass-through entities pay state-level tax** (Replacement Tax 1.5%) on top of owners' personal tax — partial double taxation.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 IL SUI return | UI-3/40 |
| **March 15** | IL S-Corp / Partnership return + Replacement Tax | IL-1120-ST, IL-1065 |
| **April 15** | IL C-Corp return + Replacement Tax | IL-1120 |
| **April 15** | IL Personal Income Tax | IL-1040 |
| **April 30** | Q1 IL SUI return | UI-3/40 |
| **June 15** | Q2 IL personal estimated tax | IL-1040-ES |
| **July 31** | Q2 IL SUI return | UI-3/40 |
| **September 15** | Q3 IL personal estimated tax | IL-1040-ES |
| **October 31** | Q3 IL SUI return | UI-3/40 |
| **December 15** | Q4 IL personal estimated tax | IL-1040-ES |

**Sales tax filing:** Monthly (>$200/month avg), Quarterly (default), Annual (small).
**Sales tax due:** 20th of month following filing period.

---

## upcoming-deadlines

**Next 12 months IL-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 SUI |
| **Mar 15** | IL S-Corp / Partnership + Replacement Tax |
| **Apr 15** | IL C-Corp + Replacement Tax + Personal Income |
| Apr 30 | Q1 SUI |
| Jun 15 | Q2 personal estimated |
| Jul 31 | Q2 SUI |
| Sep 15 | Q3 personal estimated |
| Oct 31 | Q3 SUI |
| Dec 15 | Q4 personal estimated |

---

## critical-reminders

- ⚠️ **Replacement Tax (1.5%) on pass-through entities** is unique to IL — partial double taxation
- ⚠️ **Total IL tax burden for C-Corp = 7% Corp + 2.5% Replacement = 9.5%** (one of highest in US)
- ⚠️ **Chicago has its own taxes** on top of IL state — Lease Tax (9%), Bottled Water, Soft Drink, Restaurant
- ⚠️ **Chicago + Cook County minimum wage** higher than IL state ($16.20/hour Chicago 2025; verify 2026)
- ⚠️ **IL minimum wage $15.00/hour (2025)** — increased annually
- ⚠️ **IL Paid Leave for All Workers Act** (2024) — 40 hours paid leave per year (mandatory)
- ⚠️ **Workers' Comp mandatory** even for 1 employee (no threshold like FL/TN)
- ⚠️ **Sales tax sourcing** — origin-based for IL retailers, destination-based for remote sellers
- ⚠️ **Cook County tax stacking** — IL state + Cook County + Chicago = up to 10.25% sales tax in Chicago
- ⚠️ **PTE Tax election available** — IL allows pass-through entity tax election (SALT cap workaround)
- ⚠️ **IL Department of Revenue audits aggressive** — especially on multi-state apportionment

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ S-Corp/LLC operating in IL không paying Replacement Tax → audit + back tax + penalty
- ⚠️ Chicago business not registered with City of Chicago Department of Finance → city tax issues
- ⚠️ Hire IL employee without Paid Leave for All Workers Act compliance → fines + back leave
- ⚠️ Workers' Comp not in place (even 1 employee) → criminal penalties (misdemeanor)
- ⚠️ Sales tax sourcing incorrect → significant audit exposure
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into IL → economic nexus
- ⚠️ PTE Tax election deadline missed (last day of tax year) → no SALT cap workaround
- ⚠️ Chicago minimum wage not honored ($16.20+) → fines + back wages
- ⚠️ IL state minimum wage updates not implemented Jan 1 → wage theft claim risk

---

## validation-rules

### IL-Specific Validation

- **Replacement Tax base:** Same as federal taxable income (with adjustments)
- **PTE Tax election:** Must elect annually, by last day of tax year
- **Sales tax sourcing:** Origin (in-state retailers), destination (remote sellers since 2020)
- **Sales tax exemptions:** Groceries (1% reduced), prescription drugs (1%), agricultural inputs
- **Multi-state apportionment:** Single sales factor (since 2017)
- **Chicago vs Cook County vs IL state:** Track each level separately for tax purposes
- **Minimum wage:** Verify by city — Chicago/Cook County higher than rest of IL

---

## sales-tax

**Illinois Sales & Use Tax**

- **Authority:** Illinois Department of Revenue (IDOR)
- **Base rate:** 6.25% state (general merchandise)
- **Reduced rates:**
  - 1% on groceries (unprepared food)
  - 1% on prescription drugs
  - 6.25% on prepared food, candy, soft drinks
- **Local taxes:** Up to 4.75% additional (Chicago: 1.25% home rule + 1% county + 1% RTA = 9.5% combined)
- **Total Chicago rate:** 10.25% (highest major US city)
- **Permit required:** Illinois Business Tax Number from IDOR (online)
- **What's taxable:**
  - Tangible personal property
  - Some services (maintenance contracts, telecom, hotel)
  - Prepared food
  - Software (varies — canned vs custom)
- **What's NOT taxable:**
  - Most professional services
  - Manufacturing machinery (with certificate)
  - Newspapers
- **Filing frequency:**
  - Monthly: avg liability >$200/month
  - Quarterly: default
  - Annual: <$50/year
- **Due date:** 20th of month following filing period

---

## estimated-tax

### IL Corporate Income Tax + Replacement Tax (C-Corp)

For C-Corps owing >$400 in IL tax:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | IL-1120-ES |
| Q2 | June 15 | IL-1120-ES |
| Q3 | September 15 | IL-1120-ES |
| Q4 | December 15 | IL-1120-ES |

### IL Replacement Tax (S-Corp / Partnership / LLC)

Generally paid with annual return (March 15) — no quarterly estimates required for entities owing <$400.

### IL Personal Income Tax (Owners)

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | IL-1040-ES |
| Q2 | June 15 | IL-1040-ES |
| Q3 | September 15 | IL-1040-ES |
| Q4 | January 15 | IL-1040-ES |

**Calculation:** IL flat 4.95% personal tax + replacement tax allocation from K-1.

### PTE Tax Election

- IL pass-through entities can elect entity-level tax (4.95%)
- Saves federal SALT cap workaround
- Election made annually
- Quarterly estimated payments if elected

**AI MUST when processing `estimated-tax` form for IL:**
1. Distinguish entity type (C-Corp vs pass-through)
2. C-Corp: Form IL-1120-ES quarterly (Income + Replacement)
3. Pass-through: Replacement Tax with annual return
4. Owners: IL-1040-ES quarterly
5. Check PTE election status — affects payment routing
6. Apply Chicago city tax separately if applicable

---

## withholding-form

**IL Employee State Withholding Form: IL-W-4**

- **Purpose:** Determines IL state income tax withholding
- **Default if no IL-W-4:** Single, 0 allowances
- **Update:** Employee can submit anytime
- **Companion form:** Federal W-4

**Required at hire:**
- Federal W-4 + IL-W-4
- I-9 (within 3 days)
- New Hire Reporting via Illinois Directory of New Hires within 20 days

---

## withholding-tables

**IL Withholding Calculation:**

- Flat 4.95% on all wages above standard exemption
- 2026 standard exemption: ~$2,775 per allowance (verify annually)
- Method: Flat percentage (simplest of all states)

**Tools:**
- IL DOR Booklet IL-700-T (annually updated)
- Most payroll software handles automatically

**Special situations:**
- Bonuses: Use 4.95% supplemental rate
- Out-of-state remote workers for IL employer: Source-based (where work performed)

---

## payroll-taxes

### Employer-Side IL Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **IL SUI** | 0.85%–8.65% | First $13,500 (2026) | New employer ~3.95% |
| **No SDI** | N/A | N/A | IL doesn't have State Disability |
| **IL Income Tax PIT** | 4.95% flat | All wages above exemption | Employer withholds |

### New Employer Default Rates
- New employer SUI: ~3.95% Year 1
- IL minimum wage: $15.00/hour (2025) — verify 2026
- Chicago minimum: $16.20/hour (2025) — verify 2026
- Cook County minimum: $14.05 (2024) — verify 2026

### Quarterly Reporting
- **Form UI-3/40** — Quarterly Wage and Tax Report
- Due: Last day of month after quarter end

### E-file
- Required for employers with 25+ employees
- Recommended for all (IDES MyTax IL portal)

### Other IL Employment Requirements
- New Hire Reporting: 20 days
- Workers' Comp: MANDATORY (any employer)
- IL Paid Leave for All Workers Act: 40 hours/year (since 2024)
- Chicago: Additional sick leave + minimum wage rules

---

## entity-specific-tax

### S-Corporation in IL
- **IL Replacement Tax: 1.5%** on net income (entity-level)
- Federal Form 1120-S still required
- IL Form IL-1120-ST due March 15
- Shareholders: 4.95% personal income tax on K-1 (IL-1040)

### C-Corporation in IL
- **IL Corporate Income Tax: 7%** on net income
- **IL Replacement Tax: 2.5%** on net income (additional)
- **Combined effective IL tax: 9.5%**
- Federal Form 1120 + IL Form IL-1120 due April 15

### LLC in IL
- **IL Replacement Tax: 1.5%** (pass-through)
- LLC formation: $150 (Secretary of State)
- Annual Report: $75
- Federal Form 1065/Schedule C

### Partnership in IL
- **IL Replacement Tax: 1.5%**
- Federal Form 1065 + K-1s
- IL Form IL-1065 due March 15

### Sole Proprietor in IL
- No Replacement Tax (sole props exempt)
- IL personal income tax via IL-1040
- Just federal Schedule C

### Out-of-State Entities Operating in IL
- Subject to IL Replacement Tax + Income Tax based on IL apportionment
- Sales tax nexus rules apply
- Foreign Qualification with IL Secretary of State required
