# 📐 ENTITY MODULE SCHEMA

> **Mục đích:** Định nghĩa structure bắt buộc cho mỗi entity module (`_MODULES/entity/{entity_type}.md`).
>
> Mọi entity module PHẢI có đầy đủ 9 sections dưới đây để render từ templates không bị lỗi missing INCLUDE.

**Version:** 1.0.0
**Last Updated:** 2026-04-22

---

## REQUIRED SECTIONS

Mỗi entity module phải có đúng 9 sections, theo thứ tự, với heading `## section-id` (lowercase, dash-separated):

### 1. `## federal-deadlines`
- Markdown table của tất cả federal tax deadlines cho entity type này
- Columns: Deadline | Form | Action
- Bao gồm cả entity-level VÀ owner/shareholder-level (nếu pass-through)

### 2. `## federal-obligations`
- Liệt kê các federal returns và obligations
- Subsections: Entity-level, Owner-level (nếu áp dụng)
- Format: bullet list với form name + brief description

### 3. `## critical-rules`
- Eligibility requirements (max shareholders, foreign restrictions, etc.)
- Tax election procedures
- Distribution/draw rules
- Special considerations cụ thể cho entity type

### 4. `## upcoming-deadlines`
- Rolling 12-month deadline preview
- Format: markdown table Date | Action
- Note để user verify against `{{COMPUTED:TODAY}}`

### 5. `## owner-compensation`
- Detailed rules cho owner compensation
- Cách phân biệt salary vs draw vs distribution vs guaranteed payment
- Tax implications (FICA, SE tax, etc.)
- Documentation requirements
- Audit risk flags

### 6. `## owner-comp-protocol`
- AI Agent protocol khi xử lý form `owner-comp`
- Step-by-step what to do
- Validation checks
- File save location
- File naming convention

### 7. `## flag-conditions`
- List các situations AI Agent phải warn user
- Format: bullet list với ⚠️ prefix
- Should cover: entity rule violations, audit triggers, deadline misses

### 8. `## validation-rules`
- Entity-specific validation checks AI Agent run trên transactions
- Format: bullet list
- Cover: distribution rules, shareholder eligibility, etc.

### 9. `## estimated-tax`
- Whether entity-level estimated tax required (vs pass-through to owner)
- Federal estimated tax rules cho entity
- Owner-level estimated tax considerations
- Safe harbor rules
- AI Agent protocol khi xử lý form `estimated-tax`

---

## OPTIONAL SECTIONS

Có thể add additional sections nếu entity type cần (vd: `## conversion-rules` cho S-Corp converted from C-Corp). Nhưng KHÔNG được skip 9 required sections.

---

## CONTENT STANDARDS

### Tone
- Business professional
- Reference Forms by official IRS name (Form 1120-S, not "S-corp form")
- Cite IRS publications when applicable (Pub 463, Pub 535, etc.)

### Numbers
- Annual limits: ALWAYS include year (vd: "$168,600 (2026)")
- Tax rates: Include effective date
- Penalties: Include calculation basis

### Bilingual
- Section content có thể mix EN (technical terms) + VN (explanations)
- Form names KHÔNG dịch sang VN (Form 1120 vẫn là Form 1120, không phải "Mẫu 1120")

### Examples
- Khi giải thích complex rule, cho 1 numeric example
- Format: indented code block với calculation breakdown

---

## TEMPLATE FOR NEW ENTITY MODULE

```markdown
# {Entity Type} — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/{Entity Type}.md#section-id}}` directives.**

**Entity Type:** {Full Entity Name}
**Tax Treatment:** {Pass-through / Double taxation / Disregarded}
**Primary Tax Form:** {Form name}
**Last Updated:** {date}

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| ... | ... | ... |

---

## federal-obligations

**Entity-level returns:** ...
**Owner-level (if pass-through):** ...

---

## critical-rules

### Eligibility
- ...

### Tax Election
- ...

### Distribution/Draw Rules
- ...

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| ... | ... |

---

## owner-compensation

⚠️ **{ENTITY-SPECIFIC HEADER}**

[Detailed rules here]

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form:**

1. ...
2. ...

**File naming:** `YYYYMMDD_OwnerComp_Analysis_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ ...
- ⚠️ ...

---

## validation-rules

### {Entity Type} Specific Validation

- ...

---

## estimated-tax

**{Entity-level vs Pass-through structure explanation}**

[Rules + AI protocol]
```

---

## VALIDATION CHECKLIST

Trước khi commit entity module mới, verify:

- [ ] All 9 required sections present
- [ ] Heading format `## section-id` exactly (lowercase, dash)
- [ ] No leading whitespace before headings
- [ ] No customer-specific data (white-label test)
- [ ] All Form names spelled correctly per IRS standards
- [ ] All deadlines current cho 2026 tax year
- [ ] Numeric examples balance correctly
- [ ] Bilingual consistency (English form names, VN explanations)

---

## SUPPORTED ENTITY TYPES (v1.0.0)

| Entity Type | Module File | Status |
|-------------|-------------|:------:|
| C-Corp | `C-Corp.md` | 🟡 Phase 2 |
| S-Corp | `S-Corp.md` | ✅ Done |
| LLC-single | `LLC-single.md` | 🟡 Phase 2 |
| LLC-multi | `LLC-multi.md` | 🟡 Phase 2 |
| Partnership | `Partnership.md` | 🟡 Phase 2 |
| Sole-Prop | `Sole-Prop.md` | 🟡 Phase 2 |

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
