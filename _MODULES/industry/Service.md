# Service Industry — Industry Module

> **Module này được include khi `config.company.industry == "Service"`.**

**Industry:** Professional / Personal / Consulting Services
**COA Template:** [COA_Service.csv](../../_TEMPLATES/COA/COA_Service.csv) (~60 accounts)
**Last Updated:** 2026-04-22

---

## TYPICAL BUSINESS PROFILE

- **Examples:** Consulting, marketing agencies, law firms, accounting firms, IT services, design agencies, professional services
- **Revenue model:** Hourly billing, project fees, retainers, value-based pricing
- **No inventory** (or minimal)
- **Direct costs:** Subcontractors, direct labor, project materials
- **Major expense:** Salaries (60-80% of revenue typical)

---

## KEY METRICS & KPIs

### Profitability
- **Gross Profit Margin** = (Revenue - COGS) / Revenue
  - Target: 50-70% (services typical)
- **Net Profit Margin** = Net Income / Revenue
  - Target: 10-20% mature, 5-10% growing

### Productivity
- **Utilization Rate** = Billable Hours / Total Hours
  - Target: 70-80% billable for client-facing staff
- **Realization Rate** = Billed Hours / Worked Hours
  - Target: >90%
- **Effective Hourly Rate** = Revenue / Total Billable Hours

### Customer
- **Average Project Value** = Revenue / # Projects
- **Customer Retention Rate** = (End Customers - New Customers) / Start Customers
  - Target: >85% annually
- **Days Sales Outstanding (DSO)** = AR / (Revenue / 365)
  - Target: <45 days

---

## GAAP NUANCES

### Revenue Recognition (ASC 606)
**Service contracts:**
- **Time and materials:** Recognize as services performed (typically monthly invoicing)
- **Fixed-fee projects:** Use % completion method (input-based via labor hours)
- **Retainers:** Recognize ratably over service period
- **Subscription/managed services:** Ratable monthly recognition

### Common Mistakes
- Recognizing fixed-fee revenue when invoiced (should be % completion)
- Not deferring upfront retainer payments
- Booking subcontractor costs to expense vs COGS

---

## CHART OF ACCOUNTS HIGHLIGHTS

### Revenue Lines (4000s)
Service businesses should split revenue by service type for management reporting:
- 4010 — Consulting
- 4020 — Project-Based
- 4030 — Subscription/Retainer
- 4040 — Hourly

→ Add custom sub-accounts as needed (vd: by department, by service line, by client tier)

### COGS (5000s)
Direct costs of service delivery:
- 5010 — Subcontractor Fees (1099 contractors directly billable)
- 5020 — Direct Materials
- 5030 — Direct Labor (NOT all wages — only if directly tracked to service delivery)

→ Most service firms simplify: only Subcontractor Fees in COGS, all internal labor in 6010 OpEx.

### Major Expense Categories
- **6010 Salaries and Wages** — usually largest expense
- **6310 Software Subscriptions** — growing rapidly (CRM/PM tools)
- **6500 Marketing** — critical for client acquisition
- **6600 Travel** — client meetings/conferences

---

## SETUP CHECKLIST FOR NEW SERVICE BUSINESS

- [ ] Establish billing model (hourly vs project vs retainer)
- [ ] Set up time tracking (Harvest/Toggl/Clockify integrated với invoicing)
- [ ] Implement engagement letter / SOW template
- [ ] Set up CRM (HubSpot/Salesforce/Pipedrive)
- [ ] Configure professional liability (E&O) insurance
- [ ] Establish payment terms (Net 15-30 typical)
- [ ] Set up retainer escrow if applicable
- [ ] Document subcontractor agreements (avoid IRS reclassification)
- [ ] Track utilization rate weekly

---

## COMMON ISSUES & FLAGS

| Issue | Risk | Mitigation |
|-------|------|------------|
| Owner taking $0 W-2 in S-Corp services firm | Reasonable comp violation | Set min W-2 = 30-50% of total comp |
| Misclassifying full-time contractors as 1099 | IRS reclassification + back wages | Apply ABC test (especially CA/MA/NJ) |
| Not invoicing monthly | Cash flow + DSO blow up | Automate invoicing in PM/billing tool |
| Booking all subcontractors as expense | COGS understatement → wrong margin | Subcontractors directly billable = COGS, not expense |
| Free work / scope creep | Margin erosion | Track unbilled time, charge change orders |
| Concentration risk (1 client >25% revenue) | Revenue cliff if lost | Diversify client base, use long-term contracts |

---

## RECOMMENDED REPORTING CADENCE

- **Weekly:** Time tracking + utilization rate
- **Bi-weekly:** AR aging + collections actions
- **Monthly:** P&L by service line, project profitability, gross margin
- **Quarterly:** Pipeline forecast, customer retention, revenue concentration
- **Annually:** Pricing review, margin trends, LTV by client segment

---

## TAX OPTIMIZATION (SERVICE-SPECIFIC)

- **Section 199A QBI Deduction:** 20% deduction on pass-through income — but Specified Service Trade or Business (SSTB) limitation applies for high-income owners (consulting, law, accounting, etc.)
- **R&D Tax Credit:** Available if developing proprietary methodology/software (often missed)
- **Home office deduction:** If no separate office (Section 280A — strict requirements)
- **Health insurance:** Self-employed deduction for owner-paid premiums (Schedule 1)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
