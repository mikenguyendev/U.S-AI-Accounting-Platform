# 🔧 RENDER PROTOCOL — Template Engine for AI Agent

> **Mục đích:** Hướng dẫn AI Agent đọc `_BUSINESS_CONFIG.json` + `.md.template` files → output instance file đã resolved hoàn toàn.
>
> **Không phải runtime engine** — protocol này được AI Agent thực thi bằng cách dùng Read + Write tools native (không cần Python/Node script).

**Version:** 1.0.0
**Last Updated:** 2026-04-22
**Companion docs:** [_CONFIG/PLACEHOLDER_CONVENTION.md](../_CONFIG/PLACEHOLDER_CONVENTION.md), [_CONFIG/_BUSINESS_CONFIG.schema.json](../_CONFIG/_BUSINESS_CONFIG.schema.json)

---

## 🎯 KHI NÀO INVOKE PROTOCOL NÀY

AI Agent thực thi render khi:
1. **User onboard business mới** — vừa tạo xong `_BUSINESS_CONFIG.json` từ wizard
2. **User update config** — thay đổi field trong JSON, cần re-render workspace
3. **Template upgrade** — phiên bản template mới, cần re-render existing instances
4. **Manual test** — verify template + config compatible

User trigger: "Render workspace từ config", "Generate workspace cho [my company]", "Refresh templates"

---

## 📋 INPUTS & OUTPUTS

### Inputs (required)
1. **Config file path** — vd: `_CONFIG/_BUSINESS_CONFIG.example.json`
2. **Template directory** — `_CORE/`
3. **Output directory** — `_INSTANCES/{instance_id}/`

### Inputs (optional)
- **Module overrides** — nếu user có custom entity/state module
- **Skip list** — files không cần render

### Outputs
- 5 file MD trong instance folder (drop `.template` suffix)
- Render report: list files generated + any warnings/unresolved
- Updated `_INSTANCES/{instance_id}/_BUSINESS_CONFIG.json` (copy của config dùng để render)

---

## 🔄 PROTOCOL STEP-BY-STEP

### STEP 1: Load và Validate Config

```
1.1 Read config file (Read tool)
1.2 Parse as JSON (mental parse, không cần lib)
1.3 Validate against schema:
    - Required fields present? (schema_version, company, operations, fiscal_year, owner, approval_thresholds, compliance_status)
    - Enum values valid? (entity_type, state, industry, software, language)
    - Format constraints? (EIN regex, ZIP regex, date format)
1.4 If invalid → STOP, report errors to user
1.5 Extract instance_id (or derive từ company.legal_name → snake_case)
```

**Validation errors to flag:**
- Missing required field
- Enum value not in allowed list
- EIN format wrong (should be `XX-XXXXXXX`)
- State code not 2 letters uppercase
- Date not ISO format

### STEP 2: Prepare Output Directory

```
2.1 Compute output path: _INSTANCES/{instance_id}/
2.2 If folder exists:
    - Ask user: overwrite? archive existing? abort?
    - If overwrite → mkdir (Bash: `mkdir -p`)
    - If archive → move existing to _ARCHIVE/{instance_id}_{timestamp}/
2.3 If folder doesn't exist → create
2.4 Copy config file vào instance folder (sẽ là source of truth của instance)
```

### STEP 3: Build Computed Values Dictionary

Trước khi render, tính sẵn tất cả COMPUTED values:

```
TODAY = current date ISO (vd: 2026-04-22)
PRIOR_FY = fiscal_year.year - 1
DAYS_INTO_FY = days từ fiscal_year.start_date đến TODAY
DAYS_REMAINING_IN_FY = days từ TODAY đến fiscal_year.end_date
CURRENT_QUARTER = derive từ TODAY và FY start (Q1/Q2/Q3/Q4)
FY_PROGRESS_PCT = (DAYS_INTO_FY / 365) * 100, format "X.X%"
NEXT_TAX_DEADLINE = derive từ entity + state modules

BANK_ACCOUNTS_COUNT = len(bank_accounts)
EMPLOYEES_COUNT = len(employees where is_active=true)
CONTRACTORS_COUNT = len(contractors where is_active=true)

BANK_ACCOUNTS_TABLE = render markdown table từ bank_accounts array
EMPLOYEES_TABLE = render markdown table từ employees array
CONTRACTORS_TABLE = render markdown table từ contractors array
```

**Markdown table format example:**
```
| GL # | Type | Bank | Last 4 | Purpose |
|------|------|------|--------|---------|
| 1010 | Checking | Chase | 1234 | Operating |
| 1020 | Savings | Chase | 5678 | Tax Reserve |
```

Nếu array rỗng → render `_(none configured yet)_`

### STEP 4: Process Each Template (7-Pass Resolution)

Cho mỗi file trong `_CORE/*.md.template`:

#### Pass 1: Resolve INCLUDE directives
```
Tìm pattern: {{INCLUDE:path[#section]}}
Cho mỗi match:
  1. Resolve nested {{...}} trong path trước
     vd: {{INCLUDE:_MODULES/state/{{OPERATIONS.STATE_OF_OPERATION}}.md#deadlines}}
        → {{INCLUDE:_MODULES/state/CA.md#deadlines}}
  2. Read file at path
  3. If has #section anchor → extract section content (markdown header + body until next same-level header)
  4. Substitute INCLUDE directive với content
  5. Track depth — max 3 levels nested INCLUDE
```

