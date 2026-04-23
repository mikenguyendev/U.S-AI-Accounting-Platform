# SaaS Industry — Industry Module

> **Module này được include khi `config.company.industry == "SaaS"`.**

**Industry:** Software-as-a-Service (B2B SaaS, B2C SaaS, vertical SaaS, PLG)
**COA Template:** [COA_SaaS.csv](../../_TEMPLATES/COA/COA_SaaS.csv) (~65 accounts)
**Last Updated:** 2026-04-22

---

## TYPICAL BUSINESS PROFILE

- **Examples:** B2B SaaS (CRM, ERP, productivity), B2C SaaS (consumer apps), vertical SaaS, marketplace SaaS, PLG companies
- **Revenue model:** Recurring subscription (ARR/MRR), often venture-backed
- **Major costs:** Engineering salaries (R&D), Sales/Marketing (CAC), Cloud hosting (COGS)
- **Long-term ratable revenue:** Deferred Revenue is huge (often largest liability)
- **Negative cash flow OK** in growth phase (focus on ARR + retention)

---

## KEY METRICS & KPIs (THE METRICS THAT MATTER)

### Revenue Metrics
- **MRR (Monthly Recurring Revenue)** = Sum of monthly subscription fees
- **ARR (Annual Recurring Revenue)** = MRR × 12
- **New MRR / New ARR** = New customer additions (per period)
- **Expansion MRR** = Upsells/upgrades from existing customers
- **Churn MRR** = Lost customers (revenue)
- **Net New MRR** = New + Expansion - Churn
- **NDR (Net Dollar Retention)** = (Beginning ARR + Expansion - Contraction - Churn) / Beginning ARR
  - World-class: >120%
  - Healthy: 100-120%
  - Concerning: <100%
- **GDR (Gross Dollar Retention)** = (Beginning ARR - Contraction - Churn) / Beginning ARR
  - Target: >90%

### Customer Metrics
- **CAC (Customer Acquisition Cost)** = Sales + Marketing / # New Customers
- **LTV (Customer Lifetime Value)** = (ARPU × Gross Margin) / Churn Rate
- **LTV/CAC Ratio** — industry standard
  - Target: >3x
  - World-class: >5x
- **Payback Period (CAC Payback)** = CAC / (Monthly ARPU × Gross Margin %)
  - Target: <12 months
  - World-class: <6 months
- **Logo Churn** = # Customers Lost / Total Customers (per period)
  - Target: <5% annually (B2B SaaS)
- **Revenue Churn** = MRR Lost / Total MRR
  - Target: <2% monthly = <22% annually

### Profitability (Rule of 40)
- **Rule of 40** = Growth Rate % + Profit Margin %
  - World-class: >40
  - Acceptable: 30-40
  - Concerning: <30
- **Magic Number** = (Net New ARR × 4) / Sales + Marketing Spend
  - >1.0 = invest more in S+M, <0.5 = pause/reassess

### Cost Structure
- **Gross Margin** = (Revenue - COGS) / Revenue
  - Target: 75-85% (B2B SaaS), 60-75% (with services)
- **R&D % of Revenue** = R&D / Revenue
  - Early-stage: 30-50%
  - Growth: 20-30%
  - Mature: 10-20%
- **Sales + Marketing % of Revenue** = S+M / Revenue
  - Early-stage: 50%+
  - Growth: 30-50%
  - Mature: 20-30%

---

## GAAP NUANCES

### Revenue Recognition (ASC 606) — CRITICAL FOR SAAS
**5-step framework:**
1. Identify the contract
2. Identify performance obligations
3. Determine transaction price
4. Allocate transaction price to obligations
5. Recognize revenue when obligation satisfied

**Subscription revenue recognition:**
- Annual subscription paid upfront → Defer Revenue (Liability), recognize 1/12 per month
- Monthly subscription → Recognize as billed (substantively same as ratable)
- Multi-year contracts → Defer based on service period

**Implementation/Setup fees:**
- If "distinct" service (customer can use independently) → recognize upfront
- If part of overall service → defer over contract term (most common)

**Common revenue rec mistakes:**
- Recognizing annual prepayment immediately (HUGE mistake — overstates revenue)
- Not deferring implementation fees
- Not capitalizing sales commissions per ASC 606-10-32-32

