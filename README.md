# 🏢 AI Accounting Controller — White-Label Template

> **Plug-and-play AI Agent template for US Small Business accounting workflow.**
> Fill wizard → Get personalized workspace in 5 minutes → AI Agent acts as Corporate Controller for your company.

**Version:** 1.0.0 (stable)
**Developer:** mikenguyen.dev@gmail.com
**License:** See [LICENSE](LICENSE)
**Status:** ✅ Production-ready. All 8 development phases complete. See [CHANGELOG.md](CHANGELOG.md) for what ships.

**Languages:** 🇬🇧 English (this file) • 🇻🇳 [Tiếng Việt](README.vi.md) • 🇪🇸 [Español](README.es.md)

**👉 New to this? Read [QUICKSTART.md](QUICKSTART.md) first** ([VN](QUICKSTART.vi.md) • [ES](QUICKSTART.es.md)) — **detailed guide for non-technical users** with daily case studies.

---

## 🎯 What is this?

Reusable AI Accounting template that lets you deploy a **Corporate Accounting Controller** AI Agent for:

- ✅ **AP/AR Management** — Vendor invoices, customer invoices, aging reports
- ✅ **General Ledger** — Journal entries, adjusting entries, trial balance
- ✅ **Bank Reconciliation** — Monthly recon worksheets with adjusting JE templates
- ✅ **Tax Compliance** — Federal (1120/1120-S/1065/Schedule C) + State + Payroll filings
- ✅ **Payroll** — W-2/1099 processing, federal + state withholding
- ✅ **Financial Reporting** — P&L, Balance Sheet, Cash Flow per US GAAP
- ✅ **Budget & Variance** — Department-level analysis with reforecast recommendations

**US GAAP + IRS compliant**, designed for **Vietnamese-speaking US business owners** (bilingual VN/EN), but works equally well for English-only users (set `owner.preferred_language: "en"` in config).

**Coverage:**
- 6 entity types × 10 detailed states × 5 industries = **300 fully-modeled configurations**
- 41 additional states supported via Lenient render mode (generic fallback)
- 10 Excel templates for daily operations (JE, TB, Bank Recon, AR/AP Aging, P&L, BS, Cash Flow, Payroll, Budget)
- 18 accounting task types via browser-based forms with AI response protocols

---

## 🏗️ Architecture

```
AI_Accounting_Controller/
├── README.md                            ← You are reading this (EN)
├── README.vi.md                         ← Vietnamese overview
├── README.es.md                         ← Spanish overview
├── QUICKSTART.md                        ← ⭐ Beginner walkthrough with case studies (EN)
├── QUICKSTART.vi.md                     ← Vietnamese beginner guide
├── QUICKSTART.es.md                     ← Spanish beginner guide
├── CHANGELOG.md                         ← Version history
├── CONTRIBUTING.md                      ← How to extend (states, entities, industries)
├── LICENSE                              ← Usage terms
│
├── _CONFIG/                             ← Configuration layer
│   ├── _BUSINESS_CONFIG.schema.json     ← JSON Schema draft-07 validation
│   ├── _BUSINESS_CONFIG.example.json    ← Generic "Acme Service Group" sample
│   ├── PLACEHOLDER_CONVENTION.md        ← {{PLACEHOLDER}} syntax spec
│   ├── setup_wizard.html                ← 6-step browser onboarding wizard
│   └── NEW_BUSINESS_ONBOARDING_PROTOCOL.md  ← AI agent 7-step workflow
│
├── _CORE/                               ← Templates (rendered per-customer)
│   ├── README.md.template               ← Workspace overview + handoff doc
│   ├── AI_AGENT_MEMORY.md.template      ← Quick context loader
│   ├── COMPANY_PROFILE.md.template      ← Master profile (compliance, deadlines)
│   ├── FORM_SCHEMA.md.template          ← 18 task form AI response protocols
│   ├── USE_CASES_GUIDE.md.template      ← 20 common use cases with prompts
│   └── RENDER_PROTOCOL.md               ← 7-pass resolution algorithm
│
├── _MODULES/                            ← Knowledge base (16 modules)
│   ├── entity/                          ← C-Corp, S-Corp, LLC-single, LLC-multi, Partnership, Sole-Prop
│   ├── state/                           ← CA, NY, TX, FL, DE, WA, IL, GA, NJ, MA + matrix CSV
│   ├── industry/                        ← Service, Retail, Restaurant, Manufacturing, SaaS
│   └── COMPLIANCE_CALENDAR_GENERATOR.md ← Entity × state deadline algorithm
│
├── _TEMPLATES/                          ← Reusable artifacts
│   ├── COA/                             ← 5 industry Chart of Accounts CSVs + QBO mapping
│   └── Excel/                           ← 10 Excel templates (CSV + guide MD each)
│
├── _INSTANCES/                          ← Customer workspaces (your data lives here)
│   ├── README.md                        ← How to create a new instance
│   └── {customer_id}/                   ← Created via render protocol (wizard → JSON → render)
│
├── _DELIVERIES/                         ← Customer delivery packages (versioned zips)
│   └── {customer_id}_v1.0_YYYY-MM-DD/   ← Self-contained workspace ready to email
│
├── Accounting_Task_Form.html            ← Minimal daily-use form (2-click rule)
├── Accounting_Task_Form - Full version.html  ← Full 18-type form
├── VERSION                              ← Current version (1.0.0)
│
├── _ARCHIVE/                            ← Completed roadmaps + migration guides
│   └── Roadmap_Refactor_v1_DONE.md      ← 8-phase development log
│
└── _DEPRECATED_pre_template/            ← Legacy files from pre-refactor era (for history)
```

