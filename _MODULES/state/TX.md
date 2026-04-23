# Texas (TX) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/TX.md#section-id}}` directives.**

**State:** Texas
**Tax Authority:** Texas Comptroller of Public Accounts, Texas Workforce Commission (TWC)
**Last Updated:** 2026-04-22

> **🎯 KEY ADVANTAGE:** Texas có **NO state income tax** cho cá nhân hoặc business. Replaced bởi **Franchise Tax** (margin tax). Tax-friendly cho high-income business owners, đặc biệt S-Corp/LLC pass-through structures.

---

## tax-obligations

### Key Texas Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **TX Franchise Tax (Margin Tax)** | 0.375% (retail/wholesale), 0.75% (other) | Comptroller | May 15 (Form 05-158-A) |
| **No-Tax-Due Threshold** | Revenue ≤ $2.47M (2024-2025; verify 2026) — File Form 05-163 | Comptroller | May 15 |
| **TX Sales & Use Tax** | 6.25% state + up to 2% local (max 8.25%) | Comptroller | Monthly/Quarterly/Annual |
| **TX State Income Tax** | **0%** (NO state income tax) | N/A | N/A |
| **TX SUTA (Unemployment Insurance)** | 0.31%–6.31% on first $9,000 wages | TWC | Quarterly (Form C-3) |
| **TX No SDI** | N/A (Texas does NOT have State Disability Insurance) | N/A | N/A |
| **Workers' Compensation** | Optional in TX (only state where it's not mandatory) | DWC | Per pay period if subscribed |

> **⚠️ NOTE:** Texas franchise tax base = "margin" = lesser of:
> - Total revenue × 70%
> - Total revenue - COGS
> - Total revenue - compensation
> - Total revenue - $1M (since 2024)

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 TX SUTA return | Form C-3 |
| **April 30** | Q1 TX SUTA return | Form C-3 |
| **May 15** | **TX Franchise Tax / No-Tax-Due Report** | Form 05-158-A or 05-163 |
| **May 15** | TX Public Information Report | Form 05-102 |
| **July 31** | Q2 TX SUTA return | Form C-3 |
| **October 31** | Q3 TX SUTA return | Form C-3 |

**Sales tax filing frequency:** Monthly (>$500K annual liability), Quarterly (default), Annual (small).
**Sales tax due:** 20th of month following filing period (most common).

---

## upcoming-deadlines

**Next 12 months TX-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 SUTA (Form C-3) |
| Apr 30 | Q1 SUTA |
| **May 15** | **Franchise Tax + Public Info Report** |
| Jul 31 | Q2 SUTA |
| Oct 31 | Q3 SUTA |

---

## critical-reminders

- ⚠️ **No state income tax** — but franchise tax STILL applies for entities (LLC, Corp, LP)
- ⚠️ **Sole props + GPs exempt** from franchise tax (no entity-level filing)
- ⚠️ **No-Tax-Due Report** still required dù revenue dưới threshold (Form 05-163, due May 15)
- ⚠️ **Public Information Report (PIR)** required ANNUALLY (Form 05-102) — discloses officers/directors
- ⚠️ **Forfeiture risk:** Miss franchise tax filing → entity loses right to sue, transact business
- ⚠️ **Sales tax permit required** trước khi bán taxable items — Texas Comptroller online application
- ⚠️ **NO mandatory Workers' Comp** — Texas only state where it's optional. BUT employer who declines loses common law defenses (injured employee can sue without limits)
- ⚠️ **Texas minimum wage = federal $7.25/hour** (no state minimum higher)
- ⚠️ **No SDI, no state withholding** — payroll simpler than CA/NY
- ⚠️ **Local taxes:** Some cities (Houston, Dallas, Austin) have additional city sales tax — verify destination-based

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Entity active in TX không file Franchise Tax / No-Tax-Due Report by May 15 → forfeiture risk
- ⚠️ PIR (Form 05-102) not filed → entity right-to-transact suspended
- ⚠️ Sales tax collected nhưng không có Comptroller permit → operating illegally
- ⚠️ Hire TX employee, declined Workers' Comp → notify employees in writing (required), accept tort liability
- ⚠️ Multi-state nexus: Selling >$500K annually into TX → economic nexus, must collect TX sales tax
- ⚠️ Franchise tax revenue calculated incorrectly → understatement penalty
- ⚠️ Out-of-state employee working remotely from TX → may trigger TX SUTA obligation

---

## validation-rules

### TX-Specific Validation

