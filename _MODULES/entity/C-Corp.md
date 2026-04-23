# C-Corporation — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/C-Corp.md#section-id}}` directives.**

**Entity Type:** C-Corporation
**Tax Treatment:** Double taxation (entity tax + dividend tax to shareholders)
**Primary Tax Form:** Form 1120
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings |
| **January 31** | Form 941 (Q4) | Q4 payroll tax return |
| **April 15** | **Form 1120** | C-Corp income tax return (calendar year filers) |
| **April 15** | Form 7004 | Extension request (extends to October 15) |
| **April 15** | Form 1120-W (Q1) | Q1 estimated tax voucher |
| **April 30** | Form 941 (Q1) | Q1 payroll tax return |
| **June 15** | Form 1120-W (Q2) | Q2 estimated tax |
| **July 31** | Form 941 (Q2) | Q2 payroll tax return |
| **September 15** | Form 1120-W (Q3) | Q3 estimated tax |
| **October 15** | Form 1120 (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax return |
| **December 15** | Form 1120-W (Q4) | Q4 estimated tax |

**Fiscal year filers:** Form 1120 due 15th day of 4th month after fiscal year end.

---

## federal-obligations

**Entity-level returns:**
- **Form 1120** (annual) — U.S. Corporation Income Tax Return
- **Form 1120-W** (quarterly) — Estimated Tax for Corporations (worksheet, not filed)
- **Form 941** (quarterly) — Employer's Quarterly Federal Tax Return (payroll)
- **Form 940** (annual) — FUTA (Federal Unemployment Tax)
- **Form W-2/W-3** (annual) — Wage statements for employees
- **Form 1099-NEC** (annual) — Contractor payments >$600/year
- **Form 1099-DIV** (annual) — If issuing dividends to shareholders >$10

**Shareholder-level (NOT pass-through):**
- Shareholders pay personal tax on dividends received (qualified vs ordinary)
- Form 1099-DIV reports dividend income
- Capital gains tax on stock sales

**Key difference vs S-Corp:**
- C-Corp pays 21% federal income tax (flat rate since 2018)
- THEN dividends taxed AGAIN at shareholder level (15-20% qualified rate)
- Total effective rate can reach ~40% for qualified dividends, higher for ordinary

---

## critical-rules

### Eligibility
- **No restrictions** on shareholders (foreign OK, entities OK, unlimited count)
- Multiple classes of stock allowed (preferred, common, voting/non-voting)
- Default tax classification for incorporated entities (no election needed)

### Tax Election (to switch FROM C-Corp)
- File **Form 2553** to elect S-Corp status
- Or file **Form 8832** + Form 2553 for LLC electing C-Corp first then S
- Once elected, must wait 5 years to revoke (with exceptions)

### Distribution Rules
- **Dividends** = formal distributions of profit
- Must be approved by board of directors
- Documented in board meeting minutes
- Reported via Form 1099-DIV
- NOT deductible to corporation (already taxed)

### Accumulated Earnings Tax
- ⚠️ Penalty 20% on retained earnings beyond reasonable business needs
- Threshold: $250,000 (general corp), $150,000 (Personal Service Corp)
- Mitigation: document business purpose for retained earnings (expansion, working capital, etc.)

### Personal Holding Company (PHC) Tax
- ⚠️ Penalty 20% on undistributed PHC income
- PHC defined: 5+ shareholders own >50%, AND 60%+ income is passive
- Avoid by: distributing earnings, restructuring shareholding

### Loans to/from Shareholders
- Must be bona fide loans with documented terms
- Interest rate must be at least Applicable Federal Rate (AFR)
- Failure → IRS reclassifies as dividend (taxable)

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | W-2, W-3, 1099-NEC, Form 940, Q4 941 |
| Apr 15 | **Form 1120** + Q1 estimated tax |
| Apr 30 | Q1 Form 941 |
| Jun 15 | Q2 estimated tax |
| Jul 31 | Q2 Form 941 |
| Sep 15 | Q3 estimated tax |
| Oct 15 | Extended Form 1120 |
| Oct 31 | Q3 Form 941 |
| Dec 15 | Q4 estimated tax |
| Jan 31 (next yr) | Year-end filings cycle restart |

---

## owner-compensation

⚠️ **C-CORP COMPENSATION RULES — Different from S-Corp**

Owner-employees in C-Corp có 2 cách nhận compensation:

### Option 1: W-2 Salary
- Subject to FICA (15.3%) + federal/state income tax withholding
- DEDUCTIBLE to corporation (reduces taxable income)
- Most common for active owner-employees

### Option 2: Dividends
- Paid from after-tax corporate profit (already 21% federal tax)
- Then taxed AGAIN at shareholder level (qualified dividend rate 0/15/20%)
- NOT deductible to corporation
- Higher overall tax burden than salary in most cases

### Reasonable Compensation Considerations
- Unlike S-Corp (where IRS pushes salary UP), in C-Corp IRS may push salary DOWN
- Reason: C-Corp owners may inflate salary to avoid double taxation on dividends
- IRS test: salary must be "reasonable" — not excessive
- Excessive salary → reclassified as disguised dividend (loses corporate deduction)

### Optimal Strategy
- Pay reasonable W-2 for active services (gets corporate deduction)
- Distribute remaining profit as dividends only when needed
- Consider retaining earnings in corporation for growth (lower tax than dividends)

### Documentation Required
- Annual board resolution approving compensation
- Comparable salary data (similar to S-Corp — but argument flipped)
- Time tracking + role description
- Industry benchmark studies

**Strongly recommend:** Annual review with CPA, especially if salary >$200K.

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form for C-Corp:**

1. Identify if comp is W-2 salary, dividend, or mix
2. If salary > $200K → flag for "reasonable compensation" review (excessive risk)
3. If dividend distribution → verify:
   - Board resolution exists
   - Pro-rata to shareholding (or per share class)
   - Form 1099-DIV will be issued
4. Calculate tax burden comparison:
   - Salary scenario: Income tax + FICA (corporate deduction = corporate tax savings)
   - Dividend scenario: Corp pays 21%, then shareholder pays 0/15/20% on dividend
   - Show net cash to owner under each
5. Check Accumulated Earnings: if entity retains >$250K without business purpose → flag PHC/AE risk
6. Recommend CPA review if total comp >$300K
7. Save documentation to: `05_Payroll/Owner_Compensation/`

**File naming:** `YYYYMMDD_OwnerComp_Analysis_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Owner salary excessively high (>3x industry benchmark) → IRS may reclassify as dividend
- ⚠️ Dividend declared without board resolution → corporate formality violation
- ⚠️ Loan to shareholder >$10K without written terms + AFR interest → constructive dividend risk
- ⚠️ Retained earnings >$250K without documented business purpose → Accumulated Earnings Tax risk
- ⚠️ Personal expenses paid by corporation → constructive dividend
- ⚠️ Form 1120 not filed by April 15 → 5%/month penalty (max 25%) + interest
- ⚠️ Estimated tax underpayment >$500 → Form 2220 underpayment penalty
- ⚠️ Issuing dividends to multiple shareholders at non-pro-rata rate → preference issue (unless multiple stock classes)
- ⚠️ 5 or fewer shareholders own >50% AND passive income >60% → PHC tax risk

---

## validation-rules

### C-Corp Specific Validation

- **Dividend pro-rata check:** Within same stock class, distributions must be proportional
- **Multiple stock class handling:** Verify class designations (preferred vs common, voting vs non-voting) tracked separately
- **Foreign shareholder withholding:** 30% withholding on dividends (or treaty rate)
- **Constructive dividend test:** Personal expenses, excessive comp, below-market loans → reclassify as dividend
- **Net Operating Loss (NOL) tracking:** NOLs carry forward indefinitely (post-2017), 80% of taxable income limit
- **Section 1244 stock:** Original issue stock loss = ordinary deduction (vs capital loss) up to $50K single / $100K joint

---

## estimated-tax

**Entity-level estimated tax REQUIRED for C-Corp:**

C-Corp pays its OWN federal income tax (unlike S-Corp). Quarterly estimated tax mandatory if expected annual tax >$500.

### Schedule (calendar year)

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1120-W (worksheet only) |
| Q2 | June 15 | Form 1120-W |
| Q3 | September 15 | Form 1120-W |
| Q4 | December 15 | Form 1120-W |

**Note:** Form 1120-W is a worksheet (not filed). Payment via EFTPS, check, or wire.

### Safe Harbor (avoid underpayment penalty)
- 100% of current year tax (annualized), OR
- 100% of prior year tax (if prior year had tax liability AND was full 12-month year)

**Large corporations** (taxable income >$1M in any of last 3 years): Cannot use prior year safe harbor for Q2-Q4 (must use current year method).

### Underpayment Penalty
- Form 2220 if underpaid
- Rate: Federal short-term rate + 3% (compounded daily)

**AI MUST when processing `estimated-tax` form for C-Corp:**
1. Confirm payment is for ENTITY (not shareholder)
2. Calculate based on YTD taxable income × 21% federal rate
3. Apply safe harbor rules
4. Flag if estimated payment <80% of expected annual liability
5. Pay via EFTPS recommended (mandatory for >$2,500/quarter)
6. Recommend CPA review for amounts >$25K
