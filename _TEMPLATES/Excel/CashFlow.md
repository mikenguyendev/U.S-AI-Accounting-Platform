# 💵 Cash Flow Statement Template (Indirect Method) — Setup Guide

> Reconciles Net Income (accrual) to actual cash movement. Quarterly minimum.

**File:** `CashFlow.csv`
**Update cadence:** Quarterly minimum, monthly recommended
**Storage:** `_INSTANCES/{instance_id}/06_Financial_Reporting/Cash_Flow_Statement/`

---

## 📋 STRUCTURE

3 sections per GAAP:

1. **Operating Activities** — Day-to-day business cash flow
2. **Investing Activities** — CapEx and investments
3. **Financing Activities** — Debt, equity, distributions

```
Net Income
+ Adjustments (non-cash items)
+/- Working Capital Changes
= Cash from Operations

+/- Cash from Investing Activities
+/- Cash from Financing Activities

= Net Change in Cash
+ Beginning Cash
= Ending Cash (must match Balance Sheet)
```

---

## 🔧 INDIRECT METHOD CALCULATIONS

### Starting Point: Net Income from P&L
```excel
=P&L!NetIncome
```

### Add Back Non-Cash Items
- **Depreciation** (Account 6850) — Add full amount
- **Amortization** (Account 6860) — Add full amount
- **Stock-Based Compensation** (Account 6090 SaaS) — Add full amount
- **Bad Debt Expense** — Add full amount (provision)
- **(Gain)/Loss on Sale of Assets** — Reverse (move to Investing)

```excel
=Depreciation + Amortization + SBC + BadDebt - GainOnSale
```

### Working Capital Changes (CRITICAL CONCEPT)

**Increase in Asset = USE of cash (subtract)
Decrease in Asset = SOURCE of cash (add)
Increase in Liability = SOURCE of cash (add)
Decrease in Liability = USE of cash (subtract)**

```excel
Change in AR:           =-(CurrentAR - PriorAR)  [increase = use cash]
Change in Inventory:    =-(CurrentInv - PriorInv)
Change in Prepaid:      =-(CurrentPrepaid - PriorPrepaid)
Change in AP:           =+(CurrentAP - PriorAP)  [increase = source cash]
Change in Accrued:      =+(CurrentAccrued - PriorAccrued)
Change in Deferred Rev: =+(CurrentDR - PriorDR)
```

### Cash from Operations (CFO)
```excel
=NetIncome + Adjustments + WorkingCapitalChanges
```

### Cash from Investing (CFI)
```excel
=ProceedsFromSales - CapEx - Investments - Acquisitions
```

### Cash from Financing (CFF)
```excel
=ProceedsFromStock + ProceedsFromDebt - DebtRepayments - Distributions - StockBuyback
```

### Net Change in Cash
```excel
=CFO + CFI + CFF
```

### Ending Cash Reconciliation
```excel
=BeginningCash + NetChangeInCash
```
**MUST equal Balance Sheet Cash. Verify reconciliation.**

---

## 📊 INTERPRETATION

### Cash from Operations (CFO) — Health Indicator
- **Positive AND > Net Income:** Strong cash generation, working capital well-managed
- **Positive AND < Net Income:** OK, but watch working capital build-up
- **Negative:** RED FLAG — burning cash from core operations
  - SaaS exception: early-stage growth requires this; watch trajectory
  - Established business: serious problem

### Cash from Investing (CFI) — Growth Indicator
- **Negative:** Investing in future (CapEx, acquisitions) — typical for growing business
- **Positive:** Selling assets — could be strategic divestiture or distress

### Cash from Financing (CFF) — Capital Structure
- **Positive:** Raising capital (debt/equity) — growth or covering shortfall
- **Negative:** Returning capital (dividends/buybacks/debt paydown) — mature business

### Free Cash Flow (FCF) — Key Metric
```
FCF = CFO - CapEx
```
- **Positive:** Self-sustaining business
- **Negative:** Need external financing

