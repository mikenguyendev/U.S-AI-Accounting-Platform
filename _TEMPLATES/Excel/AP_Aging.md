# 💸 AP Aging Template — Setup Guide

> Track vendor payables by age. Cash management + vendor relationship tool.

**File:** `AP_Aging.csv`
**Update cadence:** Weekly (payment cycle)
**Storage:** `_INSTANCES/{instance_id}/01_AP-AR_Management/Accounts_Payable/`

---

## 📋 STRUCTURE

| Column | Type | Notes |
|--------|------|-------|
| Vendor_ID | Text | Internal vendor code |
| Vendor_Name | Text | Legal entity name |
| Invoice_Number | Text | Vendor invoice ID |
| Invoice_Date | Date | When invoice received |
| Due_Date | Date | When payment due |
| Invoice_Amount | Currency | Total owed |
| Amount_Paid | Currency | Cumulative payments made |
| Balance_Due | Formula | Invoice - Paid |
| Days_Until_Due | Formula | Due_Date - TODAY() (negative = overdue) |
| Aging_Bucket | Formula | Current/1-30/31-60/61-90/90+ |
| Payment_Terms | Text | Net X / COD / Due on Receipt |
| 1099_Required | Yes/No | Flag for 1099-NEC tracking |
| Approval_Status | Enum | Pending/Approved/On Hold/Disputed |
| Payment_Method | Enum | Check/ACH/Wire/Credit Card |
| Notes | Text | Status notes |

---

## 🔧 FORMULAS

### Balance Due
```excel
=F2-G2
```

### Days Until Due (negative = overdue)
```excel
=E2-TODAY()
```

### Aging Bucket (flipped vs AR)
```excel
=IF(H2<=0, "Paid",
  IF(E2>=TODAY(), "Current",
    IF(TODAY()-E2<=30, "1-30 Days Overdue",
      IF(TODAY()-E2<=60, "31-60 Days Overdue",
        IF(TODAY()-E2<=90, "61-90 Days Overdue", "90+ Days Overdue")))))
```

### 1099 YTD tracker (separate sheet)
```excel
=SUMIFS(AP!F:F, AP!B:B, "[VendorName]", AP!L:L, "Yes", AP!D:D, ">="&StartOfYear)
```
→ Track YTD per vendor; if >$600, issue 1099-NEC at Jan 31.

---

## 🎨 CONDITIONAL FORMATTING

### Color-code aging
- Current → Green (cash flow safe)
- 1-30 Days Overdue → Yellow (act soon)
- 31-60 Days Overdue → Orange (risk of late fees / service cut)
- 61-90+ Days Overdue → Red (critical)

### Due within 7 days
- Days_Until_Due ≤ 7 AND > 0 → Blue highlight (payment action needed)

### Approval workflow
- Approval_Status = "Pending Approval" → Red text
- Approval_Status = "On Hold" → Gray italic
- Approval_Status = "Disputed" → Red background

### 1099 required
- 1099_Required = "Yes" → Blue text for tracking

---

## ✅ PAYMENT WORKFLOW

### Priority hierarchy
1. **Payroll (always on time)** — Legal requirement + employee retention
2. **Sales tax, payroll tax remittance** — Government penalties severe
3. **Critical services (rent, utilities, insurance)** — Service cutoff risk
4. **Trade vendors (materials, inventory)** — Business continuity
5. **Professional services** — Relationship maintenance
6. **Others** — Per terms

### Early payment discount decision
**Formula:** Discount % × 365 / (Normal days - Discount days)

Example: 2/10 Net 30 = 2% × 365 / (30-10) = 36.5% annualized return
→ Take discount if cash available (effectively 36% return)

### Dispute handling
1. Mark Approval_Status = "Disputed"
2. Document dispute in Notes
3. Notify vendor in writing
4. Withhold payment until resolved
5. Post to separate "Disputed AP" ledger if material
6. Set review calendar

---

## 📊 KEY METRICS

### DPO (Days Payable Outstanding)
```
DPO = (Total AP / Total Purchases) × Days in Period
```
- **Healthy:** 30-45 days
- **Negotiating power:** 45-60 days
- **Vendor relationship risk:** >60 days

### AP Turnover
```
AP Turnover = Total Purchases / Average AP
```
Lower = paying slower (better cash conservation, worse vendor relationships).

### % Past Due
```
% Past Due = Past Due Balance / Total AP
```
- **Healthy:** <10%
- **Warning:** 10-25%
- **Crisis:** >25%

---

## 📝 1099-NEC TRACKING

### Who gets a 1099-NEC?
- **Unincorporated** vendors (Sole Prop, LLC-single by default, Partnership)
- Services provided (NOT product purchases)
- Total YTD payments > $600
- NOT payments via credit card (payment processor issues 1099-K)
- NOT payments to corporations (C-Corp, S-Corp) unless attorney

### Required info on file (W-9)
- Legal name
- Business name (if different)
- Federal Tax Classification
- TIN (SSN or EIN)
- Address
- Backup withholding status

### Year-end process
1. December: Pull YTD payment list per vendor
2. Identify 1099-NEC candidates
3. Verify W-9 on file (BLOCKER if missing)
4. Generate 1099-NEC forms
5. Mail/email to vendors by Jan 31
6. File with IRS (e-file via FIRE system or mail Form 1096 + 1099s)

---

## 🎯 CASH FLOW MANAGEMENT

### Weekly AP Schedule
Every Friday:
- Review AP aging report
- Identify payments due next week
- Confirm cash availability
- Approve batch payments
- Execute ACH/check run Monday or mid-week

### Payment batching
- **ACH run:** Weekly (process 3-5 business days)
- **Checks:** Bi-weekly (print + mail cycle)
- **Wires:** Ad-hoc (for urgent/large)
- **Credit card:** As purchased (auto)

---

## ⚠️ COMMON ISSUES

1. **Duplicate invoices** — Same invoice from vendor twice; reject duplicate
2. **Vendor billing errors** — Wrong amount, quantity, or item
3. **Missing PO reference** — Require PO for purchases > threshold
4. **Unauthorized purchases** — Staff buying without approval; enforce threshold rules
5. **Payment sent but not cleared** — Check lost in mail; reissue + stop payment on original
6. **Vendor change of address** — Update records; payment bouncebacks common
7. **Currency issues** — Foreign vendor invoices require FX conversion; document rate
8. **Penalty/late fee charges** — Dispute if service interruption caused by vendor

---

## 💡 NEGOTIATION LEVERS

When cash tight, consider:
- **Extended terms** — Request Net 45 or Net 60 from key vendors
- **Payment plan** — Split large invoice across 2-3 months
- **Early payment discount** — Offer 2% for 10-day pay (your vendor may appreciate)
- **Supplier financing** — Some vendors offer 60-90 day terms
- **Credit card payment** — Use card for float (20-50 days), pay balance in full

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
