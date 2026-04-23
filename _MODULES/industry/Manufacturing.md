# Manufacturing Industry — Industry Module

> **Module này được include khi `config.company.industry == "Manufacturing"`.**

**Industry:** Manufacturing (job shop, batch, continuous, contract manufacturing)
**COA Template:** [COA_Manufacturing.csv](../../_TEMPLATES/COA/COA_Manufacturing.csv) (~80 accounts)
**Last Updated:** 2026-04-22

---

## TYPICAL BUSINESS PROFILE

- **Examples:** Custom job shops, contract manufacturers, batch producers, OEM, white-label producers
- **Revenue model:** Product sales (B2B common), custom orders, service contracts
- **Major costs:** Direct materials (40-60%) + Direct labor (15-25%) + Manufacturing overhead (15-25%)
- **Inventory complexity:** 3-tier (raw materials, WIP, finished goods)
- **Capital intensive:** Equipment, facility, tooling

---

## KEY METRICS & KPIs

### Profitability
- **Gross Margin** = (Revenue - COGS) / Revenue
  - Target: 25-40% (varies — high-mix low-volume higher, commodity lower)
- **Material Cost %** = Direct Materials / Revenue
  - Target: <40% (industry varies)
- **Labor Cost %** = Direct Labor / Revenue
  - Target: 15-25%
- **Overhead Rate** = Manufacturing Overhead / Direct Labor (or Machine Hours)
  - Used for cost allocation

### Operations
- **Throughput** = Units produced per period
- **Cycle Time** = Time to complete one unit
- **First-Pass Yield** = (Good Units First Time) / Total Units Started
  - Target: >95%
- **OEE (Overall Equipment Effectiveness)** = Availability × Performance × Quality
  - World-class: 85%+
  - Good: 70-85%
- **Capacity Utilization** = Actual Output / Capacity
  - Target: 80-95% for healthy operations

### Inventory
- **Inventory Turnover** (Total) = COGS / Avg Total Inventory
  - Target: 4-8x annually (job shop), 12+ (lean manufacturing)
- **Days Inventory Outstanding** = (Avg Inventory / COGS) × 365
- **Raw Materials Turnover** — separate metric
- **WIP Days** — minimize (cash trapped)
- **Finished Goods Days** — balance against customer service level

### Quality
- **Scrap Rate** = Scrap Cost / Total Material Cost
- **Rework Rate** = Rework Hours / Total Production Hours
- **Customer Returns Rate** = Returns / Shipments

---

## GAAP NUANCES

### Revenue Recognition (ASC 606)
- **Standard products:** Recognize at delivery (transfer of control)
- **Custom orders / long-term contracts:** Use % completion method (input or output basis)
  - Cost-to-cost method most common
  - Recognize: (Cost incurred / Total estimated cost) × Total contract value
- **Bill-and-hold arrangements:** Strict criteria — customer must request, item set aside, ready to ship
- **Service contracts:** Ratable over service period

### Inventory Valuation
- **3-tier inventory:** Raw Materials → WIP → Finished Goods
- **Cost methods:** FIFO (most common), Standard Cost (with variance accounts), Weighted Average
- **Absorption costing required by GAAP** — must include direct material + direct labor + allocated overhead in inventory cost
- **Direct costing (variable costing) NOT GAAP** — excludes fixed overhead from inventory (used internally only)

### Manufacturing Overhead Allocation
**Critical concept:** Overhead must be allocated to inventory units based on rational, systematic basis:
- **Direct labor hours** (most common for labor-intensive)
- **Machine hours** (capital-intensive)
- **Direct labor cost** (small operations)
- **Activity-based costing (ABC)** for complex operations

### Common Mistakes
- Not allocating overhead to WIP/Finished Goods (understates inventory + overstates COGS)
- Using direct costing for external reporting (GAAP violation)
- Not capturing tooling costs into inventory
- Booking R&D as COGS (should be separate OpEx)
- Inventory write-downs not taken timely (LCNRV requires reduction when market value < cost)
- Section 263A (UNICAP) not applied for businesses >$29M revenue

---

## CHART OF ACCOUNTS HIGHLIGHTS

### Inventory (1200s) — 3-tier critical
- 1200 — Raw Materials
- 1210 — Work in Process (WIP)
- 1220 — Finished Goods
- 1230 — Spare Parts/MRO (Maintenance, Repair, Operating)

### COGS (5000s) — split direct vs overhead
- 5010 — Direct Materials
- 5020 — Direct Labor
- 5030 — Manufacturing Overhead Applied
- 5040 — Subcontractor Services
- 5050 — Freight In

### Manufacturing Overhead (5100s) — separately tracked
- 5100 — Indirect Materials
- 5110 — Indirect Labor (supervisor, QC, maintenance)
- 5120 — Factory Rent
- 5130 — Factory Utilities
- 5140 — Equipment Depreciation (production equipment)
- 5150 — Maintenance

