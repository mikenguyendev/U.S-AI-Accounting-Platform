# Delaware (DE) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/DE.md#section-id}}` directives.**

**State:** Delaware
**Tax Authority:** Delaware Division of Revenue (DOR), Delaware Department of Labor (DOL)
**Last Updated:** 2026-04-22

> **🎯 INCORPORATION HUB:** Delaware là nơi 67% Fortune 500 incorporated. Pro-business courts (Court of Chancery), flexible corporate law, no sales tax, but franchise tax on shares can be expensive nếu authorized shares cao.
>
> **⚠️ DUAL TAX EXPOSURE:** Nếu incorporate in DE but operate elsewhere, MUST pay both: (1) DE franchise tax + DE annual report; (2) state taxes nơi actually doing business. Common mistake: thinking "incorporate in DE = only DE taxes."

---

## tax-obligations

### Key Delaware Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **DE Franchise Tax (Corp)** | $400 minimum (Authorized Shares method) OR $400 minimum (Assumed Par Value method) | DE DOS | March 1 |
| **DE Franchise Tax (LLC)** | $300 flat | DE DOS | June 1 |
| **DE Corporate Income Tax** | 8.7% on net income (only if doing business IN Delaware) | DOR | April 15 |
| **DE Personal Income Tax** | Progressive 2.2%–6.6% | DOR | April 30 |
| **DE Gross Receipts Tax** | 0.0945%–1.9914% (varies by activity) | DOR | Monthly/Quarterly |
| **DE Sales & Use Tax** | **0%** (NO state sales tax) | N/A | N/A |
| **DE SUI (Unemployment)** | 0.1%–8.0% on first $10,500 wages (2026) | DOL | Quarterly |
| **No SDI** | N/A | N/A | N/A |
| **Workers' Compensation** | MANDATORY for all employers | Office of WC | Per pay period |

> **⚠️ KEY DISTINCTION:**
> - **Incorporated in DE but NOT doing business in DE:** Pay only DE Franchise Tax + Annual Report. NO DE income tax.
> - **Incorporated AND operating in DE:** Pay franchise tax + DE Corporate Income Tax 8.7% + Gross Receipts Tax.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 SUI return | UC-8 |
| **March 1** | **DE Corp Franchise Tax + Annual Report** | DE Annual Report |
| **April 15** | DE Corporate Income Tax (if operating in DE) | Form 1100 |
| **April 30** | Q1 SUI return | UC-8 |
| **April 30** | DE Personal Income Tax | Form 200-01 |
| **June 1** | **DE LLC/LP Franchise Tax** | DE LLC Tax |
| **July 31** | Q2 SUI return | UC-8 |
| **October 31** | Q3 SUI return | UC-8 |

**Gross Receipts Tax filing:** Monthly (most), Quarterly (small businesses).
**Due:** 20th of month following filing period.

---

## upcoming-deadlines

**Next 12 months DE-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 SUI |
| **Mar 1** | **DE Corp Franchise Tax + Annual Report** |
| Apr 15 | DE Corp Income (if operating in DE) |
| Apr 30 | Q1 SUI + DE Personal Income |
| **Jun 1** | **DE LLC/LP Franchise Tax** |
| Jul 31 | Q2 SUI |
| Oct 31 | Q3 SUI |

---

## critical-reminders

- ⚠️ **DE Franchise Tax can be SHOCKING for high-share C-Corps** — Authorized Shares method default, can be $50K+ for startups with 10M+ authorized shares
- ⚠️ **Use "Assumed Par Value" method** instead — caps at $200K for most companies (still high but predictable)
- ⚠️ **Annual Report MANDATORY** for all DE corps (filed with Franchise Tax) — late = $200 penalty + interest + entity status risk
- ⚠️ **LLCs simpler:** Flat $300/year, no annual report required
- ⚠️ **NO sales tax in DE** — major reason for some retail/distribution operations in DE
- ⚠️ **Gross Receipts Tax** — small but applies to all DE-based businesses (different from sales tax)
- ⚠️ **Do not confuse "incorporated" with "operating":** Only physical presence/employees in DE creates income tax nexus
- ⚠️ **Court of Chancery** — DE's specialized business court (no juries) — major reason VCs prefer DE incorporation
- ⚠️ **Registered Agent required** — must have DE-based agent for service of process (~$100-300/year)
- ⚠️ **DE personal income tax 6.6% top rate** — applies to DE residents and DE-source income (lower than NY/CA)
- ⚠️ **DE minimum wage:** $13.25/hour (2024) — verify 2026
- ⚠️ **Reciprocity:** DE has reciprocity với PA, MD, NJ for some income types — verify per situation

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ DE Corp using default Authorized Shares method when Assumed Par Value would be lower → overpayment
- ⚠️ DE Annual Report not filed by March 1 → $200 penalty + entity in "delinquent" status
- ⚠️ DE LLC not paying $300 by June 1 → entity loses good standing
- ⚠️ Operating in DE without registering Foreign Qualification (if from another state) → fines + back taxes
- ⚠️ Hiring DE employees but not registered with DE DOL → SUI compliance issue
- ⚠️ Issuing many authorized shares "just in case" → triggers astronomical franchise tax
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions in DE → may trigger income tax (if doing business)
- ⚠️ Registered Agent fees unpaid → DE DOS may dissolve entity
- ⚠️ Incorporating in DE but operating in CA — assuming "DE only" taxes (must pay BOTH)

---

## validation-rules

### DE-Specific Validation

