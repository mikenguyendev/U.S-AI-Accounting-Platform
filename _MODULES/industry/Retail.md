# Retail Industry — Industry Module

> **Module này được include khi `config.company.industry == "Retail"`.**

**Industry:** Retail (brick-and-mortar, e-commerce, omnichannel)
**COA Template:** [COA_Retail.csv](../../_TEMPLATES/COA/COA_Retail.csv) (~75 accounts)
**Last Updated:** 2026-04-22

---

## TYPICAL BUSINESS PROFILE

- **Examples:** Specialty stores, e-commerce sellers, boutiques, multi-brand retailers, dropshippers
- **Revenue model:** Product sales (margin-based)
- **High inventory** (typically 30-50% of total assets)
- **Major direct cost:** COGS (60-75% of revenue typical)
- **Sales tax compliance** critical (multi-state nexus)

---

## KEY METRICS & KPIs

### Profitability
- **Gross Profit Margin** = (Revenue - COGS) / Revenue
  - Target: 25-50% (varies wildly by category — luxury 60%+, grocery 20-30%)
- **Net Profit Margin** = Net Income / Revenue
  - Target: 5-10% mature

### Inventory
- **Inventory Turnover** = COGS / Average Inventory
  - Target: 4-6x annually (specialty), 8-12x (fast-moving consumer goods)
- **Days Inventory Outstanding (DIO)** = (Avg Inventory / COGS) × 365
  - Target: 60-90 days (industry-dependent)
- **Sell-through Rate** = Units Sold / Units Received (per period)
  - Target: >70% by end of season

### Customer & Operations
- **Average Order Value (AOV)** = Revenue / # Orders
- **Conversion Rate** = Buyers / Visitors (e-commerce)
  - Target: 2-3% (industry varies)
- **Cart Abandonment Rate** (e-commerce)
  - Industry average: ~70%
- **Return Rate** = Returns / Sales
  - Target: <10% (apparel can hit 30%+)
- **Sales per Square Foot** (brick-and-mortar)

---

## GAAP NUANCES

### Revenue Recognition (ASC 606)
- **Point-of-sale** in-store: Recognize at time of sale
- **E-commerce:** Recognize when control transfers (typically at shipping for FOB shipping point)
- **Gift cards:** Defer until redeemed (Liability 2710)
- **Loyalty programs:** Defer portion attributed to future redemption (Liability 2720)
- **Sales returns:** Estimate return rate, accrue allowance

### Inventory Valuation
- **Cost methods:** FIFO (most common), LIFO (less common, IRS conformity rule), Average Cost, Specific Identification
- **Lower of Cost or Net Realizable Value (LCNRV)** — write down obsolete/damaged
- **Inclusion of carrying costs:** Freight in (5020) included in inventory cost; storage often expensed

### Common Mistakes
- Booking gift card sales as revenue immediately (should defer)
- Not accruing return allowance
- Inventory shrinkage discovered only at year-end (should be regular cycle counts)
- Mixing personal + business inventory

---

## CHART OF ACCOUNTS HIGHLIGHTS

### Revenue Lines (4000s)
Track by channel for multi-channel retailers:
- 4010 — Retail (in-store)
- 4020 — Online/E-commerce
- 4030 — Wholesale (B2B)
- 4040 — Gift cards redeemed
- 4050 — Shipping revenue (separate from product)

### COGS (5000s)
- 5010 — Cost of Goods Sold (primary)
- 5020 — Freight In (capitalize to inventory or expense based on policy)
- 5030 — Inventory Adjustments — Shrinkage (theft/damage)
- 5040 — Inventory Write-downs (obsolescence)
- 5050 — Shipping Costs Outbound (cost to ship to customer)

### Sales Tax Liability (2400s)
**Critical for retail:**
- 2410 — Sales Tax Payable — State
- 2420 — Sales Tax Payable — Local/County
→ Track per jurisdiction for multi-state nexus

