# 📐 STATE MODULE SCHEMA

> **Mục đích:** Định nghĩa structure bắt buộc cho mỗi state module (`_MODULES/state/{STATE}.md`).
>
> Mọi state module PHẢI có đầy đủ 11 sections để render từ templates không bị lỗi missing INCLUDE.

**Version:** 1.0.0
**Last Updated:** 2026-04-22

---

## REQUIRED SECTIONS

Mỗi state module phải có đúng 11 sections, theo thứ tự, với heading `## section-id`:

### 1. `## tax-obligations`
- Master table tax obligations cho state
- Columns: Item | Rate/Amount | Authority | Deadline
- Bao gồm: franchise/income tax, sales tax, withholding, unemployment, disability (nếu có)

### 2. `## deadlines`
- Comprehensive markdown table state deadlines
- Columns: Date | Action | Form
- Bao gồm cả entity-level và payroll deadlines

### 3. `## upcoming-deadlines`
- Rolling 12-month preview state-specific
- Format: markdown table Date | Action

### 4. `## critical-reminders`
- Bullet list ⚠️ items state-specific
- Cover: minimum taxes, mandatory insurances, special compliance

### 5. `## flag-conditions`
- AI Agent warnings cho state-specific violations
- Format: bullet list ⚠️

### 6. `## validation-rules`
- State-specific validation checks
- Cover: tax sourcing, exemptions, reciprocity, minimum wage

### 7. `## sales-tax`
- Sales tax authority + rates
- What's taxable / not taxable
- Filing frequency rules
- Permit requirements

### 8. `## estimated-tax`
- State entity-level estimated tax rules
- Quarterly schedule (some states differ from federal)
- Safe harbor rules
- Pass-through entity considerations

### 9. `## withholding-form`
- State withholding form name (vd: DE-4 cho CA, IT-2104 cho NY)
- Companion forms required at hire
- Filing rules

### 10. `## withholding-tables`
- Withholding calculation method
- Brackets (or pointer to state pub)
- Tools/calculators
- Special situations (bonuses, supplemental wages)

### 11. `## payroll-taxes`
- Employer-side payroll taxes table
- Wage bases
- Reporting forms
- E-file thresholds

---

## OPTIONAL SECTIONS

- `## entity-specific-tax` — Per entity type breakdown nếu state có rules khác nhau
- `## local-taxes` — City/county-specific (vd: NYC additional tax)
- `## reciprocity` — Reciprocity agreements với states khác
- `## special-programs` — State-specific programs (vd: CalSavers, NY Paid Family Leave)

---

## CONTENT STANDARDS

### Tax authority full names
- CA: Franchise Tax Board (FTB), CDTFA, EDD
- NY: Department of Taxation and Finance, Department of Labor
- TX: Texas Comptroller, Texas Workforce Commission
- ... (use official state agency names)

### Rates & dates
- ALWAYS year-stamp rates (vd: "$800 (2026)")
- Distinguish state min wage vs city min wage
- Note effective dates for new laws

### Forms
- Use exact state form name (vd: "Form 100-S" cho CA, "CT-3-S" cho NY)
- Include filing frequency (annual, quarterly, monthly)

### No-tax states
States without state income tax (TX, FL, WA, NV, SD, AK, WY, TN, NH cho some income):
- `## tax-obligations` còn lại các taxes khác (sales, payroll, franchise)
- `## withholding-tables` ghi rõ "No state income tax withholding"
- Vẫn phải có 11 sections (các sections không applicable ghi "N/A — no state income tax")

---

## TEMPLATE FOR NEW STATE MODULE

```markdown
# {State Name} ({CODE}) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/{CODE}.md#section-id}}` directives.**

**State:** {Full State Name}
**Tax Authority:** {Primary agencies}
**Last Updated:** {date}

---

## tax-obligations

[Markdown table]

---

## deadlines

[Markdown table]

---

## upcoming-deadlines

[Markdown table]

---

## critical-reminders

[Bullet list ⚠️]

---

## flag-conditions

[Bullet list ⚠️]

---

## validation-rules

[Bullet list]

---

## sales-tax

[Detailed sales tax info]

---

## estimated-tax

[Quarterly schedule + rules]

---

## withholding-form

[Form name + companion forms]

---

## withholding-tables

[Calculation method + tools]

---

## payroll-taxes

[Employer-side taxes table]
```

---

## VALIDATION CHECKLIST

Trước khi commit state module mới:

- [ ] All 11 required sections present
- [ ] Heading format `## section-id` exactly
- [ ] State agency names spelled correctly
- [ ] All rates year-stamped (2026)
- [ ] Form names match state's official naming
- [ ] No-tax-state cases handled gracefully (N/A vs missing)
- [ ] No customer-specific data
- [ ] Major city local taxes mentioned (vd: NYC, Chicago, San Francisco)

---

## STATE PRIORITY LIST (v1.0.0)

| Priority | State | Code | Status | % US SMB |
|:--------:|-------|:----:|:------:|---------:|
| 1 | California | CA | ✅ Done | ~12% |
| 2 | Texas | TX | 🟡 Phase 2 | ~9% |
| 3 | New York | NY | 🟡 Phase 2 | ~7% |
| 4 | Florida | FL | 🟡 Phase 2 | ~7% |
| 5 | Illinois | IL | 🟡 Phase 2 | ~5% |
| 6 | Pennsylvania | PA | 🟡 Phase 2.5 | ~5% |
| 7 | Ohio | OH | 🟡 Phase 2.5 | ~4% |
| 8 | Georgia | GA | 🟡 Phase 2 | ~4% |
| 9 | North Carolina | NC | 🟡 Phase 2.5 | ~4% |
| 10 | Michigan | MI | 🟡 Phase 2.5 | ~3% |
| 11 | New Jersey | NJ | 🟡 Phase 2 | ~3% |
| 12 | Virginia | VA | 🟡 Phase 2.5 | ~3% |
| 13 | Washington | WA | 🟡 Phase 2 | ~3% |
| 14 | Massachusetts | MA | 🟡 Phase 2 | ~3% |
| 15 | Delaware | DE | 🟡 Phase 2 | <1% (but high incorp) |

**Coverage:** Top 10 states = ~60% of US SMBs. Phase 2 covers top 10 + DE.

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
