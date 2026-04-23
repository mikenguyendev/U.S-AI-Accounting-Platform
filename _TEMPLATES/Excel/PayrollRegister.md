# 💼 Payroll Register Template — Setup Guide

> Per pay period payroll calculation register. Foundation for paystubs, 941 quarterly, W-2 annual.

**File:** `PayrollRegister.csv`
**Update cadence:** Per pay period (weekly/bi-weekly/semi-monthly/monthly)
**Storage:** `_INSTANCES/{instance_id}/05_Payroll/Pay_Periods/FY{year}/`

---

## 📋 STRUCTURE

Per-employee per-pay-period:

### Earnings
- Gross Wages = Regular Hours × Rate + OT Hours × Rate × 1.5
- Salaried: Annual / Pay Periods (e.g., $75K / 26 = $2,884.62 bi-weekly)

### Pre-tax Deductions (reduce Gross before Federal/State income tax)
- 401(k) Deferral
- Health Insurance Premium
- HSA Contribution
- Other Section 125 (dental, vision, FSA)

### Tax Withholdings
- Federal Income Tax (per W-4 + IRS Pub 15-T)
- Social Security: 6.2% on wages up to $168,600 (2026 cap)
- Medicare: 1.45% on all wages
- Additional Medicare: 0.9% on wages > $200K
- State Income Tax (per state W-4 equivalent)
- State SDI (CA, NY, NJ, RI, HI)
- State Other (ETT, etc.)

### Post-tax Deductions
- Roth 401(k) (post-tax retirement)
- Garnishments (court-ordered)
- Loans (employer loan repayments)

### Net Pay = Gross - Pre-tax - Taxes - Post-tax

### Employer Costs (separate from employee paycheck)
- Employer FICA (matches employee 6.2% + 1.45%)
- FUTA: 0.6% on first $7,000 (after state credit)
- SUI: State-specific rate on wage base
- State ETT (CA, etc.)
- Workers' Comp insurance

---

## 🔧 FORMULAS

### Gross Wages (hourly)
```excel
=Hours_Regular*Pay_Rate + Hours_OT*Pay_Rate*1.5
```

### Federal Income Tax Withholding
Use IRS Pub 15-T tables OR percentage method:
```excel
// Simplified — actual calc more complex
=IF(Filing_Status="Single",
    [Single bracket lookup],
    [Married bracket lookup])
```

Most payroll software handles this automatically. Manual calc requires:
- W-4 step inputs (steps 2, 3, 4)
- Annualized wage calculation
- Apply percentage method tables (Pub 15-T)

### Social Security Tax (Employee)
```excel
=MIN(Gross_Wages, 168600 - YTD_SS_Wages) * 0.062
```

### Medicare Tax (Employee)
```excel
=Gross_Wages * 0.0145
```

### Additional Medicare (only if YTD wages > $200K single)
```excel
=IF(YTD_Wages + Gross_Wages > 200000,
    MAX(0, MIN(Gross_Wages, YTD_Wages + Gross_Wages - 200000)) * 0.009,
    0)
```

### State Income Tax Withholding (varies by state)
- CA: Use Method B from DE-44 (progressive 1%-13.3%)
- IL: Flat 4.95%
- TX/FL/WA: $0 (no state income tax)
- NY: Use NYS-50-T-NYS (4%-10.9%) + NYC if resident

### Net Pay
```excel
=Gross - 401k - Health - PreTaxOther - FederalTax - SS - Medicare - AddMed - StateTax - StateSDI - StateOther - PostTaxDeductions
```

### Employer FICA SS
```excel
=MIN(Gross_Wages, 168600 - YTD_SS_Wages) * 0.062
```

### Employer FICA Medicare
```excel
=Gross_Wages * 0.0145
```

### FUTA (after credit)
```excel
=IF(YTD_FUTA_Wages < 7000,
    MIN(Gross, 7000 - YTD_FUTA_Wages) * 0.006,
    0)
```
(0.6% with state credit; 6.0% if state credit unavailable)

### SUI (state-specific rate)
```excel
=IF(YTD_SUI_Wages < SUI_Wage_Base,
    MIN(Gross, SUI_Wage_Base - YTD_SUI_Wages) * SUI_Rate,
    0)
```

### Workers' Comp
```excel
=Gross_Wages * WC_Rate / 100
```
(Rate per $100 of wages; varies by class code)

### Total Employer Cost
```excel
=Gross + EmployerFICA + EmployerMedicare + FUTA + SUI + WC + OtherEmployerCosts
```

---

## 📝 SAMPLE PAYROLL JE

For example data above (PP ending 4/15/2026, 4 employees, $11,570.50 gross):

