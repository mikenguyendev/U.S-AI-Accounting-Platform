# General/Limited Partnership — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/Partnership.md#section-id}}` directives.**
>
> **Note:** Multi-member LLCs taxed as partnership có nhiều rules tương tự — xem `LLC-multi.md` nếu structure là LLC.

**Entity Type:** Partnership (General Partnership, Limited Partnership, LLP)
**Tax Treatment:** Pass-through (Form 1065 + K-1s)
**Primary Tax Form:** Form 1065
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings (if has employees) |
| **January 31** | Form 941 (Q4) | Q4 payroll tax (if has employees) |
| **March 15** | **Form 1065** | Partnership return + K-1s issued to partners |
| **March 15** | Form 7004 | Extension request (extends to September 15) |
| **April 15** | Form 1040-ES (Q1) | Partner's Q1 estimated tax (personal) |
| **April 30** | Form 941 (Q1) | Q1 payroll tax (if employer) |
| **June 15** | Form 1040-ES (Q2) | Q2 estimated tax (partners) |
| **July 31** | Form 941 (Q2) | Q2 payroll tax |
| **September 15** | Form 1040-ES (Q3) | Q3 estimated tax (partners) |
| **September 15** | Form 1065 (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax |
| **January 15 (next yr)** | Form 1040-ES (Q4) | Q4 estimated tax (partners) |

**Partner receives K-1 by March 15** — needed for personal Form 1040.

---

## federal-obligations

**Entity-level returns:**
- **Form 1065** (annual) — U.S. Return of Partnership Income
- **Schedule K-1** — issued to each partner
- **Form 941** (quarterly) — IF has employees
- **Form 940** (annual) — IF has employees
- **Form W-2/W-3** (annual) — IF has employees (NOT for partners)
- **Form 1099-NEC** (annual) — Contractor payments >$600/year

**Partner-level:**
- Form 1040 + Schedule E (passive) or include in Schedule C income (active)
- Form 1040-ES quarterly estimated tax
- Self-employment tax on guaranteed payments + active partner share

---

## critical-rules

### Partnership Types
| Type | Liability | SE Tax | Common Use |
|------|-----------|--------|------------|
| **General Partnership (GP)** | Unlimited personal liability for ALL partners | All partners owe SE tax on share | Old-school businesses, default for 2+ owners without formal LLC |
| **Limited Partnership (LP)** | General Partner = unlimited; Limited Partners = limited | GP owes SE tax; LPs only on guaranteed payments | Investment funds, real estate |
| **Limited Liability Partnership (LLP)** | All partners limited liability (varies by state) | All partners owe SE tax (similar to LLC-multi) | Law firms, accounting firms, professional services |
| **Limited Liability Limited Partnership (LLLP)** | Both GPs + LPs have limited liability | Same as LP | Rare, only some states |

### Key Differences vs LLC-multi
- **Liability:** GPs in partnership = unlimited (huge risk vs LLC structure)
- **Formation:** Partnership often formed by handshake (informal); LLC requires state filing
- **State filing:** GP usually no state filing; LLP/LP requires registration
- **Tax treatment:** Same (Form 1065) — partnership and LLC-multi taxed identically
- **For most modern businesses:** LLC-multi preferred for liability protection

### Partner Compensation
3 categories same as LLC-multi:
1. Guaranteed Payments (Box 4 of K-1)
2. Distributive Share (Box 1)
3. Distributions (cash transfers)

### Capital Account & Basis
- Each partner has Capital Account
- Track contributions, profit/loss share, distributions
- Basis affects loss deductibility, distribution tax treatment
- Form 1065 Schedule K-1 reports beginning/ending capital

### Partnership Audit Regime (BBA)
- Since 2018, partnership audits handled at entity level (not partner level)
- Must designate Partnership Representative (PR) — not "Tax Matters Partner"
- PR has authority to bind partnership in IRS proceedings
- Adjustments paid by partnership unless "push-out" election

### Partnership Agreement (CRITICAL)
- Even GP needs written agreement (verbal partnerships invite disputes)
- Should specify:
  - Profit/loss allocation
  - Capital contribution requirements
  - Distribution priorities
  - Decision-making authority
  - Buy-sell provisions
  - Dissolution procedures

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 1040-ES (partners, prior year) |
| Jan 31 | W-2, W-3, 1099-NEC (if employer) |
| **Mar 15** | **Form 1065 + K-1s** |
| Apr 15 | Q1 1040-ES (partners) |
| Apr 30 | Q1 Form 941 (if employer) |
| Jun 15 | Q2 1040-ES (partners) |
| Jul 31 | Q2 Form 941 |
| Sep 15 | Q3 1040-ES (partners); extended Form 1065 |
| Oct 31 | Q3 Form 941 |
| Jan 15 (next yr) | Q4 1040-ES (partners) |

---

## owner-compensation

⚠️ **PARTNERS ARE NOT EMPLOYEES — NO W-2**

Same structure as LLC-multi:

### Guaranteed Payments
- Compensation for services or capital regardless of profit
- Reported K-1 Box 4
- Subject to SE tax
- DEDUCTIBLE to partnership (reduces partnership income)
- No federal/state withholding (partner self-pays)

### Distributive Share
- Partner's allocated share of partnership profit/loss
- Reported K-1 Box 1
- Active partners (GPs, materially participating LPs): subject to SE tax
- Truly passive limited partners: NOT subject to SE tax on share

### Distributions
- Cash transfers to partners
- Up to basis: tax-free (return of capital)
- Beyond basis: taxable gain
- Distributions don't change taxable income (income already taxed via K-1)

### General Partner vs Limited Partner SE Tax
- **General Partner:** SE tax on full distributive share + guaranteed payments
- **Limited Partner:** SE tax ONLY on guaranteed payments (not on profit share)
- ⚠️ "Limited partner" must be truly limited — not active in management

### Documentation Required
- Partnership Agreement
- Capital account ledger per partner
- Profit/loss allocation worksheet
- Form K-1 issued by March 15

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form for Partnership partner:**

1. Identify partner type: General, Limited, or LLP
2. Categorize payment: guaranteed payment vs distribution vs capital return
3. **Guaranteed Payment** journal entry:
   ```
   Dr. 6800 - Guaranteed Payments to Partners    $XXX.XX
       Cr. [Cash account]                                $XXX.XX
   ```
4. **Distribution** journal entry:
   ```
   Dr. 3501 - Partner [Name] Distributions    $XXX.XX
       Cr. [Cash account]                             $XXX.XX
   ```
5. NO W-2 (partners are NOT employees)
6. NO payroll tax withheld (partner self-pays via 1040-ES)
7. Update partner's capital account
8. For LP structure: verify limited partner is truly passive (else IRS may reclassify)
9. Track YTD by partner for K-1 prep
10. Save documentation to: `05_Payroll/Partner_Compensation/`

**File naming:** `YYYYMMDD_PartnerComp_[PartnerName]_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Partner added to W-2 payroll → MAJOR ERROR (not allowed)
- ⚠️ General partnership operating without written agreement → high dispute risk
- ⚠️ Limited partner active in management → loses limited liability + SE tax exposure
- ⚠️ Distribution exceeding partner basis → taxable gain
- ⚠️ Profit allocation deviates from agreement → audit risk
- ⚠️ Form 1065 not filed by March 15 → $235/partner/month penalty (max 12 months)
- ⚠️ K-1 not issued by March 15 → same penalty
- ⚠️ Partnership Representative (PR) not designated → BBA audit issues
- ⚠️ Foreign partner → 37% withholding (or treaty rate) on effectively connected income (Form 8804/8805)
- ⚠️ GP using personal funds for partnership debts → indicates unlimited liability exposure
- ⚠️ State LP/LLP registration lapsed → loses limited liability shield

---

## validation-rules

### Partnership Specific Validation

- **Partner count:** Must be ≥2 (else dissolution)
- **K-1 issuance:** Verify all partners receive K-1 by March 15
- **Capital account:** Beginning + Contributions + Allocations - Distributions = Ending
- **Special allocations:** Verify Substantial Economic Effect (Section 704(b))
- **GP vs LP designation:** Track in partner roster, drives SE tax treatment
- **State annual report:** Many states require LLP/LP annual filing
- **Self-Employment Tax for active partners:** Calculate on full distributive share + guaranteed payments

---

## estimated-tax

**Pass-through structure:** Partnership does NOT pay federal entity income tax. Each partner pays personal estimated tax.

### Partner-Level Estimated Tax

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1040-ES |
| Q2 | June 15 | Form 1040-ES |
| Q3 | September 15 | Form 1040-ES |
| Q4 | January 15 (next year) | Form 1040-ES |

### Calculation per Partner
**Estimated tax = (Income tax on K-1 share + SE tax on share + Additional Medicare) ÷ 4**

### Safe Harbor (per partner)
- 100% of prior year tax (110% if AGI >$150K), OR
- 90% of current year tax

### State PTE Tax Election
- Many states allow partnership-level state tax election (SALT cap workaround)
- Members get state credit for entity-paid tax
- Evaluate annually with CPA

**AI MUST when processing `estimated-tax` form for Partnership:**
1. Confirm payment is for PARTNER (Form 1040-ES), NOT entity
2. Exception: state PTE election if applicable
3. Allocate based on K-1 share + guaranteed payments
4. Distinguish GP (SE tax on full share) vs LP (SE tax only on guaranteed payments)
5. Track YTD partner-by-partner
6. Recommend CPA for amounts >$10K/quarter
