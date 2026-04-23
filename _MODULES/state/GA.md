# Georgia (GA) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/GA.md#section-id}}` directives.**

**State:** Georgia
**Tax Authority:** Georgia Department of Revenue (DOR), Georgia Department of Labor (GDOL)
**Last Updated:** 2026-04-22

> **🎯 RECENTLY SIMPLIFIED:** Georgia transitioned từ progressive bracket system (1%-5.75%) sang **flat 5.39% rate (2024)**, gradually reducing to 4.99% by 2029. Pro-business climate, moderate tax burden, mid-range complexity.

---

## tax-obligations

### Key Georgia Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **GA Corporate Income Tax (C-Corp)** | 5.39% (2024-2025; reducing to 4.99% by 2029) | DOR | April 15 |
| **GA Net Worth Tax (C-Corp)** | $10–$5,000 sliding scale (based on net worth) | DOR | April 15 (with 600) |
| **GA Personal Income Tax** | 5.39% flat (2024-2025) | DOR | April 15 |
| **GA Sales & Use Tax** | 4% state + up to 5% local (Atlanta 8.9%) | DOR | Monthly/Quarterly |
| **GA SUI (Unemployment)** | 0.04%–8.1% on first $9,500 wages | GDOL | Quarterly (DOL-4N) |
| **No SDI** | N/A | N/A | N/A |
| **Workers' Compensation** | MANDATORY for 3+ employees | GA SBWC | Per pay period |

> **⚠️ NOTE:** GA's flat tax rate is scheduled to decrease yearly: 5.39% (2024-2025) → 5.19% (2026) → 4.99% (eventual). Verify current year rate.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 GA SUI return | DOL-4N |
| **March 15** | GA S-Corp / Partnership return | Form 600S, Form 700 |
| **April 15** | GA C-Corp return + Net Worth Tax | Form 600 |
| **April 15** | GA Personal Income Tax | Form 500 |
| **April 30** | Q1 GA SUI return | DOL-4N |
| **June 15** | Q2 GA personal estimated tax | Form 500-ES |
| **July 31** | Q2 GA SUI return | DOL-4N |
| **September 15** | Q3 GA personal estimated tax | Form 500-ES |
| **October 31** | Q3 GA SUI return | DOL-4N |
| **January 15** | Q4 GA personal estimated tax | Form 500-ES |

**Sales tax filing:** Monthly (most), Quarterly (small businesses).
**Sales tax due:** 20th of month following filing period.

---

## upcoming-deadlines

**Next 12 months GA-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 personal estimated (prior year) |
| Jan 31 | Q4 SUI |
| **Mar 15** | GA S-Corp / Partnership |
| **Apr 15** | GA C-Corp + Net Worth Tax + Personal Income |
| Apr 30 | Q1 SUI |
| Jun 15 | Q2 personal estimated |
| Jul 31 | Q2 SUI |
| Sep 15 | Q3 personal estimated |
| Oct 31 | Q3 SUI |

---

## critical-reminders

- ⚠️ **Flat tax rate decreasing annually** — verify current year (5.39% 2024-2025 → 4.99% by 2029)
- ⚠️ **Net Worth Tax** unique — C-Corps pay sliding scale $10-$5,000 based on issued capital + paid-in capital + retained earnings
- ⚠️ **GA PTE Tax election available** — pass-through entity tax election (SALT cap workaround)
- ⚠️ **Sales tax sourcing:** Origin-based for in-state sellers, destination-based for remote sellers (since 2018)
- ⚠️ **Workers' Comp threshold: 3+ employees** — exemption for small operations
- ⚠️ **GA minimum wage = federal $7.25** (no state minimum higher) — but federal contracts $17.20+
- ⚠️ **No state-mandated paid leave** — GA is one of states without PFML
- ⚠️ **Atlanta + several cities** have additional local sales tax (up to 8.9% Atlanta combined)
- ⚠️ **GA reciprocity agreements:** GA does NOT have reciprocity with neighboring states
- ⚠️ **GA tax credits** — film tax credit (popular for Atlanta production), Quality Jobs Tax Credit

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ C-Corp not filing Net Worth Tax with Form 600 → audit + back tax
- ⚠️ Hire 3rd employee without Workers' Comp → state penalties + civil exposure
- ⚠️ Sales tax sourcing incorrect → audit assessment
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into GA → economic nexus
- ⚠️ PTE Tax election deadline missed (annually with first estimated payment) → no SALT workaround
- ⚠️ Atlanta operations not registered with City of Atlanta → city occupational license required
- ⚠️ Tax rate using outdated rate (still using 5.75% from pre-2024) → underpayment

---

## validation-rules

### GA-Specific Validation

- **Tax rate by year:** 5.39% (2024-2025), 5.19% (2026), 4.99% (eventual) — verify
- **Net Worth Tax base:** Issued + Paid-in Capital + Retained Earnings (NOT just market cap)
- **Apportionment:** Single sales factor (since 2008)
- **Sales tax sourcing:** Origin (in-state), destination (remote)
- **Sales tax exemptions:** Groceries (no state sales tax, but local may apply), prescription drugs, manufacturing inputs
- **Local taxes:** Verify city/county rates

