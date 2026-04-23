# Restaurant Industry — Industry Module

> **Module này được include khi `config.company.industry == "Restaurant"`.**

**Industry:** Food Service (FSR, QSR, fast-casual, café, bar, catering)
**COA Template:** [COA_Restaurant.csv](../../_TEMPLATES/COA/COA_Restaurant.csv) (~70 accounts)
**Last Updated:** 2026-04-22

---

## TYPICAL BUSINESS PROFILE

- **Examples:** Full-service restaurant (FSR), quick-service (QSR), fast-casual, café/coffee shop, bar/pub, catering
- **Revenue model:** Food + beverage sales (high volume, low margin)
- **Major costs:** Food cost (28-32%) + Labor (28-35%) — combined "Prime Cost" target <60%
- **Tipping complexity:** Tip pooling, FICA tip credit, IRS reporting

---

## KEY METRICS & KPIs

### Profitability (the BIG 4)
- **Food Cost %** = Food COGS / Food Sales
  - Target: 28-32% (FSR), 25-28% (QSR), 30-35% (fine dining)
- **Beverage Cost %** = Bev COGS / Bev Sales
  - Target: 18-22% (full bar), 15-18% (beer-wine only)
- **Labor Cost %** = Labor / Sales (including taxes + benefits)
  - Target: 28-32%
- **Prime Cost** = Food Cost + Beverage Cost + Labor
  - Target: 55-65% (industry standard)

### Operations
- **Cover Count** = # of guests served per day/week
- **Average Check** = Sales / Covers
- **Table Turn** = Covers / (Tables × Available Hours)
  - Target: 1.5-3 turns per service period
- **Sales per Square Foot**

### Inventory
- **Food Inventory Turnover** = Food COGS / Avg Food Inventory
  - Target: 25-50x annually (perishables turn fast)
- **Days Food on Hand** = (Food Inventory / Food COGS) × 365
  - Target: 7-14 days (perishables)
- **Beverage Inventory Turnover** — slower than food
  - Target: 8-15x annually

### Off-Premise
- **Takeout/Delivery %** = (Takeout + Delivery) / Total Sales
- **Delivery platform commission** — typically 15-30% (DoorDash/UberEats/GrubHub)

---

## GAAP NUANCES

### Revenue Recognition
- **Standard:** Recognize at point of sale (when food/drink delivered)
- **Gift cards:** Defer until redeemed
- **Catering deposits:** Defer until event delivered (Liability 2700)
- **Loyalty programs:** Defer portion attributed to future redemption

### Tip Accounting
**Critical area, often messed up:**
- **Server tips kept by server:** NOT employer revenue, NOT in P&L. Only payroll reporting (W-2 Box 7).
- **Pooled tips distributed to staff:** Pass-through. Liability 2220 (Tips Payable to Employees) when collected, settled when distributed.
- **Service charges (mandatory tips on large parties):** ARE employer revenue. Must report as wages to recipient (NOT tips).
- **FICA Tip Credit (Section 45B):** Employer credit for FICA on tip income above min wage portion. Reduce payroll tax expense.

### Inventory Valuation
- **Perishables:** Must be diligently counted weekly (food spoils fast)
- **Cost method:** Most use Weighted Average (food prices fluctuate)
- **Open bottles** at bar: count partial bottles for accuracy
- **Spoilage/waste:** Track separately (5070 + 5080)

### Common Mistakes
- Booking server tips as restaurant revenue (should pass through)
- Not tracking food vs beverage cost separately (one COGS line obscures issues)
- Skipping inventory counts (food cost spikes hidden)
- Not reporting service charges as wages (FLSA + IRS issue)
- Comp meals/staff meals booked to revenue then expense (should never hit revenue)

---

## CHART OF ACCOUNTS HIGHLIGHTS

### Revenue Lines (4000s) — granular split
- 4010 — Food (Dine-in)
- 4020 — Food (Takeout/Delivery)
- 4030 — Beverage (Non-Alcohol)
- 4040 — Beer
- 4050 — Wine
- 4060 — Spirits/Cocktails
- 4070 — Catering

→ Granular split lets you analyze margin by category. Combined "Sales" hides the story.

### Inventory (1200s) — split by category
- 1200 — Food
- 1210 — Beverage (Non-Alcohol)
- 1220 — Beer
- 1230 — Wine
- 1240 — Spirits