- **Franchise Tax method election:** Re-evaluate annually — Authorized Shares vs Assumed Par Value
- **Authorized Shares method:** Up to 5,000 = $175; beyond = $250 + $0.04/share over 5K (capped at $200K)
- **Assumed Par Value method:** Total Gross Assets × (Issued Shares / Total Authorized) × $400/$1M
- **Gross Receipts Tax classifications:** Must use correct activity code
- **Foreign Qualification:** Out-of-state DE-incorporated entities operating in another state must register there too
- **Registered Agent:** Required, must be DE physical address
- **No sales tax means no use tax compliance** for in-DE sales (but use tax owed if buying from out-of-state for DE use)

---

## sales-tax

**Delaware has NO state sales tax.**

- **No sales tax permit required**
- **No sales tax to collect from customers**
- **No sales tax filings**

**However:**
- **Gross Receipts Tax** still applies to DE-based businesses (see below)
- **Use tax** owed on out-of-state purchases used in DE? No, DE has no use tax either.

**Sales tax reciprocity:** Customers buying in DE pay no sales tax. Customers shopping in DE while residing in another state may owe USE tax in their home state.

---

## estimated-tax

### DE Corporate Income Tax (only if operating in DE)

For C-Corps operating in DE owing >$5,000 estimated tax:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 1 | Form 1100-T |
| Q2 | June 15 | Form 1100-T |
| Q3 | September 15 | Form 1100-T |
| Q4 | December 15 | Form 1100-T |

**Calculation:** 25% of expected annual liability per quarter.

### DE Personal Income Tax (Owners)

For DE residents OR non-residents with DE-source income:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 30 | Form 200-ES |
| Q2 | June 15 | Form 200-ES |
| Q3 | September 15 | Form 200-ES |
| Q4 | January 15 | Form 200-ES |

**AI MUST when processing `estimated-tax` form for DE:**
1. Distinguish: incorporated in DE vs operating in DE
2. If only incorporated (no operations): NO DE income tax estimated payments needed
3. If operating in DE: file Form 1100-T quarterly
4. Owners who are DE residents: file Form 200-ES personally
5. Non-resident owners receiving DE-source income: also file Form 200-ES (non-resident)

---

## withholding-form

**DE Employee State Withholding Form: W-4DE / Federal W-4 (DE accepts federal)**

- **Purpose:** Determines DE state income tax withholding
- **Note:** Delaware uses federal W-4 by default; DE-specific W-4DE for state-only adjustments
- **Default if no form:** Single, 0 allowances
- **Update:** Employee can submit anytime

**Companion forms required at hire:**
- Federal W-4
- I-9 (within 3 days)
- New Hire Reporting via DE Division of Child Support within 20 days

---

## withholding-tables

**DE Withholding Calculation:**

Use DE Department of Revenue Withholding Tables (annually updated).

- Progressive brackets: 2.2%–6.6%
- Standard deduction varies by filing status

**Tools:**
- DE DOR Withholding Calculator
- IRS Pub 15-T (federal portion)

**Special situations:**
- Bonuses: Aggregate or supplemental rate (varies — most use 5%)
- Out-of-state remote workers for DE employer: Convenience of Employer rule does NOT apply in DE (withhold based on workplace state)

---

## payroll-taxes

### Employer-Side DE Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **DE SUI** | 0.1%–8.0% | First $10,500 (2026) | New employer 1.8% |
| **No SDI** | N/A | N/A | DE does not have SDI |
| **DE Income Tax PIT** | 2.2%–6.6% | All wages | Employer withholds |

### New Employer Default Rates
- New employer SUI: 1.8% Year 1
- DE minimum wage: $13.25/hour (2024) — verify 2026

### Quarterly Reporting
- **Form UC-8** — Employer's Quarterly Tax & Wage Report
- Due: Last day of month after quarter end

### E-file
- Required for employers with 50+ employees
- Recommended for all (DE DOL portal)

### Other DE Employment Requirements
- New Hire Reporting: 20 days (DE Child Support)
- Workers' Comp: MANDATORY (private insurance market)
- Paid Sick Leave: NOT mandated (no state law)

---

## entity-specific-tax

### S-Corporation in DE
- **DE Franchise Tax** ($400 min) annually if incorporated in DE
- DE doesn't recognize federal S-Corp election for DE state tax purposes — but pass-through still applies for federal
- Federal Form 1120-S still required
- DE-resident shareholders: pay DE personal income tax on K-1

### C-Corporation in DE
- **DE Franchise Tax** based on Authorized Shares OR Assumed Par Value method
- **DE Corporate Income Tax 8.7%** ONLY if operating in DE (rare for "DE C-Corps" that operate elsewhere)
- Federal Form 1120 + DE Form 1100 if operating in DE

### LLC in DE
- **DE LLC Tax: $300/year** flat (much simpler than corp)
- LLC formation: $90 (one-time) + $300 annual
- NO annual report required (just pay tax)
- Federal Form 1065/Schedule C
- ✅ Most popular structure for non-DE businesses incorporating in DE for legal benefits

### Partnership in DE
- **DE Partnership Tax: $300/year** if registered as LP/LLP
- General Partnership: no DE filing needed
- Federal Form 1065 + K-1s

### Sole Proprietor in DE
- No state filing for sole prop
- DE personal income tax via Form 200-01
- Just federal Schedule C

### Out-of-State Entities Incorporated in DE
- ✅ This is the COMMON scenario (e.g., CA startup incorporates in DE)
- Pay DE Franchise Tax ($300 LLC or $400+ Corp) annually
- Maintain DE Registered Agent (~$100-300/year)
- Operate + pay taxes in actual operating state
- File Foreign Qualification (Authority to Transact Business) in operating state(s)