### ASC 340-40: Capitalized Sales Commissions
**Major change for SaaS (effective 2018):**
- Commissions on new customer contracts MUST be capitalized as asset (1300)
- Amortized over expected customer life (NOT contract length)
- Renewal commissions also capitalized (often shorter amortization period)

**Example:**
- Sales rep gets $10K commission on $50K annual subscription
- Customer expected to stay 4 years
- Amortize $10K / 4 = $2,500/year (NOT all in Year 1)

### ASC 985-20: Internal-Use Software
**Capitalize software development costs:**
- Pre-feasibility / Research: EXPENSE (R&D — 6010)
- Application Development: CAPITALIZE (1710 — Capitalized Software Development)
- Post-implementation/Operations: EXPENSE (R&D)

Amortize capitalized software over expected useful life (typically 3-5 years).

### Common Mistakes
- Recognizing all subscription revenue when invoiced → restated financials
- Not capitalizing material sales commissions → understates assets
- Capitalizing R&D before feasibility → overstates assets
- Mixing customer support (CoR) with general support (OpEx)
- Not amortizing capitalized software

---

## CHART OF ACCOUNTS HIGHLIGHTS

### Deferred Revenue (2700, 2710) — usually LARGEST liability
- 2700 — Deferred Revenue Current (annual subs paid upfront)
- 2710 — Deferred Revenue Long-term (multi-year)

→ Often >50% of total liabilities for healthy SaaS company.

### Capitalized Assets
- 1300 — Sales Commissions Asset (ASC 606)
- 1710 — Capitalized Software Development
- 1720 — Capitalized Software Amortization (contra)

### Revenue Lines (4000s) — split by recurring vs services
- 4010 — Subscription Revenue Annual
- 4020 — Subscription Revenue Monthly
- 4030 — Subscription Revenue Multi-Year
- 4040 — Usage-Based Revenue (consumption pricing)
- 4050 — Implementation/Onboarding Revenue
- 4060 — Professional Services Revenue
- 4070 — Add-on/Upsell Revenue

### COGS (5000s) — Cost of Revenue
- 5010 — Hosting Infrastructure (AWS/GCP/Azure production costs)
- 5020 — Third-Party APIs (Twilio/SendGrid/etc. passed through)
- 5030 — Customer Support team
- 5040 — Customer Success team (if direct cost)
- 5050 — Payment Processing fees
- 5060 — Implementation Labor
- 5070 — Software Amortization (capitalized)

→ Note: Cloud hosting for DEV/STAGING goes to 6310 (OpEx), NOT COGS.

### Equity (3000s) — VC-specific accounts
- 3020 — Preferred Stock — Series A/B/Seed
- 3040 — Stock-Based Compensation reserve

### Insurance (specific to SaaS)
- 6710 — D&O (Directors and Officers) — required by VCs
- 6720 — E&O / Tech Errors and Omissions
- 6730 — Cyber Liability — CRITICAL for SaaS
- 6820 — Compliance Costs (SOC 2/GDPR/HIPAA)

---

## SETUP CHECKLIST FOR NEW SAAS BUSINESS

- [ ] Subscription billing platform (Stripe Billing/Chargebee/Recurly)
- [ ] Revenue recognition platform (Stripe Revenue Recognition/Sage Intacct/SaaSOptics)
- [ ] CRM (HubSpot/Salesforce) integrated với billing
- [ ] Customer success platform (Gainsight/ChurnZero) for retention
- [ ] Cloud cost management (AWS Cost Explorer/Vantage/CloudHealth)
- [ ] Engineering management tools (Jira/Linear)
- [ ] Documentation: Privacy policy, ToS, DPA, SLA
- [ ] SOC 2 Type II preparation (within 12 months for B2B)
- [ ] D&O insurance (especially VC-backed)
- [ ] Cyber liability insurance (mandatory really)
- [ ] DE incorporation (most common for VC-backed)
- [ ] 83(b) elections for founder stock (within 30 days of grant — CRITICAL)
- [ ] Stock option plan (ISO + NSO)
- [ ] R&D tax credit study setup (often missed — significant savings)
- [ ] Multi-state nexus tracking (sales tax — Wayfair rules apply to SaaS in some states)

---

## COMMON ISSUES & FLAGS

