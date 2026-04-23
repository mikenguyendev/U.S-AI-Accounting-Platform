# 📓 Journal Entry Template — Setup Guide

> Template cho post journal entries với auto-balance check.

**File:** `JournalEntry.csv`
**Update cadence:** Per transaction
**Storage:** `_INSTANCES/{instance_id}/02_General_Ledger/Journal_Entries/FY{year}_Q{quarter}/`

---

## 📋 STRUCTURE

| Column | Type | Required | Notes |
|--------|------|:--------:|-------|
| JE_Number | Text | ✅ | Format: JE-YYYY-XXX |
| Date | Date | ✅ | mm/dd/yyyy or yyyy-mm-dd |
| Account_Number | Text | ✅ | From COA (4-5 digit) |
| Account_Name | Text | ✅ | From COA |
| Description | Text | ✅ | Brief explanation |
| Debit | Currency | One of D/C | $ amount |
| Credit | Currency | One of D/C | $ amount |
| Reference | Text | Optional | Invoice#/Doc ref |
| Posted_By | Text | ✅ | Preparer name |
| Approved_By | Text | If >threshold | Approver name |
| Status | Enum | ✅ | Posted / Pending / Reversed |

---

## 🔧 FORMULAS TO ADD

### After importing CSV to Excel/Sheets:

**1. Total Debits (cell F100, adjust to last data row)**
```excel
=SUM(F2:F99)
```

**2. Total Credits (cell G100)**
```excel
=SUM(G2:G99)
```

**3. Balance Check (cell I100)**
```excel
=IF(F100=G100,"✅ BALANCED","⚠️ OUT OF BALANCE BY "&TEXT(F100-G100,"$#,##0.00"))
```

**4. JE-level subtotals (use SUMIFS for per-JE balance):**
```excel
JE Debit Total: =SUMIFS(F:F,A:A,"JE-2026-001")
JE Credit Total: =SUMIFS(G:G,A:A,"JE-2026-001")
JE Balance:     =IF(SUMIFS(F:F,A:A,"JE-2026-001")=SUMIFS(G:G,A:A,"JE-2026-001"),"OK","NOT BALANCED")
```

**5. Account validation (Data Validation):**
```excel
Data → Data Validation → List → Source: =COA!$A$2:$A$200
```

---

## 🎨 CONDITIONAL FORMATTING

### Highlight unbalanced JEs
- Select column I (balance check column)
- Conditional Formatting → Text contains "OUT OF BALANCE" → Red fill

### Highlight pending entries
- Select column K (Status)
- Conditional Formatting → Equal to "Pending" → Yellow fill

### Highlight reversed entries
- Conditional Formatting → Equal to "Reversed" → Gray fill, strikethrough

### Highlight large amounts (review trigger)
- Select columns F and G
- Conditional Formatting → Greater than $10,000 → Orange border

---

## ✅ VALIDATION RULES

1. **Each JE must balance:** Sum(Debit) = Sum(Credit) per JE_Number
2. **No empty Debit + Credit:** Each row must have either Debit OR Credit (not both, not neither)
3. **Date within fiscal period:** Must be between FY start_date and end_date
4. **Account_Number must exist in COA**
5. **Status enum:** Posted / Pending / Reversed only
6. **Approval required:** If row total > Conservative tier threshold, Approved_By must be filled

---

## 📝 SAMPLE DATA EXPLAINED

### JE-2026-001: Payroll posting (5 lines)
```
Dr. Salaries and Wages     $5,000.00
    Cr. Fed Income Tax WH        $750.00
    Cr. FICA WH (Employee)       $382.50
    Cr. State Income Tax WH      $200.00
    Cr. Cash (Net pay)         $3,667.50
                              ─────────
                Total Cr:    $5,000.00 ✓
```

### JE-2026-002: Software purchase on credit card (2 lines)
```
Dr. Software Subscriptions  $599.88
    Cr. Credit Card Payable     $599.88 ✓
```

---

## 🔄 FILING WORKFLOW

1. AI Agent receives transaction request (form input or photo)
2. Validates per Phase 5 protocol (Extract → Confirm → Execute)
3. Adds row(s) to template
4. Verifies balance check
5. Saves with name: `YYYYMMDD_JE-XXX_[Description].xlsx`
6. Stores in: `02_General_Ledger/Journal_Entries/FY{year}_Q{quarter}/`
7. Updates Trial Balance template (Pull from JE log)

---

## ⚠️ COMMON PITFALLS

1. **JE numbers reused** — Sequential by year (JE-2026-001, JE-2026-002, ...)
2. **Approval skipped for large entries** — Review threshold per Conservative/Moderate/Aggressive
3. **Reversing entries on wrong date** — Reversing JE = first day of NEXT period
4. **Posted then deleted** — NEVER delete posted entries; use reversing JE instead
5. **Mixing periods** — One JE should be one date (split if multi-period)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
