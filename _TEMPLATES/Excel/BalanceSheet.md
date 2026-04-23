# ⚖️ Balance Sheet Template — Setup Guide

> Point-in-time snapshot of Assets, Liabilities, and Equity. MUST balance to the cent.

**File:** `BalanceSheet.csv`
**Update cadence:** Monthly (at period end)
**Storage:** `_INSTANCES/{instance_id}/06_Financial_Reporting/Balance_Sheet/`

---

## 📋 THE FUNDAMENTAL EQUATION

```
ASSETS = LIABILITIES + EQUITY
```

If this doesn't balance, accounting is WRONG. No exceptions.

---

## 📋 STRUCTURE

Standard US GAAP format:

### ASSETS (ordered by liquidity)
1. Current Assets (convertible to cash within 12 months)
2. Fixed Assets (long-term productive assets)
3. Other Assets (deposits, intangibles)

### LIABILITIES (ordered by maturity)
1. Current Liabilities (due within 12 months)
2. Long-Term Liabilities (due > 12 months)

### EQUITY (ownership claim)
- Common Stock + Preferred Stock (par value issued)
- Additional Paid-in Capital (above par)
- Retained Earnings (accumulated profits)
- Current Year Net Income
- (Distributions/Dividends) — contra
- (Treasury Stock) — contra

---

## 🔧 FORMULAS

### Pull balances from Trial Balance
For each line item:
```excel
=SUMIFS(TB!G:G, TB!A:A, "[Account Number Range]")
```

### Total Current Assets
```excel
=SUM([all current asset lines])
```

### Net Fixed Assets (Gross less Accumulated Depreciation)
```excel
=SUM([gross fixed asset lines]) - [Accumulated Depreciation]
```

### Total Assets
```excel
=[Current Assets] + [Net Fixed Assets] + [Other Assets]
```

### Total Liabilities
```excel
=[Current Liabilities] + [Long-Term Liabilities]
```

### Retained Earnings (end of period)
```excel
=[Beginning RE] + [Current Year Net Income] - [Distributions]
```

### Total Equity
```excel
=[Common Stock] + [APIC] + [Retained Earnings] + [Current Year NI] - [Distributions] - [Treasury Stock]
```

### BALANCE CHECK (critical!)
```excel
=IF(ABS([Total Assets] - ([Total Liabilities] + [Total Equity])) < 0.01,
    "✅ BALANCED",
    "⚠️ OUT OF BALANCE: "&TEXT([Total Assets] - ([Total Liabilities] + [Total Equity]), "$#,##0.00"))
```

### Change in Balance (Prior Period)
```excel
Change $: =D2-E2
Change %: =IFERROR((D2-E2)/E2, 0)
```

---

## 📊 KEY RATIOS (calculate + track)

### Liquidity Ratios