### COGS (5000s) — match revenue split
- 5010 — Food Cost
- 5020 — Beverage Cost (Non-Alcohol)
- 5030 — Beer Cost
- 5040 — Wine Cost
- 5050 — Spirits Cost

### Tips Liability (2220)
**Pooled tips:** Liability when collected, debit when distributed.

---

## SETUP CHECKLIST FOR NEW RESTAURANT

- [ ] Liquor license (state + local — can take 6-12 months)
- [ ] Health Department permit + inspection passed
- [ ] Food handler certifications for managers (state-specific)
- [ ] POS system integrated với accounting (Toast/Square/Lightspeed Restaurant)
- [ ] Inventory management (BlueCart/MarketMan/MarginEdge)
- [ ] Tip pooling policy in writing (legal review!)
- [ ] FICA Tip Credit tracking enabled in payroll
- [ ] Workers' Comp (high rate for restaurants — 4-8% of payroll)
- [ ] Liquor Liability insurance (Dram Shop)
- [ ] Property + general liability + cyber insurance
- [ ] Pest control contract (mandatory for health code)
- [ ] Grease trap cleaning schedule
- [ ] Daily cash reconciliation procedure (high theft risk)
- [ ] Vendor terms (food typically Net 7-15, alcohol typically COD or Net 7)

---

## COMMON ISSUES & FLAGS

| Issue | Risk | Mitigation |
|-------|------|------------|
| Food cost % >35% consistently | Margin death spiral | Cycle counts, recipe costing, portion control, vendor renegotiation |
| Labor cost % >35% | Prime cost over 60% | Schedule optimization, cross-training, auto-scheduling tools |
| Tips not reported correctly to IRS | Section 6053 violation, audit | Use POS tip allocation, file Form 8027 if applicable |
| Service charges treated as tips | Wage/hour + FICA issues | Automatic gratuity = wages (not tips) |
| Skipping daily cash reconciliation | Cash theft + skim | End-of-day Z-tape vs deposit reconciliation |
| Waste/spoilage not tracked | Hidden food cost issues | Separate accounts (5070 waste, 5080 spoilage) |
| Cash payments to staff | Wage/hour violations + tax evasion | All payments via payroll |
| Free meals not tracked | Comp inflates revenue | Comp register + waste/spoilage tracking |
| Workers' Comp lapse | Mandatory + criminal liability | Verify coverage monthly |
| Liquor license lapse | Forced closure | Calendar reminder 90 days before renewal |

---

## RECOMMENDED REPORTING CADENCE

- **Daily:** Sales (by category), labor hours vs sales, cash reconciliation, food cost % (trailing 7-day)
- **Weekly:** Prime cost (food + bev + labor), inventory variance, AR catering, void/comp report
- **Bi-weekly:** Payroll review, tip allocation report
- **Monthly:** P&L by category, profit per cover, vendor scorecard
- **Quarterly:** Menu engineering analysis (% sold × margin), price optimization
- **Annually:** Liquor license renewal, health permits, equipment maintenance plan

---

## TAX OPTIMIZATION (RESTAURANT-SPECIFIC)

- **FICA Tip Credit (Section 45B):** Federal credit for employer FICA paid on tip income above wages — significant savings (often $5-20K/year for full-service)
- **Section 179 expensing:** Up to $1.16M (2024) on equipment — kitchen + POS equipment qualifies
- **Bonus depreciation:** 60% (2024, phasing down) for qualified property
- **Work Opportunity Tax Credit (WOTC):** Hiring credit for certain employees (veterans, long-term unemployed)
- **Empowerment Zone hiring credits:** If located in qualifying zone
- **R&D Credit:** Some restaurants qualify for menu/recipe development

---

## OFF-PREMISE / DELIVERY CONSIDERATIONS

### Third-party delivery platforms
**Track separately:** DoorDash/UberEats/GrubHub commissions are 15-30% — major margin hit.

GAAP treatment options:
- **Net method:** Record net amount received from platform as revenue (most common)
- **Gross method:** Record full menu price as revenue, commission as COGS

→ Choose one method, apply consistently. AICPA tends toward gross method for "controlling agent" transactions.

### Ghost kitchens / virtual brands
- Separate revenue tracking per virtual brand
- Allocate shared kitchen overhead by sales mix
- Watch for menu cannibalization

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
