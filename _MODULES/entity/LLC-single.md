# Single-Member LLC (LLC-single) — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/LLC-single.md#section-id}}` directives.**

**Entity Type:** Single-Member Limited Liability Company
**Tax Treatment:** Disregarded entity (default) — Schedule C on owner's 1040
**Primary Tax Form:** Schedule C (filed with Form 1040)
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings (if has employees) |
| **January 31** | Form 941 (Q4) | Q4 payroll tax (if has employees) |
| **April 15** | **Form 1040 + Schedule C** | Owner's personal return with business income |
| **April 15** | Form 1040-ES (Q1) | Q1 estimated tax (combines income + SE tax) |
| **April 15** | Form 4868 | Extension request (extends to October 15) |
| **April 30** | Form 941 (Q1) | Q1 payroll tax (if has employees) |
| **June 15** | Form 1040-ES (Q2) | Q2 estimated tax |
| **July 31** | Form 941 (Q2) | Q2 payroll tax |
| **September 15** | Form 1040-ES (Q3) | Q3 estimated tax |
| **October 15** | Form 1040 (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax |
| **January 15 (next yr)** | Form 1040-ES (Q4) | Q4 estimated tax |

**Note:** No separate entity tax return cho LLC-single (default treatment). All business income/loss flows to owner's 1040.

---

## federal-obligations

**Entity-level returns:**
- **NONE for income tax** (disregarded entity, default)
- **Form 941** (quarterly) — IF has employees
- **Form 940** (annual) — IF has employees
- **Form W-2/W-3** (annual) — IF has employees
- **Form 1099-NEC** (annual) — Contractor payments >$600/year (issued by LLC if it's the payer)

**Owner-level (default disregarded treatment):**
- **Form 1040** + **Schedule C** (Profit or Loss from Business) — Annual
- **Schedule SE** (Self-Employment Tax) — If net earnings ≥$400
- **Form 1040-ES** (quarterly) — Estimated tax voucher

**Optional: Elect to be taxed as Corporation**
- File Form 8832 → C-Corp treatment
- File Form 8832 + Form 2553 → S-Corp treatment
- Election typically for tax savings at higher income levels

---

## critical-rules

### Eligibility
- **Single owner only** (multi-member becomes LLC-multi taxed as partnership)
- Owner can be individual, trust, or another disregarded entity (NOT another LLC-multi)
- Default: disregarded entity
- Optional: elect C-Corp or S-Corp tax treatment

### Self-Employment Tax (KEY consideration)
- **15.3%** on net earnings from self-employment (12.4% SS + 2.9% Medicare)
- SS portion capped at $168,600 (2026 wage base)
- Additional Medicare 0.9% on earnings >$200K (single) / $250K (married)
- **Deductible above-the-line:** half of SE tax (employer-equivalent portion)

### Owner Compensation
- Owner does NOT take W-2 salary (single-member LLC default)
- Instead: **owner draws** (transfer cash from business to personal account)
- Draws ARE NOT deductible (they're not expenses)
- All net profit taxed via Schedule C, regardless of how much owner withdraws

### Liability Protection
- LLC structure limits owner's personal liability for business debts
- BUT requires:
  - Separate business bank account (no commingling)
  - Operating Agreement on file
  - Adequate capitalization
  - Proper LLC formalities
- Failure → "piercing the corporate veil" → personal liability exposure

### Why Elect S-Corp Treatment?
- Default LLC-single: ALL net income subject to 15.3% SE tax
- S-Corp election: Only W-2 portion subject to FICA (15.3%); distributions NOT subject to FICA
- Break-even typically at $40K-50K net income (savings exceed compliance costs)
- Trade-off: more complexity (payroll, separate return, reasonable comp rule)

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 1040-ES (prior year) |
| Jan 31 | W-2, W-3, 1099-NEC, Form 940 (if employer) |
| Apr 15 | **Form 1040 + Schedule C** + Q1 estimated |
| Apr 30 | Q1 Form 941 (if employer) |
| Jun 15 | Q2 1040-ES |
| Jul 31 | Q2 Form 941 (if employer) |
| Sep 15 | Q3 1040-ES |
| Oct 15 | Extended Form 1040 |
| Oct 31 | Q3 Form 941 (if employer) |

---

## owner-compensation

⚠️ **OWNER DRAWS — NOT a Business Expense**

Owner of single-member LLC takes **owner draws**, NOT salary:

### Owner Draw vs Salary
| Aspect | Owner Draw (LLC-single default) | W-2 Salary (S-Corp election) |
|--------|--------------------------------|------------------------------|
| Tax timing | All net profit taxed regardless of draw | Only salary + distribution taxed |
| FICA/SE tax | 15.3% on ALL net profit | 15.3% only on salary portion |
| Withholding | None (owner pays via 1040-ES) | Yes (federal + state + FICA) |
| Documentation | Bank transfer Owner's Equity → Personal | Payroll register + W-2 |
| Deductible to business | NO | YES (salary expense) |

### Tax Impact Example
**Net business profit: $100,000**

LLC-single (default):
- Schedule C net income: $100,000
- SE tax: $14,130 (15.3% on 92.35% of net)
- Income tax: variable based on bracket
- **All $100K taxed regardless of how much owner withdrew**

LLC-single → S-Corp election (with $50K W-2):
- W-2 wages: $50,000 → FICA $7,650 (split employer/employee)
- Distribution: $50,000 → no FICA
- Total FICA: $7,650 vs $14,130 (savings ~$6,480)

### Documentation Required
- Owner's Equity account in COA (3000 series)
- Track contributions vs distributions separately
- Owner's draw posted: Dr. Owner's Equity / Cr. Cash
- Annual reconciliation cho Schedule C

### Section 199A Qualified Business Income (QBI) Deduction
- 20% deduction on qualified business income (Schedule C income qualifies)
- Phase-out: $191,950 (single) / $383,900 (married joint) for 2024 — verify 2026 thresholds
- Specified Service Trade or Business (SSTB): doctors, lawyers, consultants — extra restrictions

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form for LLC-single (default):**

1. Confirm structure: default disregarded entity, NOT S-Corp election
2. Process as **Owner Draw**, NOT salary:
   ```
   Dr. 3500 - Owner's Draw      $XXX.XX
       Cr. [Cash account]              $XXX.XX
   ```
3. NO payroll tax calculation (owner pays via 1040-ES)
4. NO W-2 issued to owner
5. Track YTD owner draws cho Schedule C reconciliation
6. If net income trending >$50K → recommend evaluating S-Corp election (Form 2553 + Form 8832)
7. Calculate projected SE tax for owner planning:
   - Net SE income × 92.35% × 15.3% = SE tax
   - Plus federal income tax based on owner's bracket
8. Save documentation to: `05_Payroll/Owner_Compensation/`

**File naming:** `YYYYMMDD_OwnerDraw_LLC_FY{year}.xlsx`

**If S-Corp election made:** Switch to S-Corp protocol (file 2553 + payroll setup).

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Owner trying to put themselves on W-2 payroll (default LLC-single doesn't allow — must elect S-Corp first)
- ⚠️ Personal expenses paid from business account → veil piercing risk + non-deductible
- ⚠️ Business + personal funds in same bank account → veil piercing risk
- ⚠️ Net income >$50K + still default LLC → S-Corp election would save tax (recommend CPA review)
- ⚠️ Q1-Q4 estimated tax not paid → underpayment penalty (Form 2210)
- ⚠️ Schedule C net loss for 3+ consecutive years → IRS hobby loss rule risk
- ⚠️ No Operating Agreement on file → veil piercing risk
- ⚠️ Multi-member operations but only filing as single-member → IRS reclassification risk

---

## validation-rules

### LLC-single Specific Validation

- **Disregarded entity check:** Verify no Form 8832 / Form 2553 filed (else use C-Corp / S-Corp module)
- **Owner draws posted correctly:** Dr. Owner's Equity (NOT expense)
- **1099 issuance to LLC vendors:** Issue 1099-NEC to single-member LLCs (treated as individual)
- **EIN vs SSN:** LLC-single can use SSN OR get EIN (EIN required if has employees or excise tax obligations)
- **State LLC filing fee:** Most states require annual LLC fee (varies $50-$800)
- **Operating Agreement:** Should exist even with single member (state may require)

---

## estimated-tax

**Pass-through to owner:** LLC-single (default) does NOT pay federal entity tax. Owner pays personal estimated tax.

### Owner-Level Estimated Tax Schedule

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1040-ES |
| Q2 | June 15 | Form 1040-ES |
| Q3 | September 15 | Form 1040-ES |
| Q4 | January 15 (next year) | Form 1040-ES |

### Calculation
**Estimated tax = (Federal income tax + SE tax + Additional Medicare) ÷ 4**

Example (single owner, $100K net SE income):
- Income tax (~22% effective): ~$15,000
- SE tax: $14,130
- Total annual: ~$29,130
- Quarterly: ~$7,283

### Safe Harbor (avoid penalty)
- 100% of prior year tax liability (110% if AGI >$150K), OR
- 90% of current year tax

**AI MUST when processing `estimated-tax` form for LLC-single:**
1. Confirm payment is for OWNER (Form 1040-ES), not entity
2. Calculate combined: income tax + SE tax + additional Medicare
3. Account for QBI deduction (Section 199A)
4. Apply safe harbor rules
5. Recommend CPA review for amounts >$10K/quarter
6. Save to: `04_Tax_Compliance/Estimated_Tax_Payments/Owner/`
