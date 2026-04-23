# 💰 AR Aging Template — Setup Guide

> Track customer receivables by age bucket. Priority collection tool.

**File:** `AR_Aging.csv`
**Update cadence:** Weekly (minimum), daily during active collections
**Storage:** `_INSTANCES/{instance_id}/01_AP-AR_Management/Accounts_Receivable/Aging_Reports/`

---

## 📋 STRUCTURE

| Column | Type | Notes |
|--------|------|-------|
| Customer_ID | Text | Internal customer code |
| Customer_Name | Text | Legal entity name |
| Invoice_Number | Text | Unique invoice ID |
| Invoice_Date | Date | When invoice issued |
| Due_Date | Date | When payment due |
| Invoice_Amount | Currency | Total invoiced |
| Amount_Paid | Currency | Cumulative payments received |
| Balance_Due | Formula | Invoice_Amount - Amount_Paid |
| Days_Overdue | Formula | TODAY() - Due_Date (if past due) |
| Aging_Bucket | Formula | Current/1-30/31-60/61-90/90+ |
| Payment_Terms | Text | Net 15/30/60/90 |
| Contact | Text | Accounting contact |
| Notes | Text | Collection history |
| Collection_Status | Enum | New/Reminder Sent/2nd Notice/Negotiating/Collections/Write-off |

---

## 🔧 FORMULAS

### Balance Due
```excel
=F2-G2  // Invoice_Amount - Amount_Paid
```

### Days Overdue
```excel
=IF(E2>TODAY(), "-", TODAY()-E2)  // Negative = not yet due
```

### Aging Bucket
```excel
=IF(H2<=0,"Paid",
  IF(E2>TODAY(),"Current (Not Yet Due)",
    IF(TODAY()-E2<=30,"1-30 Days",
      IF(TODAY()-E2<=60,"31-60 Days",
        IF(TODAY()-E2<=90,"61-90 Days","90+ Days")))))
```

### Bucket Totals (add summary rows at bottom)
```excel
Current Total:    =SUMIFS(H:H,J:J,"Current (Not Yet Due)")
1-30 Total:       =SUMIFS(H:H,J:J,"1-30 Days")
31-60 Total:      =SUMIFS(H:H,J:J,"31-60 Days")
61-90 Total:      =SUMIFS(H:H,J:J,"61-90 Days")
90+ Total:        =SUMIFS(H:H,J:J,"90+ Days")
Grand Total AR:   =SUM(H2:H99)
```

### DSO (Days Sales Outstanding) calculation
```excel
DSO = (Total AR / Total Revenue) × Days in Period
    = (SUM(Balance_Due) / [Monthly Revenue]) × 30
```

Target: <45 days for healthy business.

---

## 🎨 CONDITIONAL FORMATTING

### Color-code aging buckets
- Current (Not Yet Due) → Green fill
- 1-30 Days → Light yellow fill
- 31-60 Days → Orange fill
- 61-90 Days → Light red fill
- 90+ Days → Dark red fill, white bold text

### Flag high-risk amounts
- Balance_Due > $10,000 AND Days_Overdue > 30 → Thick red border

### Highlight stale collection activity
- Notes column last updated > 14 days ago → Yellow highlight "Needs follow-up"

### Auto-flag write-off candidates
- Days_Overdue > 120 AND Collection_Status != "Write-off Review" → Alert "Consider write-off"

---

## ✅ COLLECTION WORKFLOW

### Collection Cadence by Age
| Age | Action |
|-----|--------|
| Current | No action (monitor) |
| 1-30 days | Friendly email reminder (day 5, 15) |
| 31-60 days | Formal 2nd notice (call + email) |
| 61-90 days | Final notice + demand letter threat |
| 90+ days | Collections agency OR attorney OR write-off |

### Collection Status Progression
```
New → Follow-up → Reminder Sent → 2nd Notice → Negotiating → Collections → Write-off Review → Written Off
```

---

## 📊 KEY METRICS

### DSO (Days Sales Outstanding)
```
DSO = (Total AR / Total Revenue) × Days in Period
```
- **Target:** <45 days
- **Warning:** 45-60 days
- **Critical:** >60 days

### % Current (Health indicator)
```
% Current = Current Balance / Total AR
```
- **Healthy:** >80%
- **Warning:** 60-80%
- **Critical:** <60%

### % 90+ (Write-off risk)
```
% 90+ = 90+ Balance / Total AR
```
- **Healthy:** <5%
- **Warning:** 5-10%
- **Critical:** >10%

### Bad Debt Allowance (GAAP)
```
ADA = Total AR × Historical bad debt rate
```
Typical: 1-3% of AR. Higher for risky industries/customers.

**Journal Entry:**
```
Dr. Bad Debt Expense         $XXX
    Cr. Allowance for Doubtful Accounts  $XXX
```

---

## 📝 WRITE-OFF PROCESS

When customer becomes uncollectible (bankruptcy, legal judgment, long-aged):

### Step 1: Document collection efforts
- All contact attempts logged
- Legal review complete
- Customer acknowledgment of inability to pay (if any)

### Step 2: Approval
- Write-offs > $1,000 typically require CFO/Owner approval
- Large write-offs require board resolution

### Step 3: Journal Entry
```
Dr. Allowance for Doubtful Accounts   $XXX
    Cr. Accounts Receivable                $XXX
```
(Reduces AR, removes from aging)

### Step 4: Tax implications
- Business bad debts (trade receivables) = ordinary deduction
- Non-business bad debts = short-term capital loss
- Must be wholly worthless (full) or partially worthless (documented)

### Step 5: Track recovery
- If customer pays later, recognize as Other Income (not Revenue)

---

## 🎯 COLLECTIONS BEST PRACTICES

1. **Invoice same day service delivered** — Faster cycle
2. **Automated reminders at day 5 and 15** — Most payments collected here
3. **Personal call at day 30** — Human touch improves collection
4. **Early payment discount (2/10 Net 30)** — 2% discount if paid in 10 days
5. **Late fee clause in contracts** — 1.5% per month typical (verify state usury caps)
6. **Credit card on file for recurring clients** — Eliminates collection cycle
7. **Progress invoicing for large projects** — Don't wait for completion
8. **Require deposits on new customers** — Reduces risk

---

## ⚠️ COMMON ISSUES

1. **Disputed invoices** — Track separately, resolve before escalating
2. **Partial payments** — Apply to oldest first OR per customer instruction
3. **Prompt payment discount confusion** — Honor only if taken within window
4. **Customers with multiple invoices** — Show all on statement; apply payments per oldest/specified
5. **Credit memos** — Net against existing AR, show separately in aging
6. **Sales tax on past due** — Interest/late fees on non-taxable portion only (varies)

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
