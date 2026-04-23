# 📁 _INSTANCES

> Folder này chứa **rendered workspaces** cho từng business instance.

## Cách tạo instance mới

1. Copy `_CONFIG/_BUSINESS_CONFIG.example.json` → `_CONFIG/_BUSINESS_CONFIG.json`
2. Customize config theo business của bạn (xem [_CONFIG/_BUSINESS_CONFIG.schema.json](../_CONFIG/_BUSINESS_CONFIG.schema.json))
3. Prompt AI Agent: *"Read `_CORE/RENDER_PROTOCOL.md` and render workspace từ `_CONFIG/_BUSINESS_CONFIG.json`"*
4. AI sẽ tạo `_INSTANCES/{your_instance_id}/` với 5 file MD + config copy

## Cấu trúc instance

```
_INSTANCES/
└── {your_instance_id}/                   ← snake_case, từ config.instance_id
    ├── _BUSINESS_CONFIG.json             ← Copy của config dùng để render
    ├── README.md                         ← Workspace overview
    ├── AI_AGENT_MEMORY.md                ← Quick context loader
    ├── COMPANY_PROFILE.md                ← Company profile (master document)
    ├── FORM_SCHEMA.md                    ← AI form processing protocol
    ├── USE_CASES_GUIDE.md                ← 20 common use cases
    │
    ├── 00_Archive/                       ← Historical FY data
    ├── 01_AP-AR_Management/              ← Vendor invoices, customer invoices
    ├── 02_General_Ledger/                ← COA, JE, adjusting entries
    ├── 03_Bank_Reconciliation/
    ├── 04_Tax_Compliance/                ← 1099, W-2, federal/state forms
    ├── 05_Payroll/
    ├── 06_Financial_Reporting/           ← P&L, BS, Cash Flow
    └── 07_Budget_Variance_Analysis/
```

## Multi-tenant (multiple businesses)

Bạn có thể manage nhiều businesses trong cùng template:

```
_INSTANCES/
├── Acme_Consulting_LLC/
├── Beta_Manufacturing_Inc/
└── Gamma_Restaurant_Group/
```

Mỗi instance độc lập, có config riêng. Phù hợp cho fractional CFO use case.

## Privacy reminder

⚠️ Instance folders chứa **confidential business data** (PII, SSN, EIN, bank accounts). Đảm bảo:
- KHÔNG commit instance folders vào public git repos
- Backup riêng theo data retention policy (IRS = 7 năm tối thiểu)
- Encrypt at rest nếu lưu trên cloud

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
