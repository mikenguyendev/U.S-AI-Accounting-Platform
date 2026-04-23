# California (CA) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/CA.md#section-id}}` directives.**

**State:** California
**Tax Authority:** California Franchise Tax Board (FTB), California Department of Tax and Fee Administration (CDTFA), Employment Development Department (EDD)
**Last Updated:** 2026-04-22

---

## tax-obligations

### Key California Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **CA Franchise Tax (minimum)** | **$800 / year** (mandatory) | FTB | April 15 (Form 100-ES) |
| **CA Corporate Income Tax (C-Corp)** | 8.84% of net income | FTB | March/April (Form 100) |
| **CA S-Corp Tax** | 1.5% of net income (min $800) | FTB | March 15 (Form 100-S) |
| **CA LLC Fee** | $800 + tiered fee on gross receipts | FTB | April 15 (Form 568) |
| **CA Sales & Use Tax** | 7.25%–10.75% (varies by city) | CDTFA | Quarterly/Monthly |
| **CA State Income Tax Withholding** | Progressive 1%–13.3% | EDD | Per pay period |
| **CA SDI (Employer collects)** | 1.1% (2026 rate) on all wages | EDD | Per pay period |
| **CA SUI (Unemployment Insurance)** | 1.5%–6.2% on first $7,000 wages | EDD | Quarterly (DE-9) |
| **CA ETT (Employment Training Tax)** | 0.1% on first $7,000 | EDD | Quarterly (DE-9) |

> **⚠️ CRITICAL:** Tất cả entities (C-Corp, S-Corp, LLC) operating in CA phải nộp **minimum $800 franchise/LLC tax** hàng năm, kể cả khi lỗ hoặc không hoạt động. Sole Prop và General Partnership được exempt.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 CA payroll return | DE-9, DE-9C |
| **March 15** | CA S-Corp tax return | Form 100-S |
| **April 15** | CA C-Corp + Franchise tax | Form 100, 100-ES |
| **April 15** | CA LLC return + fee | Form 568 |
| **April 15** | Q1 CA estimated tax | Form 100-ES |
| **April 30** | Q1 CA payroll return | DE-9, DE-9C |
| **June 15** | Q2 CA estimated tax | Form 100-ES |
| **July 31** | Q2 CA payroll return | DE-9, DE-9C |
| **September 15** | Q3 CA estimated tax | Form 100-ES |
| **October 31** | Q3 CA payroll return | DE-9, DE-9C |
| **December 15** | Q4 CA estimated tax | Form 100-ES |

**Note:** Sales tax filing frequency depends on volume — monthly (>$17K/month avg), quarterly (default), or annual (small).

---

## upcoming-deadlines

**Next 12 months CA-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 DE-9/DE-9C |
| Mar 15 | Form 100-S (S-Corp return) |
| Apr 15 | Form 100 (C-Corp), Form 568 (LLC), Q1 estimated |
| Apr 15 | **$800 minimum franchise tax due** |
| Apr 30 | Q1 DE-9/DE-9C |
| Jun 15 | Q2 estimated |
| Jul 31 | Q2 DE-9/DE-9C |
| Sep 15 | Q3 estimated |
| Oct 31 | Q3 DE-9/DE-9C |
| Dec 15 | Q4 estimated |

---

## critical-reminders

- ⚠️ **$800 minimum franchise tax** — ALWAYS DUE, kể cả $0 revenue, kể cả entity inactive. Quên = penalties + interest + suspended status
- ⚠️ **First-year exception (2024+):** New corporations get first year exempt. New LLCs do NOT (must pay $800 in year 1)
- ⚠️ **CA S-Corp 1.5% tax** ON TOP OF federal S-Corp pass-through — không phải tax-free at entity level như federal
- ⚠️ **Sales tax registration required** trước khi bán taxable goods/services (CDTFA permit)
- ⚠️ **CA SDI** — employer collects from employee wages 1.1% (2026), no employer match needed but must remit
- ⚠️ **CA Worker's Comp** — MANDATORY khi có employee (thậm chí part-time) — separate from SDI
- ⚠️ **CA Sick Leave (SB-616)** — bắt buộc 5 days / 40 hours per year từ 2024 trở đi
- ⚠️ **CA Pay Transparency (SB-1162)** — job postings phải show salary range nếu >15 employees
- ⚠️ **CalSavers** — bắt buộc retirement program nếu >5 employees không có 401(k)

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Entity active in CA nhưng không có $800 franchise tax payment cho year → CRITICAL miss
- ⚠️ Sales tax collected nhưng không có CDTFA permit → Operating illegally
- ⚠️ Hire CA employee nhưng không có Workers' Comp insurance → Mandatory violation
- ⚠️ Hire >5 CA employees nhưng không có 401(k) hoặc CalSavers enrollment → CalSavers fine ($250/employee/yr Year 1, $500/yr+ thereafter)
- ⚠️ S-Corp/LLC operating in CA mà chưa register với SOS → Suspended status risk
- ⚠️ Multi-state nexus: bán hàng vào CA >$500K → Income tax nexus, must file
- ⚠️ Employee pay rate change without DE-4 update → State withholding mismatch

---

## validation-rules

### CA-Specific Validation

