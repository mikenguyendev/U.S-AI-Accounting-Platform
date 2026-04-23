# Changelog

Tất cả changes đáng chú ý của **AI Accounting Template** được document ở file này.

Format dựa trên [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), và project tuân thủ [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.1.0] — 2026-04-23

**📚 Multi-language docs + beginner-friendly QUICKSTART guide.** No template code changes — pure documentation release so non-technical users in Vietnamese and Spanish-speaking markets can onboard without needing English fluency.

### Added — User-facing docs (3 languages)
- `QUICKSTART.md` (EN), `QUICKSTART.vi.md` (VN), `QUICKSTART.es.md` (ES) — Detailed walkthrough for non-technical users:
  - Part 1: First-time setup in 10 minutes (6 step-by-step screens)
  - Part 2: How to talk to AI — golden rule + copy-paste prompt templates
  - Part 3: 5 daily case studies with exact prompts (vendor invoice, expense receipt, customer invoice, monthly close, new employee hire)
  - Part 4: FAQ / troubleshooting (7 common issues)
  - Part 5: Where to get help (CPA vs template vs developer scope)
  - First Week Checklist + 5 tips for non-IT users
- `README.vi.md` (VN), `README.es.md` (ES) — Localized project overviews with 3-path quickstart (new business / fractional CFO / customer delivery) + AI agent compatibility notes + docs table with prominent QUICKSTART links
- Updated root `README.md` — language selector at top (🇬🇧 • 🇻🇳 • 🇪🇸), prominent QUICKSTART call-out for newcomers, refreshed docs table showing all language variants by audience (non-technical users / developers / AI agents)

### Added — Privacy protection
- `.gitignore` — comprehensive exclusion of customer data:
  - `_INSTANCES/*/` (per-customer workspaces, contain PII)
  - `_DELIVERIES/` (zipped customer packages)
  - `_DEPRECATED_pre_template/` (legacy pre-refactor customer data)
  - `_CONFIG/_BUSINESS_CONFIG.json` (plain, non-example config)
  - Standard excludes: OS junk, IDE files, Python/Node artifacts, secrets

### Changed
- Bumped `VERSION` file: 1.0.0 → 1.1.0

### No code changes
- Zero changes to `_MODULES/`, `_CORE/`, `_TEMPLATES/`, `_CONFIG/setup_wizard.html`, or HTML forms. Existing v1.0.0 instances need no migration — this is purely an additive documentation release.

---

## [1.0.0] — 2026-04-23

**🎉 Initial stable release.** Plug-and-play AI Accounting template cho US Small Business.

### Added — Configuration Layer (`_CONFIG/`)
- `_BUSINESS_CONFIG.schema.json` — JSON Schema (draft-07) với 14 top-level properties, strict `additionalProperties: false`, enum validation cho entity types (6), states (51), industries (5), payroll providers (8), accounting software (9)
- `_BUSINESS_CONFIG.example.json` — Generic "Acme Service Group" sample config
- `PLACEHOLDER_CONVENTION.md` — `{{SECTION.FIELD}}` UPPERCASE dot-notation spec; 4 directive types (INCLUDE, IF, FORMAT, COMPUTED); 8 built-in formatters; 6 computed values
- `setup_wizard.html` — 6-step browser wizard (~28 fields); draft persistence via localStorage; validation aligned with schema; outputs `_BUSINESS_CONFIG.json` + tailored `ONBOARDING_CHECKLIST.md` (~30 items)
- `NEW_BUSINESS_ONBOARDING_PROTOCOL.md` — 7-step AI agent workflow for end-to-end customer onboarding

### Added — Core Templates (`_CORE/`)
- 5 Markdown templates that render per-instance from config:
  - `README.md.template` — workspace overview + handoff doc
  - `AI_AGENT_MEMORY.md.template` — quick context loader
  - `COMPANY_PROFILE.md.template` — master profile (compliance, deadlines, approval matrix)
  - `FORM_SCHEMA.md.template` — 18 task form AI response protocols
  - `USE_CASES_GUIDE.md.template` — 20 common use cases with prompt samples