### Other Specific Liabilities
- 2710 — Gift Cards Outstanding (HIGH visibility — unredeemed liability)
- 2720 — Loyalty/Rewards Liability

---

## SETUP CHECKLIST FOR NEW RETAIL BUSINESS

- [ ] Sales tax permits in ALL nexus states
- [ ] Inventory management system (Shopify/Lightspeed/Square + dedicated inventory tool)
- [ ] POS system integrated with accounting (Toast/Square/Shopify POS)
- [ ] Cycle counting schedule (monthly minimum, weekly for high-value)
- [ ] Vendor agreements with payment terms documented
- [ ] Returns/refund policy + accounting treatment defined
- [ ] Gift card terms (5-year expiration laws, escheatment rules)
- [ ] Loyalty program GAAP treatment determined
- [ ] Insurance: GL + property + crime/theft + cyber (e-commerce)
- [ ] Ecommerce platform fees tracked separately

---

## COMMON ISSUES & FLAGS

| Issue | Risk | Mitigation |
|-------|------|------------|
| Multi-state sales tax not collected | Audit assessment + back tax + penalty | Implement Avalara/TaxJar for automation |
| Marketplace facilitator confusion (Amazon/eBay) | Double-collecting or under-collecting | Marketplaces typically remit — verify per state |
| Gift cards on Balance Sheet not revenue | Revenue recognition error | Post Liability 2710 → recognize on redemption |
| Inventory carrying costs ignored | Hidden cost of slow inventory | Track storage + insurance + obsolescence allowance |
| Stockouts or overstock | Lost sales OR write-downs | ABC analysis + min/max thresholds |
| Theft/shrinkage 1.5%+ of sales | Major margin hit | Cycle counts + cameras + employee training |
| Returns not properly tracked | Revenue overstatement | Returns accrual at sale time |
| Vendor returns/credits not captured | COGS overstatement | Track in inventory adjustments |

---

## RECOMMENDED REPORTING CADENCE

- **Daily:** Sales by channel, cash reconciliation, top sellers
- **Weekly:** Inventory levels, sell-through, pending POs
- **Monthly:** P&L by channel, gross margin, inventory turns, AR aging, sales tax accrual
- **Quarterly:** Vendor scorecards, customer cohort analysis, ABC analysis
- **Annually:** Physical inventory count, obsolescence write-down, vendor terms renegotiation

---

## TAX OPTIMIZATION (RETAIL-SPECIFIC)

- **Inventory accounting election:** FIFO vs LIFO (LIFO can defer income in inflationary periods)
- **De minimis safe harbor:** Expense items <$2,500 (per invoice) instead of capitalizing
- **Section 263A (UNICAP):** Required for retailers with avg gross receipts >$29M (2024) — capitalize indirect costs into inventory
- **Bonus depreciation:** Special depreciation for fixed assets (POS equipment, fixtures)
- **R&D Credit:** Available for product development (private label brands)
- **Section 1231 gains:** Equipment sales = potentially capital gain treatment

---

## E-COMMERCE SPECIFIC

### Multi-state nexus
**Economic nexus** triggered by either threshold per state:
- $100K sales OR 200 transactions (most common — South Dakota v. Wayfair standard)
- Some states higher: TX $500K
- TRACK BY STATE — once nexus, must register + collect sales tax

### Marketplace Facilitator Laws
- Amazon, eBay, Etsy, Walmart Marketplace collect/remit sales tax for sellers in most states
- Seller still responsible for direct sales (own website)
- Track separately

### Platform fees
- Shopify: 1.5-2% transaction + monthly subscription
- Amazon: 8-15% referral fee + FBA fees
- eBay: 12-15% final value fee
- Etsy: 6.5% transaction + 3% payment processing

→ Categorize correctly: COGS (5050) for direct cost-of-sale fees; OpEx (6520) for platform subscription

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
