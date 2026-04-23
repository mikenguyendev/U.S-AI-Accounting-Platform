# 📐 CHART OF ACCOUNTS (COA) SCHEMA

> **Mục đích:** Định nghĩa structure chuẩn cho mọi COA template trong `_TEMPLATES/COA/`.
>
> **Format:** CSV (importable vào Excel, Google Sheets, QuickBooks Online, Xero, NetSuite).

**Version:** 1.0.0
**Last Updated:** 2026-04-22

---

## 📋 CSV COLUMN STRUCTURE

Tất cả COA files dùng cùng 6 columns:

| Column | Type | Required | Example |
|--------|------|:--------:|---------|
| `Account_Number` | String (4-5 digit) | ✅ | `1010` |
| `Account_Name` | String | ✅ | `Cash — Operating Checking` |
| `Account_Type` | Enum | ✅ | `Asset` |
| `Account_Subtype` | Enum | ✅ | `Current Asset` |
| `Tax_Line` | String | Optional | `Schedule L Line 1` |
| `Description` | String | Optional | `Primary business checking account` |

---

## 🔢 ACCOUNT NUMBERING CONVENTION

5-class US GAAP standard, QuickBooks-compatible:

| Range | Account_Type | Subtype Examples |
|-------|--------------|------------------|
| **1000–1999** | Asset | Current Assets (cash, AR, inventory, prepaid), Fixed Assets (PP&E), Other Assets |
| **2000–2999** | Liability | Current Liabilities (AP, accrued, payroll, taxes), Long-term Debt, Other |
| **3000–3999** | Equity | Common Stock, APIC, Retained Earnings, Owner's Equity, Distributions |
| **4000–4999** | Revenue | Service Revenue, Product Revenue, Subscription Revenue (by line) |
| **5000–5999** | COGS | Cost of Goods Sold, Cost of Services, Direct Labor, Direct Materials |
| **6000–6999** | Expense | Operating Expenses (SG&A) — categorize by function |
| **7000–7999** | Other | Other Income, Interest Income, Interest Expense, Tax Expense |

### Sub-numbering pattern (recommended)
- **X000–X099** = Header/parent accounts (rarely posted to)
- **X100–X199** = Sub-accounts grouped by function
- **X200–X299** = Next group
- ... etc

Example:
```
1000 = Cash (parent)
1010 = Cash — Operating
1020 = Cash — Savings
1030 = Cash — Payroll
1100 = Accounts Receivable (parent)
1110 = AR — Trade
1120 = AR — Allowance for Doubtful Accounts
```

---

## 📊 ACCOUNT_TYPE ENUM (Required)

| Value | Description |
|-------|-------------|
| `Asset` | Resources owned by the business (cash, AR, inventory, equipment) |
| `Liability` | Obligations owed (AP, loans, deferred revenue) |
| `Equity` | Owner's claim on assets (capital, retained earnings) |
| `Revenue` | Income from operations |
| `COGS` | Direct costs of goods/services sold |
| `Expense` | Operating expenses (SG&A) |
| `Other_Income` | Non-operating income (interest, gains) |
| `Other_Expense` | Non-operating expense (interest, taxes, losses) |

---

## 🏷️ ACCOUNT_SUBTYPE ENUM

### Assets (1000–1999)
- `Current Asset` (cash, AR, inventory, prepaid)
- `Fixed Asset` (PP&E)
- `Accumulated Depreciation`
- `Intangible Asset` (goodwill, patents)
- `Other Asset` (security deposits, long-term receivables)

### Liabilities (2000–2999)
- `Current Liability` (AP, accrued, short-term debt)
- `Long-term Liability` (notes >1 year, lease obligations)
- `Other Liability` (deferred revenue, contingent)

### Equity (3000–3999)
- `Common Stock`
- `Preferred Stock` (C-Corp only)
- `Additional Paid-in Capital`
- `Retained Earnings`
- `Owner's Equity` (sole prop, partnership)
- `Distributions` / `Dividends`

