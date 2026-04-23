# Sole Proprietorship — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/Sole-Prop.md#section-id}}` directives.**

**Entity Type:** Sole Proprietorship
**Tax Treatment:** Owner reports on Schedule C (Form 1040)
**Primary Tax Form:** Schedule C (filed with Form 1040)
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings (if has employees) |
| **January 31** | Form 941 (Q4) | Q4 payroll tax (if has employees) |
| **April 15** | **Form 1040 + Schedule C + Schedule SE** | Owner's personal return with business income + SE tax |
| **April 15** | Form 1040-ES (Q1) | Q1 estimated tax (income + SE) |
| **April 15** | Form 4868 | Extension request (extends to October 15) |
| **April 30** | Form 941 (Q1) | Q1 payroll tax (if employer) |
| **June 15** | Form 1040-ES (Q2) | Q2 estimated tax |
| **July 31** | Form 941 (Q2) | Q2 payroll tax |
| **September 15** | Form 1040-ES (Q3) | Q3 estimated tax |
| **October 15** | Form 1040 (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax |
| **January 15 (next yr)** | Form 1040-ES (Q4) | Q4 estimated tax |

**No separate entity tax return** — business is part of owner's personal return.

---

## federal-obligations

**Entity-level returns:**
- **NONE for income tax** (sole prop is owner)
- **Form 941** (quarterly) — IF has employees
- **Form 940** (annual) — IF has employees
- **Form W-2/W-3** (annual) — IF has employees
- **Form 1099-NEC** (annual) — Contractor payments >$600/year (issued by sole prop if it's the payer)

**Owner-level:**
- **Form 1040** (annual) — personal income tax return
- **Schedule C** — Profit or Loss from Business
- **Schedule SE** — Self-Employment Tax (if net earnings ≥$400)
- **Form 1040-ES** (quarterly) — Estimated tax voucher

---

## critical-rules

### Eligibility & Formation
- **No formal filing required** to start (just start operating)
- Optional: DBA (Doing Business As) registration nếu using trade name
- Optional: EIN (required if has employees, otherwise can use SSN)
- Optional: Business license (city/county requirement varies)
- Default for any unincorporated single-owner business

### NO Liability Protection
- ⚠️ **CRITICAL:** Owner has UNLIMITED PERSONAL LIABILITY for all business debts/lawsuits
- Personal assets (home, car, savings) at risk
- Reason most businesses convert to LLC ASAP
- Sole prop appropriate only for: very low-risk businesses, side hustles, transitional structure

### Self-Employment Tax
- **15.3%** on net earnings from self-employment
- Same as LLC-single default
- Half of SE tax deductible above-the-line (employer portion)

### Owner Compensation
- **No salary** — owner takes "owner draws"
- Draws are NOT deductible (not a business expense)
- All net profit taxed via Schedule C, regardless of withdrawal amount

### EIN Decision
- **NOT required** if no employees and no excise tax obligations
- **Recommended** anyway:
  - Allows business banking (some banks won't open account with SSN only)
  - Required for many vendor accounts
  - Easier transition to LLC/Corp later
  - Reduces SSN exposure

### When to Convert to LLC/S-Corp
- **Convert to LLC:** When liability risk increases (employees, customer interactions, contracts)
- **Elect S-Corp:** When net income >$50K and want to save SE tax
- Conversion is straightforward (file LLC, transfer assets, get EIN)

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 1040-ES (prior year) |
| Jan 31 | W-2, W-3, 1099-NEC (if employer) |
| **Apr 15** | **Form 1040 + Schedule C + SE** + Q1 estimated |
| Apr 30 | Q1 Form 941 (if employer) |
| Jun 15 | Q2 1040-ES |
| Jul 31 | Q2 Form 941 (if employer) |
| Sep 15 | Q3 1040-ES |
| Oct 15 | Extended Form 1040 |
| Oct 31 | Q3 Form 941 (if employer) |

---

## owner-compensation

⚠️ **OWNER DRAWS — Same as LLC-single**

Sole proprietor takes draws, NOT salary:

### Owner Draw Structure
- Cash transfer from business account → personal account
- NOT deductible (not a business expense)
- All net profit on Schedule C taxed regardless of draw amount
- No payroll, no W-2, no withholding

### Tax Calculation
**Example: Net business profit $80,000**
- Schedule C net income: $80,000
- SE tax: $80,000 × 92.35% × 15.3% = $11,304
- Half SE tax deductible: $5,652
- AGI: $80,000 - $5,652 = $74,348
- Federal income tax based on bracket
- All taxed regardless of how much owner withdrew

### Section 199A QBI Deduction
- 20% deduction on qualified business income
- Schedule C income qualifies (subject to phase-out)
- Specified Service Trade or Business (SSTB) restrictions apply

### Documentation Required
- Owner's Equity / Drawing account in COA
- Bank transfers documented monthly
- Bookkeeping consistent (separate business + personal accounts CRITICAL)
- Schedule C reconciliation annually

### Comparison to Other Structures (Net Income $100K)

| Structure | SE Tax | Income Tax | Liability | Complexity |
|-----------|--------|------------|-----------|------------|
| Sole Prop | $14,130 | Owner's bracket | UNLIMITED | Lowest |
| LLC-single | $14,130 | Owner's bracket | Limited | Low |
| LLC + S-Corp election | ~$7,650 (on $50K W-2) | Owner's bracket | Limited | Medium |
| C-Corp | $7,650 (on $50K W-2) | Corp 21% + dividend tax | Limited | Highest |

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form for Sole-Prop:**

1. Confirm structure is sole prop (not LLC, not corporation)
2. Process as **Owner Draw**:
   ```
   Dr. 3500 - Owner's Drawing      $XXX.XX
       Cr. [Cash account]                  $XXX.XX
   ```
3. NO payroll tax calculation (owner pays via 1040-ES)
4. NO W-2 (owner is not employee)
5. Track YTD owner draws cho Schedule C reconciliation
6. If net income trending >$50K → recommend evaluating LLC formation + S-Corp election (Form 2553)
7. Calculate projected tax for owner planning:
   - SE tax: Net SE × 92.35% × 15.3%
   - Half SE deductible
   - Income tax on (AGI - Standard/Itemized)
   - Net cash flow estimate
8. **STRONGLY recommend** liability assessment if business has any of:
   - Customer-facing services
   - Employees
   - Physical premises (slip-and-fall risk)
   - Product liability exposure
   - Significant contracts
9. Save documentation to: `05_Payroll/Owner_Compensation/`

**File naming:** `YYYYMMDD_OwnerDraw_SoleProp_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Owner trying to put themselves on W-2 payroll → MAJOR ERROR (sole prop can't payroll owner)
- ⚠️ Personal expenses paid from business account → not deductible + audit risk
- ⚠️ Business + personal funds in same bank account → IRS audit difficulty + record-keeping nightmare
- ⚠️ Net income >$50K with significant liability exposure → recommend LLC conversion
- ⚠️ Net income >$50K → evaluate S-Corp election for SE tax savings
- ⚠️ Estimated tax not paid quarterly → underpayment penalty (Form 2210)
- ⚠️ Schedule C net loss for 3+ consecutive years → IRS hobby loss rule (Section 183)
- ⚠️ Has employees but no EIN → must obtain EIN (Form SS-4)
- ⚠️ Hiring contractors >$600/year without W-9 on file → can't issue 1099-NEC properly
- ⚠️ Operating in regulated industry without business license → city/state penalties

---

## validation-rules

### Sole-Prop Specific Validation

- **Single owner only:** If brings in second owner → automatically becomes partnership (Form 1065)
- **EIN vs SSN:** Either works for tax filing, but EIN strongly recommended
- **Schedule C Box A (principal business):** Must use IRS principal business code (6-digit NAICS)
- **Business expense documentation:** Receipts >$75 required (IRS Pub 463)
- **Home office deduction:** Section 280A — strict requirements (exclusive + regular use)
- **Vehicle expenses:** Standard mileage vs actual expense — must choose first year, can't switch (sometimes)
- **Net Operating Loss (NOL):** Sole prop NOL carries forward indefinitely (post-2017), 80% income limit

---

## estimated-tax

**Pass-through to owner:** Sole prop has NO entity-level tax. Owner pays personal estimated tax.

### Estimated Tax Schedule

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1040-ES |
| Q2 | June 15 | Form 1040-ES |
| Q3 | September 15 | Form 1040-ES |
| Q4 | January 15 (next year) | Form 1040-ES |

### Calculation
**Estimated tax = (Federal income tax on Schedule C net + SE tax + Additional Medicare) ÷ 4**

Adjustments:
- Subtract: half of SE tax (above-the-line deduction)
- Subtract: Section 199A QBI deduction (20%)
- Subtract: Self-employed health insurance, retirement contributions

### Safe Harbor (avoid Form 2210 penalty)
- 100% of prior year tax (110% if AGI >$150K), OR
- 90% of current year tax

### Tools
- IRS Withholding Estimator: https://www.irs.gov/individuals/tax-withholding-estimator
- Form 1040-ES worksheet
- Most accounting software (QuickBooks Self-Employed, etc.)

**AI MUST when processing `estimated-tax` form for Sole-Prop:**
1. Confirm payment is for OWNER personal (Form 1040-ES)
2. Calculate combined: income tax + SE tax + additional Medicare
3. Account for QBI deduction (20%)
4. Account for SE tax deduction (half)
5. Apply safe harbor rules
6. Recommend CPA review for amounts >$10K/quarter
7. Save to: `04_Tax_Compliance/Estimated_Tax_Payments/Owner/`