→ Overhead accounts feed into "5030 Manufacturing Overhead Applied" via standard rate.

### R&D (6320)
**Separate from COGS:**
- 6320 — Research and Development (eligible for R&D Tax Credit)

### Insurance (specific to manufacturing)
- 6720 — Product Liability (CRITICAL — products you make can hurt people)
- 6730 — Property (high values for facility + equipment)
- 6740 — Cargo/Transit

---

## SETUP CHECKLIST FOR NEW MANUFACTURING BUSINESS

- [ ] Facility lease + zoning compliance (industrial zoning)
- [ ] OSHA compliance (workplace safety)
- [ ] EPA permits (environmental — depending on processes)
- [ ] Equipment financing structure (lease vs buy decision)
- [ ] ERP/MRP system selection (NetSuite/SAP/Microsoft Dynamics for small/mid)
- [ ] Inventory management workflow (barcoding, cycle counts)
- [ ] BOM (Bill of Materials) for each product
- [ ] Routing (production process steps) documented
- [ ] Standard costs established
- [ ] Variance analysis process (price, usage, efficiency)
- [ ] Quality management system (ISO 9001 if needed for customers)
- [ ] Workers' Comp (high rate — manufacturing among highest classes)
- [ ] Product Liability insurance (per occurrence + aggregate limits)
- [ ] Property insurance (replacement cost, including business interruption)
- [ ] Vendor agreements (lead times, MOQ, payment terms)
- [ ] Customer agreements (terms, warranties, returns)

---

## COMMON ISSUES & FLAGS

| Issue | Risk | Mitigation |
|-------|------|------------|
| Inventory not counted regularly | Material variances + financial misstatement | Cycle counts (ABC analysis: A items weekly, B monthly, C quarterly) |
| Overhead allocation wrong basis | Wrong product profitability | Activity-based costing or labor/machine hours |
| WIP not properly costed | Year-end inventory swing | Track WIP daily through ERP/MRP |
| Section 263A (UNICAP) not applied | Tax compliance issue (>$29M businesses) | Capitalize indirect costs into inventory for tax |
| Tooling costs expensed | Should be capitalized | If useful life >1 year + significant cost, capitalize |
| Customer returns not estimated | Revenue overstatement | Establish return reserve based on history |
| Warranty obligations not accrued | Liability understatement | Estimate warranty cost % of sales, accrue at sale |
| Equipment maintenance neglected | Production downtime | Preventive maintenance schedule + budget |
| Vendor concentration (1 supplier >40% of materials) | Supply chain risk | Qualify backup suppliers |
| Customer concentration | Revenue cliff if lost | Diversify customer base |

---

## RECOMMENDED REPORTING CADENCE

- **Daily:** Production output vs plan, scrap rate, downtime
- **Weekly:** WIP aging, material usage variance, labor efficiency
- **Monthly:** P&L by product line, gross margin analysis, inventory variance, capacity utilization
- **Quarterly:** Vendor scorecards, customer profitability, OEE trends
- **Annually:** Standard cost re-set, capacity planning, capital expenditure plan

---

## TAX OPTIMIZATION (MANUFACTURING-SPECIFIC)

- **R&D Tax Credit (Section 41):** Federal + state credit for product development, process improvement, new tooling. **Often missed — average $50K+/year for SMB manufacturers.**
- **Section 179 expensing:** Up to $1.16M (2024) on equipment — bonus for production machinery
- **Bonus depreciation:** 60% (2024, phasing down) for qualified property
- **Section 263A (UNICAP):** Required >$29M revenue — capitalize more indirect costs into inventory
- **Domestic Production Activities Deduction (DPAD):** REPEALED — replaced by Section 199A 20% QBI deduction (pass-through only)
- **Work Opportunity Tax Credit:** Available for certain hires
- **Cost Segregation Study:** For owned facilities — accelerates depreciation (typically 5-10% of building cost)
- **Renewable Energy Credits:** Solar/efficient equipment may qualify
- **Foreign Tax Credit:** If exporting and paying foreign tax

---

## CONTRACT MANUFACTURING CONSIDERATIONS

If you manufacture for OTHER companies (vs your own brand):
- **Customer-supplied materials:** Don't include in your inventory (consigned materials)
- **Tooling owned by customer:** Track but don't depreciate (their asset)
- **Long-term contracts:** Use % completion method
- **NDAs and IP:** Structure agreements carefully

---

## EXPORT CONSIDERATIONS

If exporting:
- **IC-DISC (Interest Charge Domestic International Sales Corporation):** Tax savings on export sales (US benefit)
- **FTZ (Foreign Trade Zones):** Defer/reduce duties
- **Export documentation:** EEI, BL, COC, etc.
- **Currency hedging:** If invoicing in foreign currency

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
