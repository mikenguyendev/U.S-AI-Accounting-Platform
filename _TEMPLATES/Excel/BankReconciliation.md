# 🏦 Bank Reconciliation Template — Setup Guide

> 2-way reconciliation worksheet: Bank statement vs Book (GL) balance.

**File:** `BankReconciliation.csv`
**Update cadence:** Monthly (per bank account)
**Storage:** `_INSTANCES/{instance_id}/03_Bank_Reconciliation/Reconciliation_Reports/FY{year}/`

---

## 📋 CONCEPT

Bank Reconciliation = finding differences between:
- **Bank Statement Balance** (what bank says)
- **Book Balance** (what GL says)

These differ due to timing:
- **Bank side:** Deposits in transit (not yet cleared), outstanding checks (not yet cashed)
- **Book side:** Unrecorded items like bank fees, interest earned, NSF checks

### Formula
```
Bank Side:
  Bank Balance per statement
  + Deposits in Transit
  - Outstanding Checks
  = Adjusted Bank Balance

Book Side:
  Book Balance per GL
  + Interest/Credits (unrecorded)
  - Fees/NSF/Errors (unrecorded)
  = Adjusted Book Balance

VERIFY: Adjusted Bank Balance = Adjusted Book Balance ✓
```

---

## 🔧 FORMULAS TO ADD

### Adjusted Bank Balance
```excel
=[Bank_Balance] + [Total_Deposits_in_Transit] - [Total_Outstanding_Checks]
```

### Adjusted Book Balance
```excel
=[Book_Balance] + [Total_Additions_to_Book] - [Total_Deductions_from_Book]
```

### Difference Check
```excel
=ABS([Adjusted_Bank_Balance] - [Adjusted_Book_Balance])
```

### Status
```excel
=IF(ABS([Adjusted_Bank_Balance]-[Adjusted_Book_Balance])<0.01, "✅ RECONCILED", "⚠️ DIFFERENCE: "&TEXT([Adjusted_Bank_Balance]-[Adjusted_Book_Balance],"$#,##0.00"))
```

---

## 📂 WORKFLOW

### Step 1: Gather Data (Day 1)
- Download bank statement (PDF + CSV)
- Pull GL Cash account activity for period
- Get outstanding check list from prior month

### Step 2: Match Items (Day 2)
- Mark cleared deposits
- Mark cleared checks
- Identify unrecorded bank fees/interest
- Flag discrepancies

### Step 3: Build Reconciliation (Day 2-3)
- Enter Bank Balance (top of template)
- List Deposits in Transit
- List Outstanding Checks
- Enter Book Balance (from TB)
- List unrecorded items

### Step 4: Post Adjusting JEs (Day 3)
For each unrecorded bank item, post JE:
- **Interest earned:** Dr. Cash / Cr. Interest Income (7010)
- **Bank fees:** Dr. Bank Fees (6800) / Cr. Cash
- **NSF check:** Dr. AR (1100) / Cr. Cash (re-establish receivable)
- **ACH returns:** similar to NSF

### Step 5: Verify Reconciliation (Day 3)
- Adjusted Bank = Adjusted Book? ✓
- If difference > $0.01, INVESTIGATE line by line

### Step 6: Sign Off (Day 5)
- Preparer signs
- Controller reviews and signs
- File in permanent records

---

## 🎨 CONDITIONAL FORMATTING

### Reconciled / Not Reconciled status
- Status cell = "RECONCILED" → Green background
- Status cell starts with "DIFFERENCE" → Red background, bold

### Old outstanding checks (stale-dated >6 months)
- Check date > 6 months → Yellow highlight, trigger stale check review

### Large unrecorded items
- Amount > $1,000 unrecorded → Orange highlight, requires JE

---

## 🔍 INVESTIGATION CHECKLIST (if not reconciled)

| Difference Pattern | Likely Cause |
|--------------------|--------------|
| Off by exactly 2x an amount | Transposed digit or duplicated entry |
| Off by $9 or multiples of 9 | Classic transposition error (54 vs 45) |
| Off by small amounts ($0.01-$0.50) | Rounding; acceptable within $1 |
| Off by whole $100s or $1,000s | Decimal error or missing/extra zero |
| Off by bank fee amount | Fee not posted to GL |
| Off by interest amount | Interest not posted to GL |
| Off by exact check amount | Check cleared but not recorded (or vice versa) |
| Growing difference over months | Compounding unresolved issue — re-reconcile from clean start |

---

## 📝 SAMPLE INTERPRETATION

```
Bank Statement Ending Balance:      $12,500.00
+ Deposits in Transit:                  500.00  (Check deposited 4/30, cleared 5/2)
- Outstanding Checks:                 1,200.00  (Check #1005 $800, #1006 $400)
= Adjusted Bank Balance:            $11,800.00

GL Cash Balance:                    $11,850.00
+ Interest Earned:                        5.00  (not yet posted)
- Bank Fees:                             55.00  (not yet posted — $25 service + $30 wire)
= Adjusted Book Balance:            $11,800.00 ✓ RECONCILED
```

---

## 🔒 MULTI-ACCOUNT RECONCILIATION

If business has multiple bank accounts (checking, savings, payroll), reconcile EACH separately:
- Separate worksheet per account in workbook
- Or separate files per account
- Naming: `YYYYMM_BankRecon_[BankName]_[AccountLast4].xlsx`

Example:
- `202604_BankRecon_Chase_Business_1234.xlsx`
- `202604_BankRecon_Chase_Savings_5678.xlsx`
- `202604_BankRecon_Mercury_Payroll_9012.xlsx`

---

## ⚠️ COMMON ISSUES

1. **Stale outstanding checks (>6 months)** — Contact payee, reissue or void
2. **Unidentified transactions** — Ask bank, customer, or vendor
3. **Duplicate charges** — Dispute with bank immediately
4. **Unauthorized charges** — Fraud alert, change credentials
5. **Timing of reconciliation** — Do BEFORE month-end close, not after
6. **Not reconciling monthly** — Issues compound, error hunting gets harder
7. **Only reconciling one account** — All accounts need monthly recon

---

## 💡 AUTOMATION TIPS

- **Bank feeds into QuickBooks/Xero:** Auto-match 80-90% of transactions
- **Recurring rules:** Set up for predictable transactions (rent, subscriptions)
- **Machine learning category prediction:** Most modern software
- **Still need manual review:** 10-20% of items require human judgment

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