**Current Ratio** = Current Assets / Current Liabilities
- Healthy: 1.5 - 3.0
- Warning: <1.0 (can't cover short-term obligations)
- Excess: >3.0 (too much idle cash)

**Quick Ratio (Acid Test)** = (Current Assets - Inventory) / Current Liabilities
- Healthy: >1.0
- Warning: <0.8

**Working Capital** = Current Assets - Current Liabilities
- Must be positive for healthy operations
- Growing: good (investing in growth)
- Shrinking: concern (cash flow issue)

### Leverage Ratios

**Debt-to-Equity** = Total Liabilities / Total Equity
- Conservative: <0.5
- Moderate: 0.5-1.5
- High: 1.5-3.0
- Distress: >3.0

**Debt-to-Assets** = Total Liabilities / Total Assets
- Healthy: <0.5
- Concerning: >0.7

### Efficiency Ratios

**Days Sales Outstanding (DSO)** = (AR / Revenue) × Days
- Target: <45 days
**Days Payable Outstanding (DPO)** = (AP / Purchases) × Days
- Target: 30-45 days

**Days Inventory Outstanding (DIO)** = (Inventory / COGS) × Days
- Retail: 60-90 days
- Manufacturing: varies widely

**Cash Conversion Cycle** = DSO + DIO - DPO
- Lower = better (money comes back faster)

---

## 🎨 CONDITIONAL FORMATTING

### Out-of-balance alert
- Status cell → Text contains "OUT OF BALANCE" → RED background, WHITE bold text, large font

### Section subtotals
- Subtotal rows → Light blue fill, bold
- Total Assets / Total Liab+Equity → Darker blue fill, white bold

### Contra-asset/equity (negative normal balance)
- Accumulated Depreciation → Red text (displayed as subtraction)
- Distributions → Red text
- Treasury Stock → Red text

### Material changes vs prior period
- Change > 20% → Orange highlight, requires Note
- Change > $10K absolute → Orange highlight

### Negative balance in unexpected places
- Cash < $0 (overdraft) → Red bold
- AR < $0 (customers pre-paid) → Yellow (investigate)
- AP < $0 (we've prepaid vendors) → Yellow (reclassify?)

---

## 📝 PREPARATION CHECKLIST (Month-End)

### Before generating BS:
- [ ] Trial Balance reconciled (debits = credits)
- [ ] Bank accounts reconciled to statements
- [ ] AR aging reviewed, bad debt allowance adjusted
- [ ] Inventory counted and reconciled
- [ ] Fixed asset register updated
- [ ] Accumulated depreciation posted (monthly)
- [ ] Prepaid expenses amortized
- [ ] Accrued salaries/wages/PTO updated
- [ ] Deferred revenue recognized per ASC 606
- [ ] Sales tax liability reconciled to next remittance
- [ ] Income tax accruals posted
- [ ] Inter-company accounts reconciled (if any)
- [ ] Foreign currency translated (if any)
- [ ] Year-to-date Net Income imported from P&L
- [ ] Distributions posted to equity section
- [ ] BALANCE CHECK = $0.00 ✓

---

## ⚠️ COMMON ISSUES

1. **Out of balance by small amounts** — Rounding; investigate if >$1
2. **Out of balance by large amounts:**
   - Missing JE from period
   - Posting error (wrong account type)
   - Current Year Net Income not imported from P&L
   - Distributions posted to wrong account
   - Prior period adjustment booked as current period
3. **Negative Cash** — Overdraft; reclassify to Short-term Debt (2600)
4. **AR showing negative** — Customer overpayment; reclassify to Customer Deposits (2700)
5. **AP showing negative** — Vendor prepaid; reclassify to Prepaid Expense (1200)
6. **Fixed assets without accumulated depreciation** — Missing monthly entry
7. **Intangibles without amortization** — Section 197 amortization over 15 years (tax)
8. **Deferred revenue on Balance Sheet but P&L already recognized** — Revenue rec error

---

## 🔍 TROUBLESHOOTING OUT-OF-BALANCE

### Systematic check:
1. **Compare to Prior Period BS** — Find the account that changed unexpectedly
2. **Check Current Year NI** — Confirm imported correctly from P&L
3. **Check Distributions** — Confirm proper equity posting
4. **Re-run Trial Balance** — Should be balanced first
5. **Check for inter-period items** — Posted to wrong month?
6. **Review manual adjustments** — Last 10 JEs
7. **Verify account type consistency** — No account in wrong section

### If still off:
- **Off by exactly the amount of a recent large JE** → That JE not posted correctly
- **Off by 2x an amount** → Duplicated entry
- **Off by round numbers** → Entered in wrong column or missing zero
- **Off by ~50% of something** → Only one side of JE posted

---

## 📊 COMPARATIVE ANALYSIS

Always present BS với comparison:
- Current period vs Prior month (show monthly trend)
- Current period vs Prior year (seasonality/growth)
- Current period vs Budget (performance vs plan)
- Show $ change and % change

---

## 🏦 BANK/INVESTOR VIEW

For external stakeholders, emphasize:
- **Current Ratio** (can you pay bills?)
- **Debt-to-Equity** (how leveraged?)
- **Working Capital** (cash flow health)
- **Asset quality** (what % is actually liquid?)
- **Growth** (year-over-year equity growth)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