- `RENDER_PROTOCOL.md` — 7-pass resolution algorithm (FIELD → FORMAT → COMPUTED → IF → INCLUDE → EXISTS → cleanup); strict vs lenient mode for missing modules

### Added — Knowledge Base (`_MODULES/`)
- **6 entity modules** (covering 100% of US SMB legal structures):
  - C-Corp, S-Corp, LLC-single, LLC-multi, Partnership, Sole-Prop
  - Each with 9 standardized sections: federal-deadlines, federal-obligations, critical-rules, upcoming-deadlines, owner-compensation, owner-comp-protocol, flag-conditions, validation-rules, estimated-tax
- **10 state modules** (~80% US SMB population coverage):
  - CA, NY, TX, FL, DE, WA, IL, GA, NJ, MA
  - Each with 11 sections: tax-obligations, deadlines, upcoming-deadlines, critical-reminders, flag-conditions, validation-rules, sales-tax, estimated-tax, withholding-form, withholding-tables, payroll-taxes, entity-specific-tax
  - `_state_matrix.csv` — quick lookup across 13 columns (rates, deadlines, key indicators)
- **5 industry modules** (~85% SMB types coverage):
  - Service, Retail, Restaurant, Manufacturing, SaaS
  - Each with KPIs, GAAP nuances, common issues, tax optimization
- `COMPLIANCE_CALENDAR_GENERATOR.md` — algorithm + ICS format spec for entity × state deadline calendars

### Added — Chart of Accounts (`_TEMPLATES/COA/`)
- 5 industry COA CSVs (~340 accounts total, QBO-compatible 4-digit numbering):
  - `COA_Service.csv` (60 accounts) — consulting/agency focus
  - `COA_Retail.csv` (75 accounts) — Inventory + Sales Tax Payable + Gift Cards
  - `COA_Restaurant.csv` (70 accounts) — Food/Bev/Beer/Wine/Spirits split + Tips Payable
  - `COA_Manufacturing.csv` (80 accounts) — 3-tier inventory (Raw/WIP/Finished) + overhead allocation
  - `COA_SaaS.csv` (65 accounts) — Deferred Revenue + Capitalized Commissions (ASC 606) + Capitalized Software (ASC 985-20)
- `_QBO_MAPPING.csv` — migration map to QuickBooks Online Account Type + Detail Type
- `_COA_SCHEMA.md` — COA structure spec + numbering convention + size guidelines

### Added — Excel Templates (`_TEMPLATES/Excel/`)
- 10 CSV templates + 10 companion MD guides with formulas, conditional formatting, validation rules, troubleshooting:
  - `JournalEntry` — auto-balance check, JE-level subtotals, Status enum
  - `TrialBalance` — SUMIFS from JE, balance check, normal-balance handling
  - `BankReconciliation` — 2-way recon worksheet, adjusting JE templates
  - `AR_Aging` + `AP_Aging` — auto-bucket Current/30/60/90/90+, DSO calc, 1099 tracking
  - `P&L` — Current/YTD/Prior Year/Budget cols, EBITDA recon, industry benchmarks
  - `BalanceSheet` — balance check, ratio analysis
  - `CashFlow` — Indirect method, working capital changes, FCF metric
  - `PayrollRegister` — all federal + state taxes, employer cost calc
  - `BudgetVsActual` — variance decomposition, reforecast, action items
- `Index_workbook.csv + .md` — master navigator with dependency diagram + close cycle workflow