**Section extraction rule:**
- `#section-id` matches `## section-id` heading (case-insensitive, strip dashes/spaces match)
- Include từ heading đến before next `##` of same level
- Strip the heading itself from output (chỉ include body)

#### Pass 2: Resolve placeholders trong INCLUDE'd content
After Pass 1, INCLUDE'd content có thể chứa thêm `{{...}}` từ module file. Loop Pass 1 lại nếu cần.

#### Pass 3: Evaluate IF/ENDIF blocks
```
Tìm pattern: {{IF:condition}}...{{ENDIF}}
Cho mỗi match:
  1. Parse condition:
     - Field path (vd: COMPANY.ENTITY_TYPE)
     - Operator (==, !=, IN, EXISTS, NOT EXISTS)
     - Value (literal string, array, or EXISTS keyword)
  2. Lookup field value in config
  3. Evaluate:
     - == "S-Corp" → true if value == "S-Corp"
     - IN ["CA","NY"] → true if value in array
     - EXISTS → true if value not null and not empty string
     - NOT ... EXISTS → opposite
  4. If true → keep block content, remove {{IF}}/{{ENDIF}} tags
  5. If false → remove entire block including tags
```

#### Pass 4: Resolve COMPUTED values
```
Tìm pattern: {{COMPUTED:NAME}} hoặc {{COMPUTED:NAME|formatter}}
Lookup NAME trong dictionary built ở Step 3
Substitute value
```

#### Pass 5: Resolve FORMAT directives
```
Tìm pattern: {{FORMAT:field|formatter}}
1. Resolve field value
2. Apply formatter:
   - currency → $X,XXX.XX (use commas, 2 decimals)
   - long_date → "January 1, 2026"
   - short_date → "01/01/2026"
   - iso_date → "2026-01-01"
   - upper → UPPERCASE
   - lower → lowercase
   - tax_form → entity_type → form name (xem table dưới)
   - state_name → state code → full state name (xem table dưới)
3. Substitute
```

#### Pass 6: Resolve plain field placeholders
```
Tìm pattern: {{SECTION.FIELD}} hoặc {{SECTION.SUBSECTION.FIELD}}
Lookup value trong config
Substitute
Nếu null → render literal "(not set)"
```

#### Pass 7: Validation
```
Grep output for "{{"
Nếu match → render error, list unresolved placeholders
Nếu = 0 → success
```

### STEP 5: Write Output

```
5.1 Write rendered content to _INSTANCES/{instance_id}/{filename}.md (drop .template)
5.2 Verify file written successfully
5.3 Add to render log
```

### STEP 6: Generate Render Report

Output to user:
```
✅ Render Complete: {instance_id}

Files generated:
  - _INSTANCES/{instance_id}/README.md (~8 KB)
  - _INSTANCES/{instance_id}/AI_AGENT_MEMORY.md (~3 KB)
  - _INSTANCES/{instance_id}/COMPANY_PROFILE.md (~12 KB)
  - _INSTANCES/{instance_id}/FORM_SCHEMA.md (~16 KB)
  - _INSTANCES/{instance_id}/USE_CASES_GUIDE.md (~18 KB)

Config used: _CONFIG/_BUSINESS_CONFIG.json

Warnings:
  - (none)

Next steps:
  - Review rendered files
  - If satisfied, create data folders (00_Archive, 01_AP-AR_Management, etc.) trong instance folder
```

---

## 📚 LOOKUP TABLES

### Tax Form by Entity Type (`tax_form` formatter)

