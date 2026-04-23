# 📊 Budget vs Actual Template — Setup Guide

> Monthly variance analysis comparing Budget to Actual + forecast to year-end.

**File:** `BudgetVsActual.csv`
**Update cadence:** Monthly (post P&L finalization)
**Storage:** `_INSTANCES/{instance_id}/07_Budget_Variance_Analysis/Variance_Reports/`

---

## 📋 STRUCTURE

For each line item:
- **Annual Budget** — Full year planned amount
- **YTD Budget** — Pro-rata based on time elapsed (or seasonality-adjusted)
- **YTD Actual** — From accounting records
- **Variance $** — Actual - Budget (sign convention varies)
- **Variance %** — Variance / Budget
- **Variance Type** — Favorable / Unfavorable / On Plan
- **Forecast Full Year** — Projected based on YTD trend
- **FY Variance vs Budget** — Forecast - Annual Budget
- **Notes/Action Items** — Explanation + remediation

---

## 🔧 FORMULAS

### Variance calculations

**For Revenue (where higher = good):**
```excel
Variance $: =Actual - Budget   [positive = favorable]
Variance %: =IFERROR((Actual - Budget) / Budget, 0)
```

**For Expenses (where lower = good):**
```excel
Variance $: =Budget - Actual   [positive = favorable, opposite sign convention]
Variance %: =IFERROR((Budget - Actual) / Budget, 0)
```

**OR consistent convention (Actual - Budget):**
- Revenue: positive variance = favorable
- Expense: positive variance = unfavorable
→ Add Variance_Type column to label clearly

### Variance Type
```excel
=IF(ABS(Variance_Pct) < 0.05, "On Plan",
  IF(AND(Section="Revenue", Actual > Budget), "Favorable",
    IF(AND(Section="Revenue", Actual < Budget), "Unfavorable",
      IF(AND(Section="Expense", Actual < Budget), "Favorable",
        "Unfavorable"))))
```

### Pro-Rata YTD Budget
For non-seasonal businesses:
```excel
=Annual_Budget / 12 * Months_Elapsed
```

For seasonal businesses, use specific monthly budgets.

### Forecast Full Year
**Linear extrapolation:**
```excel
=YTD_Actual / Months_Elapsed * 12
```

**Run-rate from latest quarter:**
```excel
=(Q1 + Q2 actual + estimated Q3 + Q4) [more accurate for trending businesses]
```

### Period Variance (single month)
```excel
=Current_Month_Actual - Current_Month_Budget
```

---

## 🎨 CONDITIONAL FORMATTING

### Color-code variances by severity
- |Variance %| < 5% → Green (On Plan)
- 5% ≤ |Variance %| < 10% → Yellow (Watch)
- 10% ≤ |Variance %| < 25% → Orange (Investigate)
- |Variance %| ≥ 25% → Red bold (Critical)

### Favorable vs Unfavorable
- Variance Type = "Favorable" → Green text
- Variance Type = "Unfavorable" → Red text
- Variance Type = "On Plan" → Default text

### Forecast misses
- Forecast Full Year < Annual Budget by >5% → Yellow row (Revenue) / Red row (Expense)

### Action items required
- |Variance %| > 10% AND Notes blank → Yellow "EXPLANATION REQUIRED"

---

## ✅ MONTHLY VARIANCE PROCESS

### Step 1: Pull P&L data (after close)
- YTD Actuals from finalized P&L
- Match to budget line items

### Step 2: Calculate variances
- Dollar and percentage
- Categorize Favorable/Unfavorable/On Plan

### Step 3: Investigate material variances
**Threshold rule:** Anything > 10% OR > $1K requires explanation.

For each material variance, determine:
- **Root cause:** What drove the variance?
- **One-time vs recurring:** Will this continue?
- **Controllable vs not:** Can we change it?
- **Forecast impact:** Update full-year forecast

### Step 4: Document action items
- For unfavorable controllable variances: corrective action
- For favorable: investigate to ensure sustainability
- For one-time: document and exclude from forecast

### Step 5: Re-forecast remaining year
- Update Forecast Full Year column
- Compare against Annual Budget
- Identify need for budget revision

### Step 6: Distribute to stakeholders
- Department heads: their section
- CFO/Owner: full report
- Board: 1-page executive summary

---

## 📊 VARIANCE ANALYSIS FRAMEWORK