---

## 🚀 Quick Start — 3 paths

### 🅰️ Path A: New business onboarding (customer-facing)

**Use when:** You're onboarding a new client (or your own business) into the template.

**Time:** ~5 minutes for wizard + ~5 minutes for AI render.

1. **Fill the wizard:**
   Open [_CONFIG/setup_wizard.html](_CONFIG/setup_wizard.html) in your browser (Chrome/Edge recommended).
   Complete 6 steps: Business Identity → Location → Operations → Owner → Compliance → Review.
   Click **Download JSON** and **Download Checklist**.

2. **Save the downloads** to a new folder: `_INSTANCES/{your_instance_id}/`

3. **Prompt your AI Agent:**
   > *"Read `_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md` and render my workspace from `_INSTANCES/{your_instance_id}/_BUSINESS_CONFIG.json`."*

4. **AI executes 7 steps:** validates config → creates folder tree → renders 5 MDs → copies COA → reports critical items.

5. **Done.** Your workspace is live. Open `Accounting_Task_Form.html` and start your first task.

### 🅱️ Path B: Fractional CFO / multi-client

**Use when:** You manage multiple businesses (one template, N instances).

1. For each client, run Path A — each gets their own `_INSTANCES/{client_id}/` folder.
2. The HTML form has a **⚙️ switcher** in the header — click to upload a different config without reloading.
3. URL-param shortcut: `Accounting_Task_Form.html?config=_INSTANCES/Client_A/_BUSINESS_CONFIG.json`
4. Recent configs stored in localStorage (last 5 shown as quick-switch buttons).

### 🅲 Path C: Customer delivery (zip + email)

**Use when:** You want to package a customer's workspace as a self-contained zip to send them.

1. After Path A, ask AI: *"Create a customer delivery package (Option A minimal) for `{customer_id}`."*
2. AI creates `_DELIVERIES/{customer_id}_v1.0_YYYY-MM-DD/` folder with everything the customer needs (instance + HTML forms + relevant modules).
3. Zip that folder (Windows: right-click → Send to → Compressed folder) or PowerShell: `Compress-Archive`.
4. Email zip to customer. They unzip, open `START_HERE.md`, and run their own AI.

Example delivery structure (produced per customer, not committed to git — see `.gitignore`): `_DELIVERIES/{customer_id}_v1.0_YYYY-MM-DD/`.

---

## ⚙️ Supported configurations

### Entity types (6)