- **Franchise tax base:** Verify uses lowest of 4 calculation methods (margin)
- **No-Tax-Due threshold:** $2.47M revenue (2024-2025) — confirm 2026 threshold
- **Sales tax sourcing:** Origin-based (most TX), but special rules for out-of-state sellers
- **Sales tax exemptions:** Many — manufacturing equipment, R&D, food (not prepared), prescription drugs
- **No reciprocity issues:** Since no state income tax, no withholding issues with neighbors
- **Minimum wage:** $7.25/hour federal applies (no TX state minimum)
- **Tip credit:** Allowed in TX (tipped wages $2.13/hour minimum if tips bring to $7.25)

---

## sales-tax

**Texas Sales & Use Tax**

- **Authority:** Texas Comptroller of Public Accounts
- **Base rate:** 6.25% state
- **Local taxes:** Up to 2% additional (cities, counties, transit, special districts)
- **Total range:** 6.25%–8.25% (max)
- **Permit required:** Sales Tax Permit từ Comptroller before selling taxable items (free)
- **What's taxable:**
  - Tangible personal property
  - Many services (data processing, repair, landscaping, etc.)
  - Digital goods (since 2018)
- **What's NOT taxable:**
  - Most services (professional, medical, legal, educational)
  - Groceries (unprepared)
  - Prescription drugs
  - Manufacturing machinery (specific exemption)
- **Filing frequency:**
  - Monthly: annual liability >$500K
  - Quarterly: default
  - Annual: <$1,000/year
- **Due date:** 20th of month following filing period
- **Online filing:** Required (Webfile system)

**Special: Resale Certificates** — Buyers can purchase tax-free for resale (Form 01-339)

---

## estimated-tax

**No state income tax = no state estimated tax for entity OR owner.**

**Franchise tax:** Annual filing only (no quarterly estimates required).

**For owners of pass-through entities (LLC, S-Corp, Partnership):**
- No TX state estimated tax
- Federal estimated tax still required (Form 1040-ES) for federal income + SE tax
- Owner who relocates from CA/NY to TX saves significant state tax

**AI MUST when processing `estimated-tax` form for TX entity:**
1. Confirm: NO Texas state estimated tax required
2. If owner is TX resident: federal estimated tax only (Form 1040-ES)
3. If business has nexus in other states: those states may require estimated tax
4. Multi-state filers: track per-state estimated tax separately

---

## withholding-form

**TX has NO state income tax → NO state withholding form required**

- Federal W-4 only
- I-9 within 3 days of hire
- New Hire Reporting via TWC within 20 days (Form C-15)

**No state withholding tax to calculate or remit.**

---

## withholding-tables

**N/A — Texas has no state income tax withholding.**

Federal withholding only:
- Use IRS Pub 15-T (2026)
- Calculation methods: percentage method or wage bracket method

**Special situations:**
- Bonuses: Federal supplemental rate 22% (no state addition)
- Out-of-state remote workers: Withhold based on workplace state, not residence

---

## payroll-taxes

### Employer-Side TX Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **TX SUTA (Unemployment)** | 0.31%–6.31% | First $9,000 | Rate by experience; new employer 2.7% Year 1 |
| **No SDI** | N/A | N/A | Texas does not have State Disability Insurance |
| **No state income tax withholding** | N/A | N/A | Federal only |

### New Employer Default Rates
- New employer SUTA: 2.7% for first 3 years (then experience-rated)
- No state minimum wage above federal $7.25

### Quarterly Reporting
- **Form C-3** — TX Employer's Quarterly Report
- Due: Last day of month after quarter end (Apr 30, Jul 31, Oct 31, Jan 31)

### E-file
- Required for employers with 500+ employees
- Recommended for all (TWC online portal)

### Other TX Employment Requirements
- New Hire Reporting: Form C-15 within 20 days (TWC)
- Workers' Comp: OPTIONAL but if declined, employer notification + can be sued in tort
- Unemployment Insurance: Mandatory

---

## entity-specific-tax

### S-Corporation / C-Corporation in TX
- **Franchise Tax:** 0.375% (retail/wholesale) or 0.75% (other) of margin
- **Federal Form 1120-S / 1120** still required
- No state income tax filing

### LLC in TX
- **Franchise Tax:** Same as Corp (0.375% / 0.75% of margin)
- LLC formation fee: $300 (one-time, filed with TX Secretary of State)
- Annual: $0 LLC fee, only Franchise Tax
- Members file federal Form 1065 (multi) or Schedule C (single) — no TX state filing

### Partnership in TX
- **General Partnership:** EXEMPT from Franchise Tax
- **Limited Partnership / LLP:** Subject to Franchise Tax
- Federal Form 1065 + K-1s

### Sole Proprietor in TX
- EXEMPT from Franchise Tax
- No state income tax filing
- Just federal Schedule C
- Most tax-favorable structure for very small businesses in TX

### Out-of-State Entities Operating in TX
- Must register with TX Secretary of State if doing business in TX
- Subject to TX Franchise Tax based on TX-apportioned margin
- Sales tax nexus rules apply