| Entity Type | Tax Form |
|-------------|----------|
| C-Corp | Form 1120 |
| S-Corp | Form 1120-S |
| LLC-single | Schedule C (on owner's 1040) |
| LLC-multi | Form 1065 |
| Partnership | Form 1065 |
| Sole-Prop | Schedule C (on owner's 1040) |

### State Code → Full Name (`state_name` formatter)

```
AL=Alabama  AK=Alaska  AZ=Arizona  AR=Arkansas  CA=California
CO=Colorado  CT=Connecticut  DE=Delaware  FL=Florida  GA=Georgia
HI=Hawaii  ID=Idaho  IL=Illinois  IN=Indiana  IA=Iowa
KS=Kansas  KY=Kentucky  LA=Louisiana  ME=Maine  MD=Maryland
MA=Massachusetts  MI=Michigan  MN=Minnesota  MS=Mississippi  MO=Missouri
MT=Montana  NE=Nebraska  NV=Nevada  NH=New Hampshire  NJ=New Jersey
NM=New Mexico  NY=New York  NC=North Carolina  ND=North Dakota  OH=Ohio
OK=Oklahoma  OR=Oregon  PA=Pennsylvania  RI=Rhode Island  SC=South Carolina
SD=South Dakota  TN=Tennessee  TX=Texas  UT=Utah  VT=Vermont
VA=Virginia  WA=Washington  WV=West Virginia  WI=Wisconsin  WY=Wyoming  DC=District of Columbia
```

### Currency Formatter

```
Input: number (vd: 1234.5, 1000, 1234567.89)
Output: $X,XXX.XX
  - Always 2 decimals
  - Commas at thousands
  - $ prefix
  - vd: 1234.5 → $1,234.50, 1000 → $1,000.00, 1234567.89 → $1,234,567.89
```

### Date Formatters

```
Input: ISO date string "2026-04-22"
- iso_date → "2026-04-22"
- short_date → "04/22/2026"
- long_date → "April 22, 2026"
```

---

## ⚠️ ERROR HANDLING

### Fail-Loud Principle
**KHÔNG silent fail.** Mọi lỗi đều phải báo cho user.

### Error Types

| Error | Action |
|-------|--------|
| Config invalid (schema violation) | STOP, list violations, ask user fix config |
| Required INCLUDE file missing | STOP, list missing files, suggest creating Phase 2 modules |
| Section anchor not found in INCLUDE'd file | WARN, render `_(section "X" not found in {file})_`, continue |
| Field referenced but not in config | If has default → use default. Else → STOP, ask user to add field |
| IF condition syntax invalid | STOP, show offending block, fix |
| FORMAT formatter unknown | STOP, list available formatters |
| COMPUTED value unknown | STOP, list available computed values |
| Output directory exists | ASK user (overwrite/archive/abort) |
| Circular INCLUDE detected | STOP, show cycle, fix templates |

### Partial Render Mode

Trong Phase 1 (entity/state modules chưa có), AI Agent có thể:
1. **Strict mode** (default): Fail nếu INCLUDE missing
2. **Lenient mode** (Phase 1 only): Replace missing INCLUDE bằng marker `<!-- PHASE 2 PENDING: {include path} -->` và continue

User trigger lenient: "Render với phase-2-pending mode"

---

## 🧪 TEST MATRIX

Khi update template hoặc convention, run test cases:

### Test Case 1: Minimal Config
- Input: Bare minimum config (chỉ required fields)
- Expected: Render succeed, optional sections show "(not set)" hoặc skip

### Test Case 2: Full Config (Demo)
- Input: `_BUSINESS_CONFIG.example.json` (Acme Service Group demo)
- Expected: All 5 templates render, optional sections populated

### Test Case 3: Different Entity Types
- Input: 6 configs với 6 entity types
- Expected: Entity-specific IF blocks render correctly cho mỗi loại

### Test Case 4: Different States
- Input: 10 configs với 10 different states
- Expected: State INCLUDE resolve correctly

### Test Case 5: Empty Arrays
- Input: bank_accounts=[], employees=[], contractors=[]
- Expected: Sections render với "(none)" message, không crash

### Test Case 6: Edge Dates
- Input: TODAY = FY start date / FY end date / outside FY
- Expected: COMPUTED values handle gracefully

---

## 🔄 IDEMPOTENCY

Render protocol PHẢI idempotent: chạy 2 lần với same input → same output.

**Caveats:**
- COMPUTED values phụ thuộc TODAY → ngày khác thì output khác
- Random/uuid values KHÔNG được dùng trong protocol

---

## 📝 EXAMPLES

### Example 1: Render demo instance

```
User: "Render workspace từ _CONFIG/_BUSINESS_CONFIG.example.json"

AI Agent:
1. Read _CONFIG/_BUSINESS_CONFIG.example.json
2. Validate (all good)
3. Compute: TODAY=2026-04-22, CURRENT_QUARTER=Q2, PRIOR_FY=2025, etc.
4. Output dir: _INSTANCES/{instance_id}/ (create — instance_id từ config)
5. Render 5 templates
6. Report: 5 files generated, 0 warnings
```

### Example 2: Render with missing module (Phase 1 scenario)

```
Template references: {{INCLUDE:_MODULES/state/CA.md#deadlines}}
File doesn't exist (Phase 2 chưa làm)

Strict mode: STOP, "Module _MODULES/state/CA.md not found"
Lenient mode: Replace với "<!-- PHASE 2 PENDING: state/CA.md#deadlines -->"
```

### Example 3: Re-render after config update

```
User: "Tôi vừa update EIN trong config, re-render workspace"

AI Agent:
1. Read updated config
2. Detect existing _INSTANCES/{instance_id}/
3. Ask: overwrite? (default yes vì same instance_id)
4. Re-render all 5 files
5. Report diff: "EIN updated in 3 files"
```

---

## 🔐 SAFETY RULES

1. **NEVER write outside `_INSTANCES/{instance_id}/`** trong protocol này
2. **NEVER modify** `_CORE/*.md.template` files khi rendering
3. **NEVER modify** `_CONFIG/_BUSINESS_CONFIG.json` khi rendering (only read)
4. **NEVER auto-overwrite** existing instance — luôn confirm với user
5. **NEVER skip validation** — even nếu user request "quick render"

---

**Prepared by:** AI Accounting Controller — Template by mikenguyen.dev@gmail.com
**For:** AI Agent contributors + template maintainers
