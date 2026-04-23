# 📚 Excel Templates — Master Index

> Master reference cho 10 Excel templates trong library. Use as workbook navigator.

**Version:** 1.0.0
**Last Updated:** 2026-04-23

---

## 🗂️ TEMPLATE CATALOG

### Daily / Per-Transaction
| # | Template | Frequency | Purpose |
|---|----------|-----------|---------|
| 01 | [Journal Entry](JournalEntry.csv) | Per transaction | Foundation of all accounting; auto-balance check |
| 09 | [Payroll Register](PayrollRegister.csv) | Per pay period | Employee paychecks + employer tax calculation |

### Weekly Operations
| # | Template | Frequency | Purpose |
|---|----------|-----------|---------|
| 04 | [AR Aging](AR_Aging.csv) | Weekly | Customer collections priority |
| 05 | [AP Aging](AP_Aging.csv) | Weekly | Vendor payment scheduling + cash planning |

### Monthly Close Cycle
| # | Template | Frequency | Purpose |
|---|----------|-----------|---------|
| 02 | [Trial Balance](TrialBalance.csv) | Monthly | Verify all accounts balance |
| 03 | [Bank Reconciliation](BankReconciliation.csv) | Monthly | Reconcile bank to GL |
| 06 | [Profit & Loss](P&L.csv) | Monthly | Income Statement |
| 07 | [Balance Sheet](BalanceSheet.csv) | Monthly | Position snapshot |
| 10 | [Budget vs Actual](BudgetVsActual.csv) | Monthly | Variance analysis |

### Quarterly / Annual
| # | Template | Frequency | Purpose |
|---|----------|-----------|---------|
| 08 | [Cash Flow Statement](CashFlow.csv) | Quarterly minimum | Indirect method cash reconciliation |

---

## 🔄 DEPENDENCY DIAGRAM

```
Daily Transactions
  │
  ├─→ JE (01) ──→ Trial Balance (02)
  │                    │
  │                    ├─→ P&L (06) ─────────┐
  │                    │                      │
  │                    └─→ Balance Sheet (07)─┴─→ Cash Flow (08)
  │
  ├─→ AR (04) ───┐
  ├─→ AP (05) ───┤
  └─→ Payroll (09)→  All flow into JE → Trial Balance
                                              │
                                              └─→ Budget vs Actual (10)
                                                  vs Annual Budget
```

---

## 📅 MONTH-END CLOSE WORKFLOW (Day-by-Day)

### Day 1-3: Pre-Close Cleanup
- Post all remaining transactions for prior month
- Receive bank statements
- Send invoices to customers (any remaining for the month)
- Receive vendor invoices (cutoff check)

**Templates used:** 01 JE, 04 AR, 05 AP, 09 Payroll

### Day 4-5: Bank Reconciliation
- Reconcile each bank account
- Post adjusting JEs (interest, fees)

**Templates used:** 03 Bank Recon, 01 JE

### Day 5-7: Adjusting Entries
- Accrue salaries earned but not paid
- Amortize prepaid expenses
- Post depreciation
- Recognize deferred revenue per ASC 606
- Estimate bad debt allowance
- Inventory adjustments

**Templates used:** 01 JE

### Day 7-8: Trial Balance Review
- Generate TB from all JEs
- Verify balanced (Dr = Cr)
- Investigate material changes from prior month
- Controller sign-off

**Templates used:** 02 Trial Balance

### Day 8-10: Financial Statements
- Generate P&L
- Generate Balance Sheet
- Verify BS balances
- Generate Cash Flow (if quarter-end)

**Templates used:** 06 P&L, 07 Balance Sheet, 08 Cash Flow

### Day 10: Variance Analysis + Reporting
- Compare to Budget
- Document material variances
- Generate executive summary
- Distribute to stakeholders

**Templates used:** 10 Budget vs Actual

### Day 10-15: Lock + Distribute
- Lock period in accounting system
- Distribute monthly reporting package
- File documents in instance folder

---

## 🎯 SETUP CHECKLIST FOR NEW INSTANCE

When onboarding a new business instance:

### Step 1: COA setup
- [ ] Pick industry COA template (Service/Retail/Restaurant/Manufacturing/SaaS)
- [ ] Copy `_TEMPLATES/COA/COA_{industry}.csv` to `_INSTANCES/{instance_id}/02_General_Ledger/Chart_of_Accounts/`
- [ ] Customize accounts (rename Cash account để include bank name etc.)