### Revenue (4000–4999)
- `Service Revenue`
- `Product Revenue`
- `Subscription Revenue`
- `Other Revenue`

### COGS (5000–5999)
- `Cost of Goods Sold`
- `Cost of Services`
- `Direct Labor`
- `Direct Materials`
- `Manufacturing Overhead`

### Expenses (6000–6999)
- `Salaries and Wages`
- `Rent`
- `Utilities`
- `Office Expense`
- `Professional Services`
- `Marketing`
- `Travel and Meals`
- `Insurance`
- `Depreciation`
- `Other Operating Expense`

### Other (7000–7999)
- `Interest Income`
- `Interest Expense`
- `Tax Expense`
- `Gain/Loss on Sale of Assets`

---

## 📦 TAX_LINE FIELD (Optional)

Maps account to a specific line on tax forms. Useful for tax prep automation.

Common references:
- `Schedule L Line 1` (Cash on Balance Sheet — corporate returns)
- `Form 1120 Line 11` (Cost of Goods Sold)
- `Schedule C Line 8` (Advertising — sole prop)
- `Form 1065 Line 9` (Salaries and Wages — partnership)

Format: `[Form] Line [N]` or `[Schedule] Line [N]`.

---

## 🏭 INDUSTRY-SPECIFIC PRESETS

### Available templates

| Industry | File | Account Count | Key Differentiators |
|----------|------|:-------------:|---------------------|
| Service | `COA_Service.csv` | ~60 | Revenue by service line, no inventory |
| Retail | `COA_Retail.csv` | ~75 | Inventory, Sales Tax Payable, COGS retail |
| Restaurant | `COA_Restaurant.csv` | ~70 | Food/Bev split, Tips Payable, daily sales |
| Manufacturing | `COA_Manufacturing.csv` | ~80 | WIP, Raw Materials, Finished Goods, Overhead |
| SaaS | `COA_SaaS.csv` | ~65 | Deferred Revenue, MRR tracking, CAC, R&D |

---

## 🔧 USAGE PROTOCOL

### Step 1: Pick industry template
Based on `config.company.industry` in business config.

### Step 2: Copy CSV to instance folder
```
cp _TEMPLATES/COA/COA_{industry}.csv _INSTANCES/{instance_id}/02_General_Ledger/Chart_of_Accounts/Chart_of_Accounts_FY{year}.csv
```

### Step 3: Customize for company
- Rename `Cash — Operating Checking` → `Cash — Chase Operating Checking ****1234`
- Add company-specific revenue lines
- Remove unused accounts (or mark inactive)
- Add industry sub-niche accounts

### Step 4: Convert to .xlsx (optional)
Open CSV in Excel/Sheets → Save As → `.xlsx`.
For QuickBooks Online: import directly (QBO accepts CSV).

### Step 5: Update business config
```json
{
  "chart_of_accounts": {
    "industry_template": "Service",
    "file_path": "02_General_Ledger/Chart_of_Accounts/Chart_of_Accounts_FY2026.xlsx",
    "size": "Standard",
    "qbo_compatible_numbering": true
  }
}
```

---

## 📐 SIZE GUIDELINES

`size` field in config:

| Size | Account Count | Use Case |
|------|:-------------:|----------|
| `Minimal` | 30–40 | Solo entrepreneur, very simple operations |
| `Standard` | 50–80 | Most SMBs (recommended starting point) |
| `Extended` | 80–150 | Multi-location, multi-product, complex tracking |

Industry templates default to `Standard` size. Adjust as needed.

---

## ⚠️ MAINTENANCE RULES

- **Never delete posted accounts** — mark inactive instead (preserves audit trail)
- **Add accounts as needed** — but keep numbering consistent với schema
- **Annual review** — clean up unused accounts at year-end (mark inactive)
- **Document changes** — Operating Agreement / Board minutes for material changes

---

## 🔗 RELATED

- [QuickBooks Online standard COA mapping](_QBO_MAPPING.csv) (Phase 3 Task 3.8)
- Industry-specific guidance: [_MODULES/industry/](../../../_MODULES/industry/)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