| Issue | Risk | Mitigation |
|-------|------|------------|
| Recognizing annual revenue upfront | Material financial misstatement | Implement ASC 606 properly via revenue recognition platform |
| Not capitalizing sales commissions (ASC 606) | Understates assets, overstates expense | Track per-contract commission, amortize over customer life |
| Capitalizing all software dev | Overstates assets, audit risk | Apply ASC 985-20 stages — only Application Dev phase qualifies |
| Sales tax not collected on SaaS | Multi-state nexus issue (NY, TX, WA, MA tax SaaS) | Implement TaxJar/Avalara, monitor state laws |
| 83(b) election missed by founders | Founders pay tax on FMV at vest (huge bill) | File within 30 days of stock grant — calendar reminder |
| ISO disqualifying disposition | Loses preferential tax treatment | Educate option holders on holding periods |
| Negative gross margin | Cloud costs growing faster than revenue | Reserved instances, optimize architecture, monitor unit economics |
| High burn without ARR growth | Path to insolvency | Quarterly board review of CAC/LTV/burn multiple |
| MRR not reconciled to GAAP revenue | Investor reporting vs financial reporting mismatch | Reconciliation monthly: MRR-based ARR view vs GAAP P&L |
| Customer churn not tracked separately | Hides health metrics | Track logo churn + revenue churn + cohort analysis |
| Lack of compliance certifications | Lost B2B deals | SOC 2 Type II within 12-18 months |

---

## RECOMMENDED REPORTING CADENCE

- **Weekly:** New MRR + Churn MRR + Net New MRR, pipeline by stage
- **Monthly:** GAAP financials + SaaS metrics dashboard (MRR/ARR/CAC/LTV/NDR)
- **Quarterly:** Cohort retention analysis, CAC payback by channel, gross margin by product
- **Annually:** SOC 2 audit, R&D tax credit study, board strategy session

### Standard SaaS Metrics Dashboard
1. ARR (current vs trailing)
2. Net New ARR (last 6 months)
3. NDR (net dollar retention)
4. GDR (gross dollar retention)
5. Logo churn rate
6. CAC + LTV + LTV/CAC ratio
7. CAC Payback Period
8. Gross margin
9. R&D as % of revenue
10. Burn rate + runway

---

## TAX OPTIMIZATION (SAAS-SPECIFIC)

- **R&D Tax Credit (Section 41):** Federal + state — engineering salaries qualify. Often $50K-$500K/year savings. **MUST DO if R&D >$200K/year.**
- **Section 174 (Capitalize R&D):** Since 2022 — must capitalize R&D over 5 years (15 years foreign) — major change, increases taxable income. R&D Credit + 174 capitalization complex interplay.
- **ISO vs NSO:** Founders/employees: ISOs preferential, NSOs more flexible
- **83(b) Elections:** Within 30 days of stock grant — pay tax on FMV at grant (usually $0 early) instead of vest (potentially huge value)
- **QSBS (Qualified Small Business Stock — Section 1202):** If C-Corp, original stock held >5 years → up to $10M exclusion from capital gains tax (HUGE benefit for VC-backed)
- **State R&D credits:** Many states have additional R&D credits (CA, NY, MA, etc.)
- **DE Franchise Tax method:** Use Assumed Par Value method (NOT default Authorized Shares — can save $5K-$50K/year)
- **Foreign tax considerations:** If serving international customers, withholding/permanent establishment issues

---

## CAPITALIZED SOFTWARE — ACCOUNTING DEEP DIVE

### Section ASC 985-20 stages
**Pre-Feasibility (EXPENSE):**
- Research, conceptual design, alternatives evaluation
- All to R&D (6010)

**Application Development (CAPITALIZE):**
- Coding, testing, installation, configuration
- Direct labor + allocated overhead
- Capitalize to 1710

**Post-Implementation (EXPENSE):**
- Bug fixes, maintenance, training, data conversion
- Back to R&D (6010)

### Amortization
- Useful life: typically 3-5 years
- Method: Straight-line (most common)
- Begin amortizing when software ready for intended use
- Annual impairment review

### Common Errors
- Capitalizing too early (before feasibility decision)
- Capitalizing too late (missed development costs)
- Capitalizing maintenance/bug fixes (should be expense)
- Not amortizing once in use

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
