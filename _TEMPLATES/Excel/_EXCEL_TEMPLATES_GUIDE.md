# 📊 EXCEL TEMPLATES LIBRARY — Setup Guide

> **Mục đích:** Bộ 10 templates cho monthly close + ad-hoc reporting. Cung cấp dưới dạng CSV (data structure) + MD (formulas + instructions). Open trong Excel/Google Sheets, apply formulas per instructions, save as `.xlsx`.

**Version:** 1.0.0
**Last Updated:** 2026-04-23
**Compatibility:** Excel 2019+, Google Sheets, LibreOffice Calc, Numbers (Mac)

---

## 📋 TEMPLATE INDEX

| # | Template | CSV File | Setup Guide | Phase |
|---|----------|----------|-------------|-------|
| 1 | Journal Entry | `JournalEntry.csv` | `JournalEntry.md` | Daily |
| 2 | Trial Balance | `TrialBalance.csv` | `TrialBalance.md` | Monthly |
| 3 | Bank Reconciliation | `BankReconciliation.csv` | `BankReconciliation.md` | Monthly |
| 4 | AR Aging | `AR_Aging.csv` | `AR_Aging.md` | Weekly |
| 5 | AP Aging | `AP_Aging.csv` | `AP_Aging.md` | Weekly |
| 6 | P&L (Income Statement) | `P&L.csv` | `P&L.md` | Monthly |
| 7 | Balance Sheet | `BalanceSheet.csv` | `BalanceSheet.md` | Monthly |
| 8 | Cash Flow (Indirect) | `CashFlow.csv` | `CashFlow.md` | Quarterly |
| 9 | Payroll Register | `PayrollRegister.csv` | `PayrollRegister.md` | Per pay period |
| 10 | Budget vs Actual | `BudgetVsActual.csv` | `BudgetVsActual.md` | Monthly |

---

## 🚀 QUICK START

### Step 1: Open template in Excel/Sheets
```bash
# Open CSV
open _TEMPLATES/Excel/JournalEntry.csv

# OR import to Google Sheets:
# File → Import → Upload → JournalEntry.csv
```

### Step 2: Read companion MD
Each `.md` file contains:
- Structure overview
- Formulas to add (with cell references)
- Conditional formatting rules
- Validation rules
- Sample data
- Common pitfalls

### Step 3: Save as .xlsx
File → Save As → Excel Workbook (.xlsx)

### Step 4: Copy to instance folder
```bash
cp JournalEntry.xlsx _INSTANCES/{instance_id}/02_General_Ledger/Journal_Entries/FY2026_Q2/JE_template.xlsx
```

---

## 🎨 STYLING CONVENTIONS

### Color Palette (recommended)
- **Header rows:** `#1F4E79` background, white text, bold
- **Subtotals:** `#D9E1F2` background, bold
- **Totals:** `#1F4E79` background, white text, bold
- **Negative numbers:** Red text với parentheses `(1,234.56)`
- **Conditional warnings:** `#FFC7CE` background, dark red text
- **Conditional good:** `#C6EFCE` background, dark green text

### Number Formats
- **Currency:** `$#,##0.00;($#,##0.00)` — red negatives in parens
- **Percentages:** `0.00%`
- **Dates:** `mm/dd/yyyy` (US standard) or `yyyy-mm-dd` (ISO)
- **Account numbers:** Text format (preserve leading zeros)

### Print Settings
- Page Setup: Letter (8.5×11) portrait or landscape based on width
- Margins: 0.5" all sides
- Print Area: Set explicitly to data range
- Repeat header rows on every page
- Footer: filename + sheet name + date + page #

---

## 🔧 COMMON FORMULAS REFERENCE

### Auto-balance check (JE)
```excel
=IF(SUM(D:D)=SUM(E:E),"BALANCED","OUT OF BALANCE BY "&TEXT(SUM(D:D)-SUM(E:E),"$#,##0.00"))
```

### SUMIFS for category totals (P&L, BS)
```excel
=SUMIFS(GeneralLedger!Amount, GeneralLedger!Account, "4010", GeneralLedger!Date, ">="&StartDate, GeneralLedger!Date, "<="&EndDate)
```

### Aging bucket formula
```excel
=IF(DaysOverdue<=30,"Current",IF(DaysOverdue<=60,"31-60",IF(DaysOverdue<=90,"61-90","90+")))
```

### Variance calculation
```excel
Variance = Actual - Budget
Variance% = IFERROR((Actual-Budget)/Budget, 0)
```

### Balance Sheet validation
```excel
=IF(TotalAssets=TotalLiabilities+TotalEquity,"BALANCED ✓","NOT BALANCED — DIFF: "&TEXT(TotalAssets-(TotalLiabilities+TotalEquity),"$#,##0.00"))
```

---

## ⚠️ COMMON PITFALLS

1. **Forgetting to update date ranges** — Build with named ranges (e.g., `StartDate`, `EndDate`)
2. **Hardcoded values instead of formulas** — Always link to source data
3. **No data validation** — Use Data Validation rules to prevent garbage input
4. **Manual subtotals** — Use SUMIFS / SUBTOTAL formulas
5. **Mixed account number formats** — Standardize as text với leading zeros
6. **No audit trail** — Add "Last Updated" + "By" cells, freeze
7. **Sharing without protection** — Lock formula cells, allow input cells only
8. **Compatibility issues** — Avoid Excel-specific features (XLOOKUP if Sheets compat needed)

---

## 🤖 AI AGENT WORKFLOW

When user says "Generate journal entry", AI Agent should:

1. Read `_INSTANCES/{instance_id}/_BUSINESS_CONFIG.json` for context
2. Open template in instance folder (or copy from `_TEMPLATES/Excel/`)
3. Validate per template MD rules
4. Add row(s) with current data
5. Update Trial Balance reference
6. Save với date-stamped filename: `YYYYMMDD_JE-XXX_Description.xlsx`
7. Report to user with reference number

---

## 📦 INTEGRATION WITH ACCOUNTING SOFTWARE

These CSV templates designed to be importable to:

### QuickBooks Online
- COA import: direct CSV → Sales/Expense/Asset accounts
- JE import: requires xlsx with QBO-specific format (use Transactions Pro Importer)
- See `_QBO_MAPPING.csv` for account type translation

### Xero
- COA import: direct CSV
- JE import: through manual or Xero API
- Bank Reconciliation: through Xero's bank feed (different workflow)

### Google Sheets / Excel-only workflow
- Direct usage as primary ledger (small businesses)
- Run formulas natively, export to PDF for sharing
- Backup to Google Drive / OneDrive

### Sage / NetSuite
- COA: import via standard format
- JE: typically through native UI or API

---

## 🔄 UPDATE CADENCE

| Template | Update Cadence | Triggered By |
|----------|----------------|--------------|
| JE | Per transaction | Each posting event |
| Trial Balance | Daily during close | Pulled from GL |
| Bank Reconciliation | Monthly | Bank statement received |
| AR/AP Aging | Weekly | Cash collection cycle |
| P&L | Monthly | Month-end close |
| Balance Sheet | Monthly | Month-end close |
| Cash Flow | Quarterly | Quarter-end close |
| Payroll Register | Per pay period | Payroll run |
| Budget vs Actual | Monthly | After P&L finalized |

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