### Step 2: Opening Balance
- [ ] Create Opening Trial Balance
- [ ] Post initial capital JE
- [ ] Verify TB balanced

### Step 3: Excel templates copy
- [ ] Copy all 10 templates to instance folder structure
- [ ] Customize header cells (company name, fiscal year, etc.)

### Step 4: Connect to data sources
- [ ] Bank feeds (if using QuickBooks/Xero)
- [ ] Payroll provider integration (Gusto/ADP)
- [ ] POS integration (retail/restaurant)

### Step 5: Establish cadence
- [ ] Daily: JE entries, time tracking (services), POS reconciliation (retail/rest)
- [ ] Weekly: AR/AP aging review
- [ ] Bi-weekly: Payroll runs
- [ ] Monthly: Close cycle (per workflow above)
- [ ] Quarterly: Tax filings + Cash Flow Statement
- [ ] Annual: 1099/W-2, tax return, audit prep

---

## 🔐 ACCESS CONTROL RECOMMENDATIONS

| Template | Owner | Edit | View Only |
|----------|-------|------|-----------|
| JE | Bookkeeper / Controller | Bookkeeper | All managers |
| Trial Balance | Controller | Controller | CFO, CEO |
| Bank Reconciliation | Bookkeeper | Bookkeeper | Controller |
| AR/AP Aging | AR/AP clerk | AR/AP clerk | Sales, CFO |
| P&L | Controller | Controller | Department heads (their section), CFO, CEO, Board |
| Balance Sheet | Controller | Controller | CFO, CEO, Board |
| Cash Flow | Controller | Controller | CFO, CEO, Board, Investors |
| Payroll | HR + Payroll Admin | Payroll Admin | NONE (PII) |
| Budget vs Actual | Controller | Controller | Department heads (their section), CFO, CEO, Board |

**File locking:** Lock formula cells, allow only input cells.

---

## 🛠️ INTEGRATION OPTIONS

### Pure Excel/Sheets (Manual)
- Templates as primary ledger
- All formulas calculated manually
- Backup to Drive/OneDrive
- **Best for:** 1-5 employees, simple operations
- **Limitations:** Single user, manual reconciliation, no audit trail

### Excel + QuickBooks Online
- QBO as primary system of record
- Templates for analysis/reporting only
- Pull data via QBO export
- **Best for:** 5-50 employees, growing complexity
- **Cost:** $30-200/month QBO + accountant fees

### Excel + Xero
- Similar to QBO
- More popular outside US
- Strong bank reconciliation features

### Excel + NetSuite (Enterprise)
- For larger SMB / mid-market
- Multi-entity, multi-currency
- Custom reporting via Saved Searches
- **Cost:** $1K+/month

### Excel + Sage (SMB ERP)
- Manufacturing focus
- Good for product businesses
- Strong inventory management

---

## 📊 OUTPUT FORMATS

These templates designed to support:

### Internal Reporting
- Monthly P&L + BS package (PDF)
- Weekly cash flow forecast (Excel)
- Daily KPI dashboard (chart)

### External Reporting
- Investor update (1-page summary + detailed financials)
- Board package (1-page exec summary + 3-statements + KPIs)
- Bank reporting (BS + P&L + Cash Flow per loan covenants)
- Tax preparation (TB + supporting schedules to CPA)

### Compliance Reporting
- 941 quarterly (from Payroll Register)
- 1099-NEC annual (from AP Aging — tracked vendors)
- W-2 annual (from Payroll Register YTD)
- Sales tax filings (from POS/JE data)

---

## ⚠️ LIMITATIONS OF CSV FORMAT

CSV files don't support:
- ❌ Cell formulas (need to add manually after import)
- ❌ Cell formatting (colors, borders, fonts)
- ❌ Multiple sheets per file
- ❌ Macros / VBA
- ❌ Charts
- ❌ Conditional formatting
- ❌ Data validation rules
- ❌ Pivot tables

**Workflow:**
1. Open CSV in Excel/Sheets
2. Apply formulas per companion `.md` file
3. Apply conditional formatting per `.md` guide
4. Save As `.xlsx` (Excel format)
5. Now full feature set available

**Alternative for full automation:**
- Use AI Agent to populate templates with data
- Use accounting software (QBO/Xero) for live formula execution
- Build custom dashboards in Looker Studio / Power BI

---

## 🔄 VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-04-23 | Initial release with 10 templates + index |

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