### Revenue Variance Decomposition
```
Total Variance = Volume Variance + Price Variance + Mix Variance

Volume Variance = (Actual Units - Budget Units) × Budget Price
Price Variance  = (Actual Price - Budget Price) × Actual Units
Mix Variance    = Difference due to product mix changes
```

### Expense Variance Decomposition
```
For controllable spending:
- Spending Variance: more or less spent at same activity level
- Volume Variance: cost varied due to higher/lower activity

Salary variance breakdown:
- Headcount variance: actual hires vs planned
- Wage rate variance: salary rates higher/lower than budgeted
- Overtime variance: more/less OT than planned
- Benefits variance: rate changes
```

### COGS Variance Decomposition (for Manufacturing)
```
Material Variance:
- Price Variance: (Actual Price - Standard Price) × Actual Quantity
- Usage Variance: (Actual Quantity - Standard Quantity) × Standard Price

Labor Variance:
- Rate Variance: (Actual Rate - Standard Rate) × Actual Hours
- Efficiency Variance: (Actual Hours - Standard Hours) × Standard Rate

Overhead Variance:
- Budget Variance: Actual OH - Budget OH
- Volume Variance: (Actual hours - Budgeted hours) × Standard OH rate
```

---

## 📝 VARIANCE EXPLANATION TEMPLATES

### Revenue Underperformance
- "Sales pipeline conversion 15% below plan"
- "New product launch delayed 6 weeks"
- "Lost top 5 customer (X% of revenue)"
- "Pricing pressure required 5% discount"

### Revenue Overperformance
- "Pulled forward Q3 deals into Q2"
- "New BD hire ramped 3 weeks faster"
- "Pricing increase took effect"
- "New channel partnership"

### Expense Underspend
- "Marketing campaign delayed (will spend Q2)"
- "Vendor renegotiated contract 15% lower"
- "Hiring delayed (open role)"
- "Travel restrictions in place"

### Expense Overspend
- "New hire 2 weeks early"
- "Software price increase (vendor)"
- "Unforeseen legal matter"
- "FX impact on imported supplies"

---

## 🎯 BUDGETING METHODOLOGIES

### Top-Down (CEO sets total, allocate down)
- Pros: Strategic alignment, faster
- Cons: Department head buy-in lower

### Bottom-Up (Departments propose, CFO consolidates)
- Pros: More accurate, more buy-in
- Cons: Tendency to inflate

### Zero-Based (Justify every line item from zero each year)
- Pros: Forces hard thinking, eliminates legacy
- Cons: Time-intensive

### Rolling Forecast (Replace annual budget với 12-month rolling forecast)
- Pros: Always 12 months forward, more relevant
- Cons: Less anchored to strategic plan

### Recommended SMB approach
- Annual budget set at year start (top-down + bottom-up hybrid)
- Quarterly re-forecast (update remaining quarters)
- Monthly variance tracking

---

## 🚨 RED FLAGS REQUIRING IMMEDIATE ACTION

1. **Revenue trending >15% below budget by Q2**
   - Re-baseline forecast
   - Cost cutting plan needed
   - Hiring freeze candidate

2. **Operating expenses >20% over budget**
   - Approval threshold tightening
   - Department-by-department review
   - Identify discretionary cuts

3. **Multi-month negative trend**
   - Don't average over time — trend matters
   - Industry headwinds vs internal issues

4. **Cash burn higher than runway forecast**
   - Cash flow + variance + working capital review
   - May require fundraising acceleration (startup)

---

## ⚠️ COMMON ISSUES

1. **Comparing to wrong budget** — Mid-year reforecast vs original budget
2. **Seasonality not adjusted** — Pro-rata wrong if business is seasonal
3. **Capital vs Operating mixing** — Budget for OpEx, actual includes CapEx in same line
4. **Foreign currency variance** — Strip out FX before analyzing operating performance
5. **One-time items dilute** — Separate "underlying" from "reported" variance
6. **Department budgets don't sum to company budget** — Reconciliation needed
7. **Stale budget** — Budget set 6 months ago, market changed dramatically
8. **No accountability** — Owners not assigned per line item

---

## 💡 BEST PRACTICES

1. **Set budget by Dec 1** for following calendar year
2. **Lock budget by Dec 31** (no mid-year revisions to original)
3. **Monthly reforecast** updates expected full-year
4. **Quarterly board review** of variances
5. **Tie compensation to budget achievement** (with reasonable thresholds)
6. **Document budget assumptions** (volume, price, hires, etc.)
7. **Build in contingency** (5-10% reserve for unforeseen)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