- **$800 franchise tax check:** Verify paid annually for any entity except Sole Prop/General Partnership
- **Sales tax rate:** Use destination-based sourcing — buyer's address determines rate
- **Sales tax exemptions:** Services generally NOT taxable in CA (unlike many states), but tangible goods are
- **Use tax:** Self-assess on out-of-state purchases used in CA where no sales tax was charged
- **Reciprocity:** CA does NOT have income tax reciprocity với neighbors — non-resident workers must file CA return
- **Minimum wage compliance:** $16.00/hour state minimum (2026), some cities higher (SF $18.67, LA $17.28)

---

## sales-tax

**California Sales & Use Tax**

- **Authority:** CDTFA (California Department of Tax and Fee Administration)
- **Base rate:** 7.25% state
- **District taxes:** Add up to 3.5% local (total 7.25%–10.75%)
- **Permit required:** Seller's Permit từ CDTFA trước khi bán taxable items
- **What's taxable:** Tangible personal property (mostly), some digital goods
- **What's NOT taxable:** Services (mostly), groceries, prescriptions, certain manufacturing equipment
- **Filing frequency:** Monthly (large), quarterly (medium), annual (small)
- **Due date:** Last day of month following filing period

**For pure service businesses:** Generally không cần collect sales tax, nhưng cần xem services có bao gồm tangible deliverables không (e.g., software CD vs. SaaS).

---

## estimated-tax

**California Entity-Level Estimated Tax**

Required for entities owing >$500 CA tax:

| Quarter | Due Date | Form | % of Annual |
|---------|----------|------|-------------|
| Q1 | April 15 | Form 100-ES | 30% |
| Q2 | June 15 | Form 100-ES | 40% |
| Q3 | September 15 | Form 100-ES | 0% |
| Q4 | December 15 | Form 100-ES | 30% |

**Note:** CA estimated tax schedule is unique — Q3 has 0% (not 25/25/25/25 like federal).

**Safe harbor:**
- 100% of prior year tax, OR
- 90% of current year tax (whichever is lower)

**S-Corp consideration:** Pay entity-level CA 1.5% tax estimates; shareholders separately pay personal CA estimated tax (Form 540-ES).

---

## withholding-form

**CA Employee State Withholding Form: DE-4**

- **Purpose:** Determines CA state income tax withholding amount
- **When required:** Every CA employee, signed at hire
- **Default if no DE-4:** Withhold based on Single, 0 allowances
- **File location:** Keep in employee personnel file, NOT submitted to state
- **Update:** Employee can submit new DE-4 anytime

**Companion forms required at hire:**
- Federal W-4
- I-9 (within 3 days)
- DE-34 New Hire Reporting (employer files within 20 days)

---

## withholding-tables

**CA Withholding Calculation:**

Use CA Method B (Exact Calculation) from EDD Publication DE-44:
- 9 tax brackets, progressive 1.0% to 13.3%
- Standard deduction varies by filing status
- Personal exemption credit reduces tax

**Tools:**
- EDD Online Withholding Calculator: https://www.edd.ca.gov/payroll_taxes/rates_and_withholding.htm
- DE-44 publication updated annually
- Most payroll software (Gusto, ADP) handles automatically

**Special situations:**
- Bonuses and supplemental wages: Aggregate method or flat 6.6% (10.23% if >$1M YTD)
- Stock options: Special rules apply

---

## payroll-taxes

### Employer-Side CA Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **CA SDI** | 1.1% (2026) | All wages, no cap (changed 2024) | EMPLOYER collects, EMPLOYEE pays |
| **CA SUI (UI)** | 1.5%–6.2% | First $7,000 | Employer pays, rate varies by experience |
| **CA ETT** | 0.1% | First $7,000 | Employer pays, training fund |
| **CA PIT (state income tax)** | 1%–13.3% progressive | All wages | Employer withholds |

**New Employer Default Rates:**
- New employer SUI: 3.4% for first 2-3 years
- ETT: 0.1% (always)
- SDI: 1.1% (2026 rate)

**Quarterly Reporting:**
- **DE-9** — Quarterly Contribution Return and Report of Wages
- **DE-9C** — Quarterly Contribution Return and Report of Wages (Continuation)
- Due: Last day of month after quarter end (Apr 30, Jul 31, Oct 31, Jan 31)

**Annual Reporting:**
- **DE-7** — Annual Reconciliation Statement (only if filing annually)

**E-file required:** > $20K annual liability, must use e-Services for Business

---

## entity-specific-tax

### S-Corporation in CA

- **CA S-Corp Tax:** 1.5% of net income, minimum $800
- **Form 100-S** due March 15
- **Distributes K-1 (CA)** to CA-resident shareholders
- **Shareholders file:** Form 540 with CA-source income

### C-Corporation in CA

- **CA Corp Tax:** 8.84% of net income (or AMT 6.65% — whichever higher)
- **Form 100** due 15th day of 4th month after fiscal year end (April 15 cho calendar year)
- **Minimum $800 franchise tax** even if loss

### LLC in CA

- **$800 LLC tax** + tiered LLC fee:
  - Income $250K-$499K: $900
  - Income $500K-$999K: $2,500
  - Income $1M-$4.99M: $6,000
  - Income $5M+: $11,790
- **Form 568** due April 15

### Partnership in CA

- **$800 LLC tax** if registered as LLP (limited liability partnership)
- General Partnerships: NO franchise tax
- **Form 565** for general partnerships, Form 568 for LLPs/LLCs
