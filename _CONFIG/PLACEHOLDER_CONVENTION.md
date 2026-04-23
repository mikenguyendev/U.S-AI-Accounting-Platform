# 🔣 PLACEHOLDER CONVENTION

> **Mục đích:** Quy ước thống nhất cho `{{...}}` placeholders trong tất cả `.md.template` files. AI Agent dùng tài liệu này để render template + config → instance file chính xác.

**Version:** 1.0.0
**Last Updated:** 2026-04-22
**Status:** 🟢 Stable — không thay đổi mà không bump major version

---

## 1. SYNTAX

### Basic placeholder
```
{{SECTION.FIELD}}
{{SECTION.SUBSECTION.FIELD}}
```

**Rules:**
- Bao bọc bằng `{{` và `}}` (double curly braces)
- UPPERCASE
- Dot-notation theo cấu trúc JSON config
- KHÔNG có space giữa braces và content
- KHÔNG nested placeholder trong placeholder

### Examples
| Placeholder | Maps to (JSON path) |
|-------------|---------------------|
| `{{COMPANY.LEGAL_NAME}}` | `company.legal_name` |
| `{{COMPANY.ENTITY_TYPE}}` | `company.entity_type` |
| `{{COMPANY.EIN}}` | `company.ein` |
| `{{OPERATIONS.STATE_OF_OPERATION}}` | `operations.state_of_operation` |
| `{{OPERATIONS.ACCOUNTING_SOFTWARE}}` | `operations.accounting_software` |
| `{{FISCAL_YEAR.YEAR}}` | `fiscal_year.year` |
| `{{FISCAL_YEAR.START_DATE}}` | `fiscal_year.start_date` |
| `{{OWNER.NAME}}` | `owner.name` |
| `{{OWNER.EMAIL}}` | `owner.email` |
| `{{APPROVAL_THRESHOLDS.TIER_1_MAX}}` | `approval_thresholds.tier_1_max` |

---

## 2. SPECIAL DIRECTIVES

### `{{INCLUDE:path}}` — Insert content of another file

```
{{INCLUDE:_MODULES/entity/{{COMPANY.ENTITY_TYPE}}.md}}
{{INCLUDE:_MODULES/state/{{OPERATIONS.STATE_OF_OPERATION}}.md}}
```

**Rules:**
- Path relative đến template root
- Cho phép nested placeholder trong path (resolve placeholder trước, rồi include)
- File không tồn tại → render error, KHÔNG silent fail
- Recursive include allowed nhưng max 3 levels deep

### `{{IF:condition}}...{{ENDIF}}` — Conditional block

```
{{IF:COMPANY.ENTITY_TYPE == "S-Corp"}}
⚠️ Owner-employee MUST take W-2 reasonable comp BEFORE distributions.
{{ENDIF}}

{{IF:OPERATIONS.STATE_OF_OPERATION == "CA"}}
CA Franchise Tax minimum $800/year due April 15.
{{ENDIF}}
```

**Supported operators:**
- `==` (equals)
- `!=` (not equals)
- `IN` (value in list, vd: `OPERATIONS.STATE_OF_OPERATION IN ["CA","NY","TX"]`)
- `EXISTS` (field has non-null value, vd: `COMPANY.EIN EXISTS`)
- `NOT ... EXISTS` (field is null/missing, vd: `NOT COMPANY.EIN EXISTS`)

**Array indexing in EXISTS check:**
- `BANK_ACCOUNTS.0 EXISTS` — true nếu array có ít nhất 1 element
- `EMPLOYEES.0 EXISTS` — true nếu có employee nào đã configured
- Use này để conditional render entire sections dựa trên có data không

### `{{FORMAT:field|formatter}}` — Apply formatter

```
{{FORMAT:APPROVAL_THRESHOLDS.TIER_1_MAX|currency}}     → $1,000.00
{{FORMAT:FISCAL_YEAR.START_DATE|long_date}}            → January 1, 2026
{{FORMAT:COMPANY.LEGAL_NAME|upper}}                    → ACME SERVICE GROUP
{{FORMAT:COMPANY.ENTITY_TYPE|tax_form}}                → Form 1120-S (S-Corp)
```

**Built-in formatters:**
- `currency` → `$X,XXX.XX`
- `long_date` → `January 1, 2026`
- `short_date` → `01/01/2026`
- `iso_date` → `2026-01-01`
- `upper` → UPPERCASE
- `lower` → lowercase
- `tax_form` → tự suy ra tax form từ entity type
- `state_name` → `CA` → `California`

### `{{COMPUTED:expression}}` — Computed value

```
{{COMPUTED:DAYS_INTO_FY}}              → 112
{{COMPUTED:CURRENT_QUARTER}}           → Q2
{{COMPUTED:NEXT_TAX_DEADLINE}}         → June 15, 2026 (Q2 estimated tax)
{{COMPUTED:FY_PROGRESS_PCT}}           → 30.7%
```

**Built-in computed values:**

*Date/time:*
- `TODAY` — current date ISO format
- `DAYS_INTO_FY` — days từ FY start đến today
- `DAYS_REMAINING_IN_FY` — days từ today đến FY end
- `CURRENT_QUARTER` — Q1/Q2/Q3/Q4 dựa trên today
- `FY_PROGRESS_PCT` — % FY đã qua
- `PRIOR_FY` — `FISCAL_YEAR.YEAR - 1` (vd: 2025 nếu FY=2026)
- `NEXT_TAX_DEADLINE` — deadline gần nhất, tùy entity + state

