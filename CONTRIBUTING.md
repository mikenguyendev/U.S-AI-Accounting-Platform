# Contributing to AI Accounting Template

> **Mục đích:** File này dành cho anyone muốn mở rộng template (thêm state mới, entity mới, industry mới, Excel template mới) — bao gồm Developer, AI Agent kế nhiệm, hoặc third-party contributors.

**Target audience:** Technical users (developers, accountants với ít kinh nghiệm markdown/git)
**Template version:** 1.0.0
**Last updated:** 2026-04-23

---

## 📚 Table of Contents

1. [Before you start](#before-you-start)
2. [Add a new state module](#add-a-new-state-module)
3. [Add a new entity module](#add-a-new-entity-module)
4. [Add a new industry (COA + module)](#add-a-new-industry)
5. [Add a new Excel template](#add-a-new-excel-template)
6. [Update existing modules (annual tax refresh)](#update-existing-modules)
7. [Add a new HTML form task type](#add-a-new-html-form-task-type)
8. [Testing checklist](#testing-checklist)
9. [Versioning & PR process](#versioning--pr-process)

---

## Before you start

**Read these first:**
- [README.md](README.md) — template architecture overview
- [CHANGELOG.md](CHANGELOG.md) — what's in v1.0.0, known limitations
- [_CORE/RENDER_PROTOCOL.md](_CORE/RENDER_PROTOCOL.md) — 7-pass render algorithm
- [_CONFIG/PLACEHOLDER_CONVENTION.md](_CONFIG/PLACEHOLDER_CONVENTION.md) — `{{}}` syntax spec

**Principles:**

1. **Never break existing instances** — changes to `_MODULES/*` should be additive or fix-only. Breaking changes to schema require MAJOR bump + migration guide.
2. **Date-stamp everything** — tax rates, forms, deadlines change annually. Every numeric fact needs a date-of-authority.
3. **Test before ship** — run the cold-start protocol (see [Testing checklist](#testing-checklist)) with a fresh config after any module change.
4. **No customer data** — anything committed to this repo must be generic. Customer instances live outside version control (in each customer's zipped delivery).

---

## Add a new state module

**When to do this:** You want to expand beyond the 10 priority states (CA, NY, TX, FL, DE, WA, IL, GA, NJ, MA) into any of the other 41 states.

**Effort:** 2–4 hours per state, depending on state tax complexity.

### Steps

1. **Copy the schema template:**
   ```
   _MODULES/state/_STATE_MODULE_SCHEMA.md  →  _MODULES/state/{XX}.md
   ```
   where `{XX}` is the 2-letter state code (uppercase).

2. **Fill in all 11 required sections:**
   - `## tax-obligations` — table of all state taxes (franchise, income, sales, payroll)
   - `## deadlines` — fiscal calendar with forms + due dates
   - `## upcoming-deadlines` — next 12 months rolling
   - `## critical-reminders` — state-specific pitfalls (e.g., "CA $800 minimum franchise tax ALWAYS DUE even if $0 revenue")
   - `## flag-conditions` — AI Agent warning triggers for this state
   - `## validation-rules` — state-specific data validation
   - `## sales-tax` — sourcing rules, exemptions, filing frequency
   - `## estimated-tax` — schedule, forms, safe harbor rules
   - `## withholding-form` — state W-4 equivalent (e.g., DE-4 for CA)
   - `## withholding-tables` — calculation method reference
   - `## payroll-taxes` — employer-side taxes (SUI, SDI, PFML, etc.)
   - `## entity-specific-tax` — how C-Corp/S-Corp/LLC/Partnership each get taxed

3. **Add row to `_MODULES/state/_state_matrix.csv`** — 13 columns (code, name, personal_income_tax_max, corporate_income_tax, franchise_tax_min, sales_tax_state, sales_tax_max, sdi, pfml, workers_comp_threshold, min_wage_2025, pte_election, key_filing_dates).

4. **Source-check everything** — cite:
   - State Department of Revenue website
   - State Secretary of State filings page
   - State Employment/Labor department
   - Include "Last verified: YYYY-MM-DD" at top of the module

5. **Test the render** — pick a sample config (S-Corp + `{XX}` + Service, FY current year) and run render. Verify:
   - 0 unresolved `{{INCLUDE:state/{XX}.md#section-id}}` directives
   - All 11 sections pull correctly into COMPANY_PROFILE, README, AI_AGENT_MEMORY

6. **Update docs:**
   - Add `{XX}` to supported states list in `README.md`
   - Add changelog entry: `### Added — {XX} state module` in `CHANGELOG.md`
   - Bump MINOR version

### Quality bar

The 10 existing states (especially `CA.md`, `NY.md`) are the quality reference. Match their depth:
- Tables for rates, not prose
- Concrete examples for quirky rules (e.g., "CA Q3 estimated tax = 0% of annual" — surprising vs federal)
- Flag `⚠️ CRITICAL` items distinctly

---

## Add a new entity module

**When to do this:** Rarely — the 6 entity types (C-Corp, S-Corp, LLC-single, LLC-multi, Partnership, Sole-Prop) cover 99% of US SMB legal structures. You might add:
- Non-profit (501(c)(3)) — significantly different rules
- B-Corp — currently treated as C-Corp variant
- Benefit Corp — also C-Corp variant
- PLLC (Professional LLC) — currently treated as LLC variant

**Effort:** 4–8 hours per entity type.

### Steps

1. **Copy the schema:**
   ```
   _MODULES/entity/_ENTITY_MODULE_SCHEMA.md  →  _MODULES/entity/{Type}.md
   ```

2. **Update `_CONFIG/_BUSINESS_CONFIG.schema.json`** enum:
   ```json
   "entity_type": {
     "enum": ["C-Corp", "S-Corp", "LLC-single", "LLC-multi", "Partnership", "Sole-Prop", "YOUR_NEW_TYPE"]
   }
   ```
   ⚠️ This is a MAJOR version bump (schema change).

3. **Update render protocol tax-form lookup table** in `_CORE/RENDER_PROTOCOL.md` — add `FORMAT:ENTITY_TYPE|tax_form` mapping.

4. **Update IF-block branches** in all 5 `_CORE/*.md.template` files where entity-specific logic exists:
   - `IF:COMPANY.ENTITY_TYPE == "..."` blocks in README, AI_AGENT_MEMORY, COMPANY_PROFILE
   - IF-block in USE_CASES_GUIDE Use Case 10 (estimated tax) + 11 (tax form prep)

5. **Update HTML forms:**
   - `setup_wizard.html` — add option to Step 1 entity dropdown
   - Both `Accounting_Task_Form.html` forms — no change needed (generic via interpolate)

6. **Fill all 9 required sections** in the new entity module:
   - federal-deadlines, federal-obligations, critical-rules, upcoming-deadlines
   - owner-compensation, owner-comp-protocol
   - flag-conditions, validation-rules, estimated-tax

7. **Cold-start test** (see [Testing checklist](#testing-checklist)) with the new entity type.

---

## Add a new industry

**When to do this:** Current 5 industries (Service, Retail, Restaurant, Manufacturing, SaaS) cover ~85% of US SMB. Likely additions:
- Construction (completed contract vs percentage-of-completion accounting)
- Real Estate (rental income, depreciation schedules, 1031 exchanges)
- Healthcare (HIPAA compliance, insurance billing, Medicare/Medicaid)
- Nonprofit (donor tracking, restricted funds, Form 990)

**Effort:** 4–6 hours per industry.

### Steps

1. **Create COA CSV:**
   ```
   _TEMPLATES/COA/COA_{Industry}.csv
   ```
   - 60–80 accounts, 4-digit numbering (1000s=Assets, 2000s=Liab, 3000s=Equity, 4000s=Rev, 5000s=COGS, 6000s=OpEx, 7000s=Other)
   - Follow QBO numbering convention for future migration
   - Include industry-specific accounts (e.g., `1410 Inventory - Raw Materials` for Manufacturing, `1420 Capitalized Software` for SaaS)

2. **Update `_QBO_MAPPING.csv`** — add rows mapping your new COA accounts to QuickBooks Online Account Type + Detail Type.

3. **Write industry module at `_MODULES/industry/{Industry}.md`:**
   - Overview
   - Key KPIs specific to industry (e.g., Gross Margin, Same-Store Sales, LTV/CAC for SaaS, Table Turns for Restaurant)
   - GAAP nuances specific to industry (ASC 606 revenue recognition quirks, inventory valuation methods)
   - Common issues table
   - Tax optimization opportunities

4. **Update `_CONFIG/_BUSINESS_CONFIG.schema.json`:**
   ```json
   "industry": {
     "enum": ["Service", "Retail", "Restaurant", "Manufacturing", "SaaS", "YOUR_NEW_INDUSTRY"]
   }
   ```

5. **Update `setup_wizard.html`** — add industry option to Step 1 dropdown; extend `DETAILED_STATES` checklist generator if new industry has unique compliance items.

6. **Test:** Render a sample instance with the new industry. Verify COA copies correctly + industry module loads.

---

## Add a new Excel template

**When to do this:** User feedback indicates gap in daily ops (e.g., "I need a Fixed Asset Register with depreciation schedule").

**Effort:** 2–4 hours per template.

### Steps

1. **Design the CSV structure** at `_TEMPLATES/Excel/{TemplateName}.csv`:
   - Header row with clear column names
   - 5–10 sample rows showing realistic data
   - No formulas (CSV doesn't support) — formulas documented in companion MD

2. **Write companion guide** `_TEMPLATES/Excel/{TemplateName}.md`:
   - Purpose + when to use
   - Column-by-column explanation
   - Formulas to add after import (explicit Excel/Google Sheets syntax)
   - Conditional formatting rules
   - Data validation rules
   - Sample interpretations ("If Column X > Y, it means...")
   - Common pitfalls

3. **Update `_TEMPLATES/Excel/Index_workbook.md`** dependency diagram — add the new template + note which other templates it feeds into / depends on.

4. **Update `_CORE/FORM_SCHEMA.md.template`** if the template is tied to a form task type.

5. **Test:** Copy CSV into Google Sheets, apply formulas per MD, verify calculations match expected outputs.

---

## Update existing modules (annual tax refresh)

**When to do this:** Typically January each year when:
- Federal income tax brackets published (IRS Rev. Proc. in November prior)
- Social Security wage base updated (always $168,600 for 2026; announced October prior year)
- State tax rates change (varies by state)
- State minimum wage changes (January 1 most states)
- CA franchise tax, CA SDI rate, CA SUI rate changes

**Effort:** 1–2 days total for a full annual refresh (depending on # of states affected).

### Process

1. **Create branch:** `tax-refresh-YYYY`

2. **Update per state:** Grep for year-specific figures in `_MODULES/state/*.md`:
   ```
   grep -l "2025\|1.1%\|$168,600" _MODULES/state/*.md
   ```

3. **Critical files to check:**
   - Each state's `tax-obligations` section (rates)
   - Each state's `payroll-taxes` section (SDI, SUI, ETT rates)
   - Each state's `validation-rules` section (minimum wage)
   - `_state_matrix.csv` — refresh all numeric columns
   - `_CORE/AI_AGENT_MEMORY.md.template` — federal FICA cap reference
   - `_CORE/FORM_SCHEMA.md.template` — Form 14 (payroll-run) FICA cap

4. **Bump PATCH version** (e.g., 1.0.0 → 1.0.1) in CHANGELOG.md.

5. **Notify existing customers:** Deliver updated zip or update `_MODULES/` folder in their workspace. Note this in delivery naming: `{Customer}_v1.0.1_2027-01-15.zip`.

---

## Add a new HTML form task type

**When to do this:** User feedback indicates a repeatable accounting workflow not covered by the existing 18 task types.

**Effort:** 2–3 hours.

### Steps

1. **Decide which form (minimal or Full version):**
   - Minimal: for photo-first 2-click flow (vendor invoice, expense, deposit, bank statement, W-9, W-4)
   - Full version: for structured input with 5–15 fields (customer invoice, journal entry, payroll run, etc.)

2. **Add to `PHOTO_TASKS`, `QUICK_REQUESTS`, or `FORM_TASKS`** object in the HTML:
   ```javascript
   'task-id': {
     icon: '📌',
     title: 'Task Title',
     subtitle: 'Short description',
     prompt: `📌 TASK TITLE — {{COMPANY.NAME}}
     ... use {{PLACEHOLDER}} tokens for dynamic values
     `,
     fields: [ /* for FORM_TASKS only */ ]
   }
   ```

3. **Update `_CORE/FORM_SCHEMA.md.template`:**
   - Add row to "18 FORM TYPES — COMPLETE INDEX" table (now 19)
   - Add "Form N:" section with AI MUST protocol
   - Update the "TASK-SPECIFIC RESPONSE QUICK REFERENCE" table

4. **Add dashboard button** in HTML with appropriate category grouping.

5. **Test in browser:** fill form → verify prompt generation includes interpolated placeholders correctly.

---

## Testing checklist

Before submitting any change, run this checklist:

### Cold-start test (simulates fresh customer onboarding)

1. Create a test config at `_CONFIG/test_config.json`:
   ```json
   {
     "schema_version": "1.0.0",
     "instance_id": "Test_Business_LLC",
     "company": { "legal_name": "Test Business LLC", "entity_type": "...", "industry": "...", ... },
     "operations": { "state_of_operation": "...", ... },
     ...
   }
   ```
   Use a combination different from `Acme_Widget_LLC` (LLC-multi + TX + Retail, the shipped test instance). For example, try C-Corp + DE + SaaS or Sole-Prop + FL + Restaurant.

2. Prompt AI Agent: *"Render a workspace from `_CONFIG/test_config.json` per `_CORE/RENDER_PROTOCOL.md`. Save to `_INSTANCES/Test_Business_LLC/`."*

3. **Verify:**
   - [ ] 5 MD files created in instance
   - [ ] `grep "{{" _INSTANCES/Test_Business_LLC/*.md` returns 0 matches
   - [ ] Entity-specific content correctly included (e.g., LLC-multi K-1 rules, NOT S-Corp 1120-S)
   - [ ] State-specific content correctly included (e.g., TX margin tax, NOT CA franchise tax)
   - [ ] Industry COA copied correctly with right number of accounts
   - [ ] Folder structure has all 28 sub-folders (empty is OK)
   - [ ] HTML form loads config via `?config=_INSTANCES/Test_Business_LLC/_BUSINESS_CONFIG.json` → header shows correct entity/state

4. **Cleanup:** Delete the test instance + test config before committing.

### Schema compliance test

```
# Validate against schema (requires `ajv-cli` or similar)
ajv validate -s _CONFIG/_BUSINESS_CONFIG.schema.json -d _CONFIG/_BUSINESS_CONFIG.example.json
```

### Cross-reference check

```
# Any broken relative paths?
grep -rn "_CORE/\|_MODULES/\|_TEMPLATES/" . | grep -v "^_DEPRECATED"
```

All referenced files should exist. If a reference points to something that doesn't exist, either create the file or update the reference.

---

## Versioning & PR process

### Branch naming

- `feature/state-{XX}` — new state module
- `feature/entity-{Type}` — new entity type
- `feature/industry-{Name}` — new industry
- `feature/template-{Name}` — new Excel template
- `fix/{short-description}` — bug fix
- `tax-refresh-{YYYY}` — annual tax rate update

### PR checklist

- [ ] Cold-start test passed with combinations exercising your change
- [ ] `grep "{{"` on rendered instance returns 0 matches
- [ ] Cross-references resolve (`grep -rn "_CORE\|_MODULES\|_TEMPLATES"` all hit existing files)
- [ ] `CHANGELOG.md` entry added (under `[Unreleased]` section at top until release)
- [ ] If schema changed: migration guide drafted
- [ ] Date stamps on all tax-related figures added (e.g., "2026 rate")
- [ ] No customer PII or customer-specific names committed

### Releases

Maintainer (currently `mikenguyen.dev@gmail.com`):
1. Review PR against checklist
2. Merge to `main`
3. Tag release: `git tag v1.1.0`
4. Update `CHANGELOG.md` — move `[Unreleased]` items to new version section with date
5. Push tag: `git push origin v1.1.0`
6. Notify known customers if their modules were affected

---

## Code of Conduct

- **Data accuracy > everything.** Tax/compliance misinformation causes real financial harm to users. Always cite source + date.
- **Respect user privacy.** Never include customer names, EINs, or PII in examples or tests.
- **Bilingual respect.** The template is Vietnamese + English. Contributions in either language are welcome, but reference docs (module schemas) stay in English for consistency.
- **Constructive feedback.** If you find an error in an existing module, file an issue with citation (state DOR link, IRS publication number, etc.) — don't just remove content.

---

## Questions?

- Template architecture: `mikenguyen.dev@gmail.com`
- Tax questions: Consult a licensed CPA (we don't provide tax advice)
- Business continuity: Read `_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md`

---

*AI Accounting Template v1.0.0 — mikenguyen.dev@gmail.com*