### Added — HTML Task Forms (root level)
- `Accounting_Task_Form.html` — minimal 2-click flow (photo-first workflow), 6 photo tasks + 3 quick requests + 8 input forms
- `Accounting_Task_Form - Full version.html` — 18 task types with full schema; config-aware preview/JSON export/clipboard copy
- Both forms: runtime config loading (cascading fallback: URL param → localStorage → sibling → `_CONFIG/` → example → file picker modal), `{{PLACEHOLDER}}` interpolation at submit time, offline Tailwind CSS fallback (auto-activates after 3s if CDN unreachable), ⚙️ switcher modal for multi-client (fractional CFO use case)

### Added — Instance Management (`_INSTANCES/`)
- Per-customer workspace folder pattern (customer folders excluded from git — see `.gitignore`)
- Demo test instance shipped: `Acme_Widget_LLC/` (LLC-multi + TX + Retail, FY2026, fake data for reference)
- 8-category data folder tree (00_Archive through 07_Budget_Variance_Analysis)

### Added — Deliveries (`_DELIVERIES/`)
- Customer delivery packaging pattern: version-tagged folder containing self-contained zip-ready workspace
- Typical delivery: `{customer_id}_vX.Y_YYYY-MM-DD.zip` (~100 KB compressed, ~300 KB uncompressed, 16 files + 42 folders)
- Entire folder excluded from git (`.gitignore`) since each delivery contains customer PII

### Documentation
- Root `README.md` — template overview + quick start
- `LICENSE` — usage terms
- `CONTRIBUTING.md` — how to extend (add states, entities, industries)
- `Roadmap_Refactor.md` — 8-phase development log (archived in `_ARCHIVE/` after v1.0.0)

### Coverage Stats
- **Entity × State × Industry combinations supported:** 6 × 10 × 5 = **300 fully-modeled configurations**; 6 × 41 × 5 = 1,230 additional combos via Lenient render mode (generic state fallback)
- **Daily close cycle workflow:** end-to-end supported via Excel templates + HTML form + rendered protocols
- **White-label status:** 0 customer-name leaks outside `_DEPRECATED_pre_template/`; template ready for commercial distribution

### Known Limitations
- Excel templates are CSV+MD pairs (not native `.xlsx`) — user applies formulas per companion MD. AI agents don't natively generate `.xlsx`.
- 41 states without dedicated modules use **Lenient render mode**: rendering completes but AI agent must look up state rules manually or fall back to federal guidance.
- `setup_wizard.html` validates against schema client-side, but strict semantic checks (e.g., FY start < end, tier ordering) only happen during AI agent render pass.
- Multi-state nexus (`operations.additional_states`) is captured in config but not yet rendered into deadlines/obligations — Phase 2.5 scope.
- File:// protocol in some browsers blocks `fetch()` for config auto-load — file picker fallback covers this UX gap.

### Planned for v1.1 (Phase 2.5)
- 40 additional state modules (fill out 50-state coverage)
- Multi-state apportionment rendering in COMPANY_PROFILE
- 3 more industries (Construction, Real Estate, Healthcare)
- Auto-update annual tax rates via external data source
- Native `.xlsx` generation via AI tool improvements

---

## Version Policy

**Semantic Versioning** (MAJOR.MINOR.PATCH):

- **MAJOR** bumps when:
  - `_BUSINESS_CONFIG.schema.json` breaking changes (field removed, type changed, enum shrunk)
  - Render protocol breaking changes (placeholder syntax changed, INCLUDE semantics altered)
  - Deliverable format breaking changes (folder structure, naming convention shift)
- **MINOR** bumps when:
  - New state/entity/industry modules added
  - New Excel template added
  - New HTML form field/task type
  - New formatter, computed value, or directive type
- **PATCH** bumps when:
  - Tax rate annual refresh (most common — typically 1× per year in Q1)
  - Module content corrections (typos, clarifications)
  - HTML form UX fixes
  - Documentation improvements

**Breaking change commitment:** Any MAJOR bump includes a migration guide at `_ARCHIVE/migration_guide_vX.md` + at least 90 days notice before removing deprecated fields.

---

*AI Accounting Template by mikenguyen.dev@gmail.com*