*Aggregations từ array fields:*
- `BANK_ACCOUNTS_COUNT` — `len(bank_accounts)`
- `BANK_ACCOUNTS_TABLE` — markdown table render từ bank_accounts array
- `EMPLOYEES_COUNT` — `len(employees)` (chỉ count `is_active=true`)
- `EMPLOYEES_TABLE` — markdown table render từ employees array
- `CONTRACTORS_COUNT` — `len(contractors)` (chỉ count `is_active=true`)
- `CONTRACTORS_TABLE` — markdown table render từ contractors array

> **Note:** AI Agent render computed values dựa trên data trong config. Nếu array rỗng, table render thành "_(none configured yet)_" hoặc skip block dùng IF guard.

---

## 3. RESOLUTION ORDER

Khi render 1 template file, AI Agent xử lý theo thứ tự:

1. **Pass 1:** Resolve `{{INCLUDE:...}}` → expand file content
2. **Pass 2:** Resolve nested `{{...}}` trong INCLUDE paths
3. **Pass 3:** Evaluate `{{IF:...}}{{ENDIF}}` blocks → keep or remove
4. **Pass 4:** Resolve `{{COMPUTED:...}}` → calculate values
5. **Pass 5:** Resolve `{{FORMAT:...|...}}` → apply formatters
6. **Pass 6:** Resolve plain `{{SECTION.FIELD}}` → simple substitution
7. **Pass 7:** Validate — không còn `{{...}}` nào chưa resolve

---

## 4. ERROR HANDLING

| Scenario | Behavior |
|----------|----------|
| Field not found in config | Render error, abort. KHÔNG để placeholder lộ trong output. |
| Field is `null` | Render literal `(not set)` hoặc skip nếu trong IF block |
| INCLUDE file not found | Render error, abort. |
| IF condition syntax invalid | Render error, abort. |
| COMPUTED expression unknown | Render error, abort. |
| FORMAT formatter unknown | Render error, abort. |
| Circular INCLUDE detected | Render error, abort. |

**Nguyên tắc:** Fail loud, không silent. Output không được chứa `{{...}}` chưa resolve.

---

## 5. EXAMPLES — Template fragments

### Example A: Header
```markdown
# {{COMPANY.LEGAL_NAME}} — AI Accounting Controller Workspace

**Last Updated:** {{COMPUTED:TODAY|long_date}}
**Fiscal Year:** FY{{FISCAL_YEAR.YEAR}}
**Base Currency:** {{OPERATIONS.BASE_CURRENCY}}
**Entity Type:** {{COMPANY.ENTITY_TYPE}}
**State:** {{FORMAT:OPERATIONS.STATE_OF_OPERATION|state_name}}
```

→ Renders to:
```markdown
# Acme Service Group — AI Accounting Controller Workspace

**Last Updated:** April 22, 2026
**Fiscal Year:** FY2026
**Base Currency:** USD
**Entity Type:** S-Corp
**State:** California
```

### Example B: Conditional content
```markdown
## Tax Forms Required

{{IF:COMPANY.ENTITY_TYPE == "S-Corp"}}
- **Form 1120-S** — due March 15
- **Schedule K-1** — issued to shareholders
{{ENDIF}}

{{IF:COMPANY.ENTITY_TYPE == "C-Corp"}}
- **Form 1120** — due April 15
{{ENDIF}}

{{IF:COMPANY.ENTITY_TYPE IN ["LLC-multi", "Partnership"]}}
- **Form 1065** — due March 15
- **Schedule K-1** — issued to partners
{{ENDIF}}
```

### Example C: State-specific include
```markdown
## State Tax Obligations

{{INCLUDE:_MODULES/state/{{OPERATIONS.STATE_OF_OPERATION}}.md}}
```

---

## 6. AI AGENT RENDER PROTOCOL

Khi AI Agent được giao task "render instance":

1. Read `_CONFIG/_BUSINESS_CONFIG.json` (hoặc path user chỉ định)
2. Validate JSON theo `_BUSINESS_CONFIG.schema.json`
3. Với mỗi file `_CORE/*.md.template`:
   a. Read template content
   b. Apply 7-pass resolution (Section 3)
   c. Write output → `_INSTANCES/{{INSTANCE_ID}}/[filename].md` (drop `.template` suffix)
4. Validate: grep output files cho `{{` — phải = 0 matches
5. Report: list of files generated + diff summary

---

## 7. RESERVED IDENTIFIERS

KHÔNG dùng các identifier sau làm field name trong config (collide với directives):

- `INCLUDE`, `IF`, `ENDIF`, `ELSE`, `FORMAT`, `COMPUTED`
- `TODAY`, `NOW`
- Bất kỳ field bắt đầu bằng `_` (reserved cho metadata)

---

## 8. VERSIONING

- **1.0.0** (2026-04-22) — Initial spec, 6 directive types
- Future: nếu thêm directive mới → bump minor (1.1.0)
- Nếu thay đổi syntax breaking → bump major (2.0.0) + migration guide

---

**Prepared by:** AI Accounting Controller — Template by mikenguyen.dev@gmail.com
**For:** Template render engine + AI Agent contributors
