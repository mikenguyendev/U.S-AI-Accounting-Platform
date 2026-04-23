# 📈 Profit & Loss (Income Statement) Template — Setup Guide

> Monthly P&L với YTD + Prior Year + Budget comparisons.

**File:** `P&L.csv`
**Update cadence:** Monthly (post close)
**Storage:** `_INSTANCES/{instance_id}/06_Financial_Reporting/Profit_and_Loss/`

---

## 📋 STRUCTURE

P&L follows standard GAAP format:

```
Revenue
- COGS
= Gross Profit

- Operating Expenses
= Operating Income (EBIT)

+/- Other Income / Expense
= Income Before Taxes

- Tax Expense
= Net Income
```

Column structure:
- **Current Month** — This reporting period
- **YTD** — Year to date
- **Prior Year Same Period** — Comparison
- **Variance vs Prior** — Dollar change
- **Variance %** — Percentage change
- **Budget YTD** — Budget comparison
- **Variance vs Budget** — Performance vs plan

---

## 🔧 FORMULAS

### Pull from Trial Balance using SUMIFS
```excel
Current Month Revenue:
=SUMIFS(JE!F:F, JE!C:C, "4010", JE!B:B, ">="&MonthStart, JE!B:B, "<="&MonthEnd) -
 SUMIFS(JE!G:G, JE!C:C, "4010", JE!B:B, ">="&MonthStart, JE!B:B, "<="&MonthEnd)
```

Wait — revenue is a Credit-normal account, so:
```excel
=SUMIFS(JE!G:G, JE!C:C, "4010", ...) - SUMIFS(JE!F:F, JE!C:C, "4010", ...)
```

### YTD calculation
```excel
=SUMIFS(JE!G:G, JE!C:C, "4010", JE!B:B, ">="&FYStart, JE!B:B, "<="&TODAY())
  - SUMIFS(JE!F:F, JE!C:C, "4010", ...)
```

### Variance calculations
```excel
Variance $:  =D2-E2  (Current - Prior)
Variance %:  =IFERROR((D2-E2)/ABS(E2), 0)
```

### Gross Profit
```excel
=[Total Revenue] - [Total COGS]
```

### Gross Profit Margin
```excel
=IFERROR([Gross Profit] / [Total Revenue], 0)
```

### Operating Income (EBIT)
```excel
=[Gross Profit] - [Total Operating Expenses]
```

### Net Income
```excel
=[Operating Income] + [Other Income] - [Other Expense] - [Tax Expense]
```

### EBITDA (optional bottom section)
```excel
=[Net Income] + [Interest Expense] + [Taxes] + [Depreciation] + [Amortization]
```

---

## 🎨 CONDITIONAL FORMATTING

### Revenue growth/decline
- Variance vs Prior > 10% → Green (growth)
- Variance vs Prior < -10% → Red (decline)

### Budget variance flags
- Variance vs Budget > 10% unfavorable → Red highlight
- Variance vs Budget 5-10% unfavorable → Yellow highlight
- Favorable variance > 10% → Green highlight (also needs explanation)

### Margin alerts
- Gross Profit Margin < Target → Orange
- Net Profit Margin negative → Red bold

### Subtotal rows
- Revenue, COGS, Operating Expenses, Tax subtotals → Light blue fill
- Gross Profit, Operating Income, Net Income → Darker blue fill, white bold

---

## 📊 INDUSTRY BENCHMARKS

### Gross Profit Margin Targets
| Industry | Healthy Range |
|----------|---------------|
| Service | 50-70% |
| Retail | 25-50% |
| Restaurant | 65-72% (food cost % inverse) |
| Manufacturing | 25-40% |
| SaaS | 75-85% |

### Net Profit Margin Targets
| Industry | Healthy Range |
|----------|---------------|
| Service | 10-20% |
| Retail | 5-10% |
| Restaurant | 3-6% |
| Manufacturing | 5-10% |
| SaaS | -10% to +20% (investing for growth OK) |

---

## 🎯 REPORTING BEST PRACTICES

### Monthly package
1. **P&L** (this template)
2. **Balance Sheet** (next)
3. **Cash Flow** (quarterly minimum)
4. **1-page Executive Summary** — Key metrics + narrative
5. **Commentary** — Explain material variances
6. **KPI dashboard** — Industry-specific metrics

### Presentation order
1. Current Month (most focus)
2. YTD (trend context)
3. Prior Year comparison
4. Budget comparison
5. Key ratios

### Rounding
- Internal reports: To the dollar
- Board reports: To thousands
- Investor/external: To nearest thousand or million
- NEVER round to zero decimals if under $1K

---

## 📝 VARIANCE EXPLANATION FRAMEWORK

For each material variance (>10% or >$1K), explain:

**Price × Volume analysis:**
- Price variance: (Actual Price - Budget Price) × Actual Volume
- Volume variance: (Actual Volume - Budget Volume) × Budget Price

**One-time vs recurring:**
- One-time: legal settlement, equipment sale, severance
- Recurring: new hire, subscription change, pricing change

**Controllable vs non-controllable:**
- Controllable: marketing spend, travel, new hires
- Non-controllable: FX, commodity prices, regulatory changes

---

## ⚠️ COMMON ISSUES

1. **Revenue recognition timing** — ASC 606 compliance (deferred revenue)
2. **Classification errors** — Marketing vs Advertising vs Dues
3. **Matching principle** — Expense in period earned, not just paid
4. **Capitalization missed** — Equipment expensed instead of depreciated
5. **Accruals missed** — Payroll/utilities not accrued at period end
6. **Inter-period items** — Prepaid amortization timing
7. **Prior period adjustments** — Should be separate line, not buried in current
8. **Currency translation** — If multi-currency, use proper FX rates per GAAP

---

## 🎁 ADVANCED: WATERFALL CHART DATA PREP

For executive presentations, create waterfall showing NI drivers:

```
Row 1: Prior Year Net Income            [baseline]
Row 2: Revenue growth                   [positive]
Row 3: COGS increase                    [negative]
Row 4: Headcount expansion              [negative]
Row 5: New marketing program            [negative]
Row 6: Interest reduction               [positive]
Row 7: Tax optimization                 [positive]
Row 8: Current Year Net Income          [ending balance]
```

Insert Chart → Waterfall (Excel 2016+) or custom bar chart.

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