```
Dr. Salaries and Wages (6010)              $11,570.50
Dr. Payroll Tax Expense (6030)               1,063.21    [SS+Med ER + FUTA + SUI + ETT]
Dr. Workers Comp Insurance (6710)              404.97
    Cr. Federal Income Tax Withheld (2310)            $1,125.00
    Cr. FICA Withheld (2320) [SS+Med EE]                 841.65
    Cr. FICA Payable (2330) [SS+Med ER]                  841.65
    Cr. State Income Tax Withheld (2340)                 518.00
    Cr. State Unemployment (2350)                         40.50
    Cr. State ETT (2350)                                  11.58
    Cr. State SDI (2340)                                 127.28
    Cr. FUTA Payable (2360)                               26.03
    Cr. 401(k) Withheld (2300)                           672.28
    Cr. Health Insurance Withheld (2300)                 900.00
    Cr. Workers Comp Payable (2200)                      404.97
    Cr. Cash - Net Pay (1010)                          7,386.29
                                          ────────  ────────
                                          $13,038.68  $13,038.68
                                          BALANCED ✓
```

---

## 📊 KEY METRICS (track over time)

### Payroll % of Revenue
```
= Total Payroll Cost (incl. employer taxes + benefits) / Revenue
```
- Service: 50-70%
- Restaurant: 28-32% (target)
- Manufacturing: 15-25%
- SaaS: 50-70%

### Average Cost per FTE
```
= Total Payroll Cost / # Full-Time Equivalents
```

### Overtime % of Total Hours
```
= OT Hours / Total Hours
```
- Healthy: <10%
- Warning: 10-20%
- Burnout/cost issue: >20%

---

## 🎨 CONDITIONAL FORMATTING

### High earners flag (Additional Medicare trigger)
- YTD Wages > $200K → Yellow highlight (Additional Medicare applies)

### SS wage cap reached
- YTD SS Wages = $168,600 → Green (no more SS withholding rest of year)

### Overtime alert
- OT hours > 10 per period → Yellow (review scheduling)

### Missing components
- Net Pay = blank → Red (formula error)
- Employer Cost = blank → Red

---

## ✅ COMPLIANCE CHECKLIST

### Federal
- [ ] Federal W-4 on file for each employee
- [ ] I-9 completed within 3 days of hire
- [ ] EIN obtained
- [ ] Form 941 filed quarterly
- [ ] Form 940 filed annually
- [ ] W-2/W-3 issued by Jan 31

### State (varies)
- [ ] State withholding form on file (DE-4 for CA, IT-2104 for NY, etc.)
- [ ] State employer registration (SUI, withholding)
- [ ] State quarterly returns filed
- [ ] State new hire reporting (within state-specific window)

### Insurance
- [ ] Workers' Comp policy active
- [ ] Workers' Comp class codes accurate
- [ ] State Disability where mandatory (CA, NY, NJ, RI, HI)
- [ ] PFML where mandatory (NY, NJ, MA, WA, etc.)

### Internal
- [ ] Pay rate change approval
- [ ] Time tracking accurate
- [ ] Bonus/commission calculations documented
- [ ] PTO accruals tracked

---

## ⚠️ COMMON ISSUES

1. **Misclassifying employee as 1099 contractor** — IRS reclassification + back wages + penalties
2. **OT calculation errors** — All hours >40/week × 1.5x (federal); some states stricter
3. **Tip pooling violations** (restaurants) — DOL regulations specific
4. **Garnishment priority** — Multiple garnishments require priority order
5. **Final paycheck timing** — State-specific (some require same day)
6. **Bonus tax withholding** — Use supplemental rate (22% federal flat)
7. **Year-end true-up** — Box 12 codes, 401(k) contribution limits
8. **Additional Medicare missed** — 0.9% on wages > $200K
9. **State tax for remote workers** — Withhold based on workplace state (varies)
10. **Compensation > FICA cap** — SS only on first $168,600 (2026); easy to over-withhold

---

## 💡 PAYROLL PROVIDER VS MANUAL

### Use payroll provider when:
- 5+ employees
- Multi-state
- Complex benefits
- High audit risk industry

### Recommended providers
- **Gusto** — Best for SMB (5-50 employees)
- **ADP** — Enterprise + complex
- **Rippling** — Tech companies, integrated HR
- **Paychex** — Mid-market
- **OnPay** — Affordable basic

### Manual OK when:
- 1-4 employees
- Single state
- Owner can dedicate time
- Excel/CSV-based bookkeeping

→ This template suitable for manual approach. For 5+ employees, recommend provider.

---

*AI Accounting Template v1.0.0 by mikenguyen.dev@gmail.com*