---

## sales-tax

**Georgia Sales & Use Tax**

- **Authority:** Georgia DOR
- **Base rate:** 4% state
- **Local taxes:** Up to 5% additional (LOST + SPLOST + ELOST + special)
- **Total range:** 7%–8.9% (Atlanta highest)
- **Permit required:** Sales Tax Number from GA DOR (online, free)
- **What's taxable:**
  - Tangible personal property
  - Some services (telecom, accommodations)
  - Prepared food (restaurants)
  - Digital products (since 2014)
- **What's NOT taxable:**
  - Most professional services
  - Groceries (NO state sales tax; local may apply 1-3%)
  - Prescription drugs
  - Manufacturing machinery (with certificate)
  - Newspapers
- **Filing frequency:**
  - Monthly: liability >$200/month
  - Quarterly: $50-$200
  - Annual: <$50/year
- **Due date:** 20th of month following filing period

---

## estimated-tax

### GA Corporate Income Tax + Net Worth Tax (C-Corp)

For C-Corps owing >$500 in GA tax:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 600-ES |
| Q2 | June 15 | Form 600-ES |
| Q3 | September 15 | Form 600-ES |
| Q4 | December 15 | Form 600-ES |

### GA Personal Income Tax

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 500-ES |
| Q2 | June 15 | Form 500-ES |
| Q3 | September 15 | Form 500-ES |
| Q4 | January 15 | Form 500-ES |

### PTE Tax Election

- GA pass-through entities can elect entity-level tax (5.39%)
- SALT cap workaround
- Election made annually with first quarterly payment

**AI MUST when processing `estimated-tax` form for GA:**
1. Distinguish entity type
2. C-Corp: Form 600-ES quarterly (Income + Net Worth)
3. Pass-through: depends on PTE election
4. Owners: Form 500-ES quarterly
5. Verify current year tax rate (5.39% 2024-2025; verify 2026)

---

## withholding-form

**GA Employee State Withholding Form: G-4**

- **Purpose:** Determines GA state income tax withholding
- **Default if no G-4:** Single, 0 allowances
- **Update:** Employee can submit anytime
- **Companion form:** Federal W-4

**Required at hire:**
- Federal W-4 + GA G-4
- I-9 (within 3 days)
- New Hire Reporting via GA New Hire Reporting Center within 10 days

---

## withholding-tables

**GA Withholding Calculation:**

- Flat 5.39% (2024-2025) on wages above exemption
- Standard deduction varies by filing status

**Tools:**
- GA DOR Employer's Tax Guide (annually updated)
- Most payroll software handles automatically

**Special situations:**
- Bonuses: Use 5.39% supplemental rate (GA flat tax, simpler than CA/NY)
- Out-of-state remote workers: GA does not have Convenience of Employer rule

---

## payroll-taxes

### Employer-Side GA Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **GA SUI** | 0.04%–8.1% | First $9,500 | New employer 2.7% |
| **No SDI** | N/A | N/A | GA doesn't have State Disability |
| **GA Income Tax PIT** | 5.39% (2024-2025) | All wages above exemption | Employer withholds |

### New Employer Default Rates
- New employer SUI: 2.7% Year 1
- GA minimum wage: $7.25/hour (federal applies)

### Quarterly Reporting
- **Form DOL-4N** — Quarterly Tax and Wage Report
- Due: Last day of month after quarter end

### E-file
- Required for employers with 100+ employees
- Recommended for all (GDOL Employer Portal)

### Other GA Employment Requirements
- New Hire Reporting: 10 days
- Workers' Comp: MANDATORY (3+ employees)
- E-Verify: Required for employers with 11+ employees

---

## entity-specific-tax

### S-Corporation in GA
- **GA Corporate Income Tax 5.39%** (entity-level, NOT pass-through for GA)
  - Wait — GA recognizes federal S-Corp election → pass-through
  - S-Corp files Form 600S informational
- Federal Form 1120-S still required
- Shareholders: 5.39% personal tax on K-1

### C-Corporation in GA
- **GA Corporate Income Tax: 5.39%** on net income
- **GA Net Worth Tax: $10-$5,000** sliding scale (additional)
- Form 600 due April 15

### LLC in GA
- **No entity-level GA income tax** (pass-through)
- LLC formation: $100 (Secretary of State)
- Annual Registration: $50
- Federal Form 1065/Schedule C

### Partnership in GA
- **No entity-level income tax** (pass-through)
- Federal Form 1065 + K-1s
- GA Form 700 informational

### Sole Proprietor in GA
- No entity tax filing
- GA personal income tax via Form 500
- Just federal Schedule C

### Out-of-State Entities Operating in GA
- C-Corps subject to GA Corporate Income Tax + Net Worth Tax
- Sales tax nexus rules apply
- Foreign Qualification with GA Secretary of State