| Type | Tax form | Owner comp rule | Pass-through? |
|------|----------|------------------|:--------------:|
| C-Corp | Form 1120 | Salary OR dividends | ❌ (double taxation) |
| S-Corp | Form 1120-S | **Reasonable comp BEFORE distributions** (IRS audit trigger #1) | ✅ via K-1 |
| LLC-single | Schedule C | Owner draw + SE tax | ✅ |
| LLC-multi | Form 1065 | Guaranteed payments + K-1 | ✅ |
| Partnership | Form 1065 | Guaranteed payments + K-1 | ✅ |
| Sole-Prop | Schedule C | Owner draw + SE tax | ✅ |

Detailed rules in [_MODULES/entity/](_MODULES/entity/).

### States (10 detailed + 41 via fallback)

**Full modules** (tax-obligations, deadlines, payroll rates, withholding, entity-specific tax):

| State | Key feature | Module |
|-------|-------------|--------|
| CA | $800 franchise + 1.5% S-Corp tax + SDI/ETT/SUI | [CA.md](_MODULES/state/CA.md) |
| NY | PTET election + NYC tax + MCTMT | [NY.md](_MODULES/state/NY.md) |
| TX | No income tax, Margin tax (0.375%–0.75%) | [TX.md](_MODULES/state/TX.md) |
| FL | No income tax, C-Corp only 5.5% | [FL.md](_MODULES/state/FL.md) |
| DE | Incorporation hub, franchise tax method election | [DE.md](_MODULES/state/DE.md) |
| WA | B&O gross receipts tax + Capital Gains 7% | [WA.md](_MODULES/state/WA.md) |
| IL | 4.95% flat + Replacement Tax | [IL.md](_MODULES/state/IL.md) |
| GA | Recently flat 5.39% + Net Worth Tax | [GA.md](_MODULES/state/GA.md) |
| NJ | BAIT election, FLI/PFL, Wage Act triple damages | [NJ.md](_MODULES/state/NJ.md) |
| MA | 5% + 4% Millionaire Tax, PFML | [MA.md](_MODULES/state/MA.md) |

Plus [_state_matrix.csv](_MODULES/state/_state_matrix.csv) quick lookup table.

**Other 41 states:** Render works but state-specific rules need manual lookup (AI flags this). Phase 2.5 planned to fill gaps — see [CONTRIBUTING.md](CONTRIBUTING.md#add-a-new-state-module).

### Industries (5)

| Industry | COA size | Key accounts | Guide |
|----------|:--------:|--------------|-------|
| Service | 60 accounts | Consulting/agency focus, no inventory | [Service.md](_MODULES/industry/Service.md) |
| Retail | 75 accounts | Inventory + Sales Tax Payable + Gift Cards | [Retail.md](_MODULES/industry/Retail.md) |
| Restaurant | 70 accounts | Food/Bev/Beer/Wine/Spirits split + Tips Payable | [Restaurant.md](_MODULES/industry/Restaurant.md) |
| Manufacturing | 80 accounts | 3-tier inventory (Raw/WIP/Finished) + overhead | [Manufacturing.md](_MODULES/industry/Manufacturing.md) |
| SaaS | 65 accounts | Deferred Revenue + Capitalized Commissions (ASC 606) | [SaaS.md](_MODULES/industry/SaaS.md) |

---

## 🤖 AI Agent compatibility

Tested and recommended:

- **Claude (Anthropic)** — Primary tested platform, Opus 4.7 / Sonnet 4.6
- **ChatGPT (OpenAI)** — GPT-4o class, compatible with minor prompt tweaks
- **Gemini (Google)** — 1.5 Pro / 2.0 tested

**Context window:** ≥200K tokens recommended. The core docs + relevant modules total ~80–120 KB (~25–35K tokens) depending on entity × state.

**First prompt** for any new AI session (paste this):
> *"Read these files in order: `_BUSINESS_CONFIG.json`, `AI_AGENT_MEMORY.md`, `COMPANY_PROFILE.md`, `FORM_SCHEMA.md`. Confirm context loaded (entity, state, FY, next deadline), then ask what task I want to tackle."*

---

## 📚 Documentation

| File | Purpose | Audience |
|------|---------|----------|
| **[QUICKSTART.md](QUICKSTART.md)** ([VN](QUICKSTART.vi.md) • [ES](QUICKSTART.es.md)) | **Beginner walkthrough with daily case studies** ⭐ | **Non-technical users** |
| [README.md](README.md) ([VN](README.vi.md) • [ES](README.es.md)) | Project overview (this file) | Everyone |
| [CHANGELOG.md](CHANGELOG.md) | Version history + what ships in v1.0.0 | Everyone |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to extend template (states, entities, industries) | Developers |
| [_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md](_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md) | 7-step AI agent onboarding workflow | AI Agents |
| [_CORE/RENDER_PROTOCOL.md](_CORE/RENDER_PROTOCOL.md) | 7-pass template resolution algorithm | AI Agents |
| [_CONFIG/PLACEHOLDER_CONVENTION.md](_CONFIG/PLACEHOLDER_CONVENTION.md) | `{{PLACEHOLDER}}` syntax spec | Developers |
| [_CONFIG/_BUSINESS_CONFIG.schema.json](_CONFIG/_BUSINESS_CONFIG.schema.json) | Config schema (JSON Schema draft-07) | Developers |
| [_TEMPLATES/Excel/Index_workbook.md](_TEMPLATES/Excel/Index_workbook.md) | 10 Excel templates master index | Users + AI Agents |

---

## ⚠️ Disclaimers

- **Not legal/tax advice.** Template provides accounting workflow automation. **Always consult a licensed CPA** for complex tax decisions, audits, or jurisdiction-specific issues.
- **Compliance accuracy.** Tax rates and rules are current as of 2026 publication dates. Laws change — verify with CPA before filing. See [CONTRIBUTING.md](CONTRIBUTING.md#update-existing-modules-annual-tax-refresh) for annual refresh process.
- **AI hallucination risk.** AI Agents can make mistakes. Always double-check critical numbers, especially before month-end close or tax filing. Use the **Confirm** phase of the 5-phase AI protocol — never skip it.
- **Data security.** Workspace contains PII (SSN, EIN, bank accounts). You are responsible for securing data when sharing with AI Agents. Consider on-prem or enterprise AI plans with data privacy guarantees for sensitive clients.

---

## 👤 Developer

**mikenguyen.dev@gmail.com**

- Bug reports + feature requests: email
- Commercial licensing (multi-tenant SaaS deployment, white-label resale): email
- Contribution proposals (new state module, new industry, etc.): see [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 📝 Recent highlights

**v1.0.0 — 2026-04-23** (initial stable release):
- Full 8-phase refactor complete (75/75 tasks)
- Config-driven architecture: 1 JSON → 5 rendered MDs + COA + checklist
- 6 entity × 10 state × 5 industry modules shipped
- HTML forms runtime config-aware + offline Tailwind fallback
- Customer delivery packaging pattern proven via real-customer render + zip workflow

Full details: [CHANGELOG.md](CHANGELOG.md)

---

*Built with ❤️ for Vietnamese-speaking US business owners — and everyone else.*
