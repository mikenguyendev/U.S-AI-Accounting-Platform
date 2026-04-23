# 📊 Trial Balance Template — Setup Guide

> Monthly trial balance pulled from GL, used to verify all accounts balance before generating financial statements.

**File:** `TrialBalance.csv`
**Update cadence:** Daily during close, monthly sign-off
**Storage:** `_INSTANCES/{instance_id}/06_Financial_Reporting/Monthly_Close/{YYYY-MM}/`

---

## 📋 STRUCTURE

| Column | Type | Notes |
|--------|------|-------|
| Account_Number | Text | From COA |
| Account_Name | Text | From COA |
| Account_Type | Enum | Asset/Liability/Equity/Revenue/COGS/Expense/Other_Income/Other_Expense |
| Opening_Balance | Currency | FY opening + sign per normal balance |
| YTD_Debits | Currency | Sum of all debit entries YTD |
| YTD_Credits | Currency | Sum of all credit entries YTD |
| Current_Balance | Formula | Opening + YTD activity |
| Prior_Period_Balance | Currency | Last month balance for comparison |
| Change | Formula | Current - Prior |
| Notes | Text | Explanations for unusual changes |

---

## 🔧 FORMULAS

### Current Balance calculation (depends on normal balance)
For accounts with normal **DEBIT** balance (Asset, Expense, COGS, Other_Expense):
```excel
Current_Balance = Opening + YTD_Debits - YTD_Credits
```

For accounts with normal **CREDIT** balance (Liability, Equity, Revenue, Other_Income):
```excel
Current_Balance = -(Opening + YTD_Credits - YTD_Debits)
```

**Simplified formula for all accounts (sign depends on Account_Type):**
```excel
=IF(OR(C2="Asset",C2="Expense",C2="COGS",C2="Other_Expense"),
    D2+E2-F2,
    -(D2+F2-E2))
```

### YTD Debits/Credits from GL (using SUMIFS)
```excel
=SUMIFS(GL!F:F, GL!C:C, A2)  // YTD Debits for this account
=SUMIFS(GL!G:G, GL!C:C, A2)  // YTD Credits for this account
```

Where GL is Journal Entry log sheet with columns matching JE template.

### Balance Check (bottom row)
```excel
Total Debits:  =SUM(E2:E99)
Total Credits: =SUM(F2:F99)
Difference:    =SUM(E2:E99) - SUM(F2:F99)
Status:        =IF(ABS(SUM(E2:E99)-SUM(F2:F99))<0.01, "✅ BALANCED", "⚠️ UNBALANCED BY $"&TEXT(ABS(SUM(E2:E99)-SUM(F2:F99)),"#,##0.00"))
```

### Change calculation
```excel
=G2-H2  // Current - Prior
```

---

## 🎨 CONDITIONAL FORMATTING

### Highlight unbalanced total
- Status cell → Contains "UNBALANCED" → Red fill, white bold text

### Highlight material changes (>10% or >$1K)
- Select Change column
- Conditional Formatting → Formula:
```excel
=OR(ABS(I2)>1000, ABS(I2/H2)>0.1)
```
→ Orange background, border highlight

### Highlight zero-balance accounts (candidates for inactive)
- Current_Balance = 0 AND Opening_Balance = 0 → Gray text

### Highlight accounts without notes when change is material
- Change > threshold AND Notes is blank → Yellow "needs explanation" flag

---

## ✅ VALIDATION RULES

1. **Total Debits = Total Credits** (within $0.01 tolerance for rounding)
2. **Account_Number unique** (no duplicates)
3. **Account_Type must match COA definition**
4. **Opening_Balance:** Last year's ending = this year's opening (carry forward check)
5. **Material changes require Notes:** >10% or >$1K change without explanation flags review
6. **Negative balances in unexpected places:**
   - Asset with credit balance → INVESTIGATE
   - Liability with debit balance → INVESTIGATE
   - Revenue with debit balance → only if returns exceed sales (RARE)

---

## 📊 GROUPING FOR SUBTOTALS

Add SUBTOTAL formulas to group by Account_Type:

```
Row Insertion pattern:
Row 1:    Header
Rows 2-N: Assets
Row N+1:  "TOTAL ASSETS" with =SUBTOTAL(9, D2:DN)
Rows N+2..M: Liabilities
Row M+1:  "TOTAL LIABILITIES"
Rows M+2..: Equity
Row :     "TOTAL LIABILITIES + EQUITY" (should equal Total Assets)
Rows: Revenue
Row:      "TOTAL REVENUE"
Rows: COGS
Row:      "GROSS PROFIT" = Revenue - COGS
Rows: Expenses
Row:      "OPERATING INCOME" = Gross Profit - Expenses
Rows: Other Income/Expense
Row:      "NET INCOME" = Operating Income + Other Income - Other Expense
```

---

## 🔄 MONTH-END CLOSE USAGE

1. **Day 1–3:** Post all remaining entries for prior month
2. **Day 4:** Generate preliminary TB
3. **Day 5:** Review material changes, book adjusting entries (accruals, depreciation, prepaid amortization)
4. **Day 6:** Re-generate TB, verify balance
5. **Day 7:** Controller sign-off on TB
6. **Day 8:** Generate P&L + BS + CF from TB
7. **Day 10:** Lock period

---

## 📝 SAMPLE TB INTERPRETATION

From provided data:
- **Total Assets = $108,488.90** (Cash + AR + Prepaid + Computer - AccDep)
- **Total Liabilities = $10,700.00** (AP + CC + Accrued + Sales Tax)
- **Total Equity = $68,366.67** (Stock + RE)
- **Net Income YTD ≈ $29,422.23** (Revenue - COGS - Expenses + Other Income)

Accounting equation: $108,488.90 = $10,700 + $68,366.67 + $29,422.23 ≈ ✓ (rounds to balance)

---

## ⚠️ COMMON ISSUES

1. **Off by small amounts ($0.01-$0.10)** — Rounding from currency conversion; acceptable within $1
2. **Off by material amounts** — Missing JE, posting error, wrong account; investigate line-by-line
3. **Opening balances don't match prior year-end** — Year-end close not properly carried forward
4. **New accounts added mid-period** — Include in TB immediately, don't wait for month-end
5. **Inactive accounts showing balances** — Either reactivate or reclassify/write off

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
