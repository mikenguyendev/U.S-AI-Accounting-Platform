# S-Corporation — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/S-Corp.md#section-id}}` directives.**
>
> Mỗi `## section-id` heading định nghĩa 1 anchor có thể include riêng.

**Entity Type:** S-Corporation
**Tax Treatment:** Pass-through (income flows to shareholders via K-1)
**Primary Tax Form:** Form 1120-S
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings |
| **January 31** | Form 941 (Q4) | Q4 payroll tax return |
| **March 15** | **Form 1120-S** | S-Corp income tax return + K-1s to shareholders |
| **March 15** | Form 7004 | Extension request (extends to Sep 15) |
| **April 30** | Form 941 (Q1) | Q1 payroll tax return |
| **July 31** | Form 941 (Q2) | Q2 payroll tax return |
| **September 15** | Form 1120-S (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax return |

**Shareholder-level (Form 1040 deadlines, NOT entity):**
- April 15 — Form 1040 + Q1 estimated tax (1040-ES)
- June 15 — Q2 estimated tax
- September 15 — Q3 estimated tax
- January 15 (next year) — Q4 estimated tax

---

## federal-obligations

**Entity-level returns:**
- **Form 1120-S** (annual) — S-Corporation Income Tax Return
- **Schedule K-1** — issued to each shareholder, reports their share of income/loss/deductions
- **Form 941** (quarterly) — Employer's Quarterly Federal Tax Return (payroll)
- **Form 940** (annual) — FUTA (Federal Unemployment Tax)
- **Form W-2/W-3** (annual) — Wage statements for employees
- **Form 1099-NEC** (annual) — Contractor payments >$600/year

**Shareholder-level (pass-through):**
- Income/loss flows to Form 1040 via Schedule K-1
- Shareholder pays personal income tax on their share
- Distributions ARE NOT subject to FICA/SE tax (key benefit vs sole prop)
- BUT — reasonable W-2 wages MUST come BEFORE distributions

---

## critical-rules

### S-Corp Eligibility Requirements
- **Max 100 shareholders**
- **US citizens/residents only** — no foreign shareholders
- **No entity shareholders** — no C-Corps, partnerships, multi-member LLCs as shareholders (some trusts OK)
- **Single class of stock** — no preferred shares (voting rights can differ)
- **Calendar fiscal year** required (or strong business reason for fiscal year)

### Tax Election
- File **Form 2553** within 2.5 months of formation (or by March 15 of effective year)
- Late election relief available via Rev. Proc. 2013-30 if reasonable cause

### Reasonable Compensation Rule (#1 IRS Audit Trigger)
- Owner-employees performing services MUST receive W-2 wages at "reasonable" market rate
- Distributions taken BEFORE adequate W-2 wages → IRS reclassifies distributions as wages → back FICA + penalties + interest
- Benchmark: BLS data, comparable position salary surveys, geographic adjustment
- Document the analysis annually

### Distribution Rules
- Distributions ≠ salary (no FICA)
- Pro-rata to ownership (single class of stock)
- Cannot have "preferred" distributions to specific shareholders
- Track Accumulated Adjustments Account (AAA) carefully

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | W-2, W-3, 1099-NEC, Form 940, Q4 941 |
| Mar 15 | **Form 1120-S** + K-1s |
| Apr 15 | Shareholder Q1 1040-ES |
| Apr 30 | Q1 Form 941 |
| Jun 15 | Shareholder Q2 1040-ES |
| Jul 31 | Q2 Form 941 |
| Sep 15 | Shareholder Q3 1040-ES; extended 1120-S |
| Oct 31 | Q3 Form 941 |
| Jan 15 | Shareholder Q4 1040-ES |

---

## owner-compensation

⚠️ **CRITICAL S-CORP RULE — Reasonable Compensation**

Owner-employees who actively work in the business MUST receive W-2 wages at fair market rate BEFORE taking any distributions.

**Why it matters:**
- Distributions are not subject to FICA (15.3% savings vs salary)
- IRS knows this and aggressively audits S-Corp owners taking $0 salary
- If found unreasonable: IRS reclassifies distributions as wages → back FICA + penalties

**Determining "Reasonable":**
1. **Market rate research:**
   - Bureau of Labor Statistics (bls.gov) for comparable positions
   - Salary.com, Glassdoor for industry/geography
   - SBA size standards
2. **Factors IRS considers:**
   - Training, experience, time devoted
   - Duties and responsibilities
   - Comparable salaries for similar services
   - Dividend history
   - Salary policy for non-shareholder employees
3. **Rule of thumb (NOT IRS official):**
   - Distributions should not exceed 2x annual W-2 wages

**Documentation required:**
- Annual compensation analysis memo
- Market data sources
- Job description
- Time tracking (if part-time)

**Strongly recommend:** Annual review with CPA before finalizing comp.

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form:**

1. If `active_in_business` = "Yes" AND `proposed_annual_salary` = 0 → **BLOCK with warning**
2. Apply Reasonable Comp rule: Salary must be market-rate BEFORE distributions
3. Rule of thumb: Distributions should NOT exceed 2x annual salary
4. Require documented justification:
   - Market data (BLS, salary surveys)
   - Job description
   - Geographic adjustment
   - Industry comparable
5. Strongly recommend CPA review
6. If `cpa_consulted` = "No" → advise consultation before finalizing
7. Calculate FICA implications:
   - Salary portion: 15.3% FICA (employee + employer)
   - Distribution portion: $0 FICA
   - Show savings comparison
8. Save documentation to: `05_Payroll/Owner_Compensation/`

**File naming:** `YYYYMMDD_OwnerComp_Analysis_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Owner W-2 = $0 + active in business → CRITICAL reasonable comp violation
- ⚠️ Distribution > W-2 salary by >2x → Reasonable comp risk
- ⚠️ Distribution to one shareholder different ratio than ownership → Single class of stock violation
- ⚠️ New shareholder added that is foreign person/entity → Election termination risk
- ⚠️ More than 100 shareholders projected → Election termination risk
- ⚠️ Form 1120-S not filed by March 15 → Late filing penalty $220/shareholder/month (max 12 months)
- ⚠️ K-1s not issued by March 15 → Same late penalty
- ⚠️ Built-in gains tax issues (if recently converted from C-Corp within 5 years)

---

## validation-rules

### S-Corp Specific Validation

- **Single class of stock check:** Distributions must be pro-rata to ownership %
- **Shareholder limit:** Verify count ≤ 100 before adding new shareholder
- **Shareholder eligibility:** SSN/ITIN required; reject EIN (entity shareholders) except permitted trusts
- **Owner W-2 minimum:** If owner active, require W-2 ≥ 25% of total comp (industry rule of thumb, not IRS official)
- **AAA account tracking:** Maintain Accumulated Adjustments Account separately from retained earnings
- **Built-in gains:** If converted from C-Corp within last 5 years, track BIG tax exposure

---

## estimated-tax

**Pass-through structure:** S-Corp itself does NOT pay federal income tax (with rare exceptions: BIG, excess net passive income).

**Shareholder responsibility:**
- Each shareholder pays estimated taxes on their share of S-Corp income
- Form 1040-ES quarterly: April 15, June 15, September 15, January 15
- Calculation: shareholder's K-1 share × marginal tax rate

**State considerations:**
- Some states impose entity-level S-Corp tax (e.g., CA 1.5%, NY varies)
- See state module for details

**Safe harbor for shareholder:**
- 100% of prior year tax (110% if AGI >$150K), OR
- 90% of current year actual tax

**AI MUST when processing `estimated-tax` form:**
1. Confirm payment is for shareholder personal (Form 1040-ES) NOT entity
2. Exception: state-level S-Corp tax (verify state module)
3. Calculate based on YTD K-1 projection
4. Recommend CPA review for amounts >$5K