---

## 🎨 CONDITIONAL FORMATTING

### Negative cash flow alerts
- CFO negative → Red bold (investigate)
- Net Change in Cash negative for multi-period → Track trajectory

### Working capital changes
- AR increase > 20% → Yellow (collection slowdown)
- Inventory increase > 20% → Yellow (slow-moving)
- AP increase > 20% → Yellow (paying slower OR pre-funding growth)

### Reconciliation check
- Ending Cash differs from BS Cash → RED bold "RECONCILE!"

---

## 📝 PREPARATION CHECKLIST

### Before generating CF:
- [ ] P&L finalized (Net Income locked)
- [ ] Balance Sheet finalized (current period)
- [ ] Prior period Balance Sheet available
- [ ] All depreciation/amortization posted
- [ ] CapEx ledger maintained (additions to Fixed Assets)
- [ ] Asset disposals documented
- [ ] Equity issuance/buybacks documented
- [ ] Loan transactions documented
- [ ] Stock-based comp accrued (if applicable)

---

## 🔍 RECONCILIATION TROUBLESHOOTING

### Ending Cash doesn't match Balance Sheet?
1. **Verify Beginning Cash = Prior Period BS Cash**
2. **Check working capital changes:**
   - All current asset changes captured?
   - All current liability changes captured?
3. **Check non-cash items:**
   - Depreciation full amount added back?
   - Stock comp added back?
4. **Check investing:**
   - All CapEx (look at Fixed Asset additions)?
   - Any disposals (look for Loss/Gain in P&L)?
5. **Check financing:**
   - Any new equity?
   - Any debt activity?
   - Distributions posted correctly?

### Common errors
- **Missing depreciation add-back** — Most frequent error
- **Forgetting Net Income to Retained Earnings flow** — Should already be in BS
- **Distribution timing** — Cash basis when paid, accrual basis when declared
- **Capital lease as financing** — Treat principal as financing outflow, interest as operating

---

## 🎯 QUARTERLY DEEP-DIVE TEMPLATE

For board reports, add narrative:

### Operating Activities Discussion
- Net Income trend
- Major working capital movements
- Cash conversion cycle changes
- Quality of earnings (CFO/Net Income ratio)

### Investing Activities Discussion
- CapEx vs Depreciation (replacement vs growth)
- Major projects in progress
- Future CapEx commitments

### Financing Activities Discussion
- Capital raises (round, valuation, dilution)
- Debt actions (new, refinanced, retired)
- Distributions to shareholders
- Stock buyback rationale

### Free Cash Flow trajectory
- Trailing 12-month FCF
- FCF margin (FCF / Revenue)
- Path to FCF positive (if startup)

---

## 💡 ALTERNATIVE: DIRECT METHOD

Direct Method shows actual cash receipts/payments (vs Indirect adjustments):

### Operating Section:
```
Cash received from customers
- Cash paid to suppliers
- Cash paid to employees
- Cash paid for operating expenses
- Cash paid for interest
- Cash paid for taxes
= Cash from Operations
```

**Why most use Indirect Method:**
- Easier to prepare (start from accrual P&L)
- GAAP allows both, prefers Indirect
- Indirect shows quality of earnings (NI vs CFO)

**When Direct Method useful:**
- Cash-basis businesses
- Investor presentations (more intuitive)
- Smaller businesses without complex accruals

---

## ⚠️ COMMON ISSUES

1. **Stock-based comp not added back** — Common SaaS error; significant amount
2. **Capitalized software dev not in CFI** — Cash spent should appear in Investing
3. **Acquired company assets/liabilities** — Working capital changes from acquisition need separate disclosure
4. **FX translation** — Multi-currency requires separate adjustment line
5. **Restricted cash** — Disclose separately if not freely usable
6. **Cash equivalents definition** — Maturity ≤90 days from purchase qualifies

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
