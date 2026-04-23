# Multi-Member LLC (LLC-multi) — Entity Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/entity/LLC-multi.md#section-id}}` directives.**

**Entity Type:** Multi-Member Limited Liability Company
**Tax Treatment:** Partnership (default) — Form 1065 + K-1s to members
**Primary Tax Form:** Form 1065
**Last Updated:** 2026-04-22

---

## federal-deadlines

| Deadline | Form | Action |
|----------|------|--------|
| **January 31** | W-2, W-3, 1099-NEC, Form 940 | Year-end payroll filings (if has employees) |
| **January 31** | Form 941 (Q4) | Q4 payroll tax (if has employees) |
| **March 15** | **Form 1065** | Partnership return + K-1s issued to members |
| **March 15** | Form 7004 | Extension request (extends to September 15) |
| **April 15** | Form 1040-ES (Q1) | Member's Q1 estimated tax (personal) |
| **April 30** | Form 941 (Q1) | Q1 payroll tax (if employer) |
| **June 15** | Form 1040-ES (Q2) | Q2 estimated tax (members) |
| **July 31** | Form 941 (Q2) | Q2 payroll tax |
| **September 15** | Form 1040-ES (Q3) | Q3 estimated tax (members) |
| **September 15** | Form 1065 (extended) | If extension filed |
| **October 31** | Form 941 (Q3) | Q3 payroll tax |
| **January 15 (next yr)** | Form 1040-ES (Q4) | Q4 estimated tax (members) |

**Member receives K-1 by March 15** — needed for personal Form 1040 filing.

---

## federal-obligations

**Entity-level returns:**
- **Form 1065** (annual) — U.S. Return of Partnership Income
- **Schedule K-1** — issued to each member, reports their share of income/loss/credits
- **Form 941** (quarterly) — IF has employees
- **Form 940** (annual) — IF has employees
- **Form W-2/W-3** (annual) — IF has employees (NOT for members — see below)
- **Form 1099-NEC** (annual) — Contractor payments >$600/year

**Member-level (pass-through):**
- Income/loss flows to each member's Form 1040 via K-1
- Members file Schedule E (passive) or include on Schedule C (active)
- **Self-employment tax:** Active members owe SE tax on guaranteed payments + share of business income
- Quarterly estimated tax via Form 1040-ES

**Optional: Elect to be taxed as Corporation**
- File Form 8832 → C-Corp treatment
- File Form 8832 + Form 2553 → S-Corp treatment

---

## critical-rules

### Eligibility
- **2 or more members** (any combination of individuals, entities, foreign persons)
- Default: Partnership tax treatment
- Members can have different ownership %, profit/loss allocation, capital contributions
- Operating Agreement governs internal affairs

### Member Compensation Structure
3 ways members can receive money from LLC:
1. **Guaranteed Payments** — Like salary, regardless of profit. Subject to SE tax. Deductible to LLC.
2. **Distributions** — Share of profit. Subject to SE tax for active members.
3. **Capital Returns** — Return of contributed capital. NOT taxable.

### Self-Employment Tax for Members
- **Active members** (material participation): SE tax on guaranteed payments + share of partnership income
- **Limited partners** (passive): SE tax only on guaranteed payments, NOT on profit share
- **LLC member-managers:** Generally treated as active → SE tax on full distributive share
- IRS challenges aggressive "passive" claims for LLC members

### Capital Account Tracking (CRITICAL)
- Each member has a Capital Account
- Tracked: contributions, share of profit/loss, distributions
- 704(b) book capital vs Tax basis capital — both required
- Imbalance can trigger IRS audit
- Form 1065 Schedule K-1 reports beginning/ending capital

### Special Allocations
- Members can allocate income/loss differently from ownership %
- Must have "substantial economic effect" (Section 704(b))
- Documentation in Operating Agreement

### Profits Interest vs Capital Interest
- **Profits Interest:** Right to future profits only (no current value) — generally not taxable when granted
- **Capital Interest:** Right to current capital + future profits — taxable when granted (FMV)

---

## upcoming-deadlines

**Next 12 months (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 1040-ES (members, prior year) |
| Jan 31 | W-2, W-3, 1099-NEC (if employer) |
| **Mar 15** | **Form 1065 + K-1s** |
| Apr 15 | Q1 1040-ES (members) |
| Apr 30 | Q1 Form 941 (if employer) |
| Jun 15 | Q2 1040-ES (members) |
| Jul 31 | Q2 Form 941 |
| Sep 15 | Q3 1040-ES (members); extended Form 1065 |
| Oct 31 | Q3 Form 941 |
| Jan 15 (next yr) | Q4 1040-ES (members) |

---

## owner-compensation

⚠️ **MEMBERS CAN'T BE ON W-2 PAYROLL**

LLC-multi (taxed as partnership) — members are NOT employees. Payments to members categorized as:

### 1. Guaranteed Payments
- Compensation for services regardless of partnership profit
- Like salary BUT:
  - Reported on K-1 Box 4 (NOT W-2)
  - Subject to SE tax (member pays both halves)
  - Member pays own income tax (no withholding)
  - DEDUCTIBLE to LLC (reduces partnership income)

### 2. Distributive Share (Allocation of Profit)
- Member's % share of partnership income/loss
- Reported on K-1 Box 1 (ordinary business income)
- Active members: Subject to SE tax on full share
- Limited partners: Generally NOT subject to SE tax on share

### 3. Distributions (Cash to Member)
- Actual cash transferred to member
- Up to capital account basis: NOT taxable (return of capital)
- Beyond basis: Taxable as gain
- Distributions don't affect taxable income (already taxed via K-1)

### Tax Burden Example
**Member's share: 50% of $200K partnership profit + $60K guaranteed payment**

Member's K-1:
- Box 1 (ordinary income): $100,000 (50% of remaining $200K)
- Box 4 (guaranteed payments): $60,000
- Total taxable: $160,000

Member's tax:
- SE tax: 15.3% × 92.35% × $160K = $22,608
- Income tax: variable
- Plus Additional Medicare 0.9% if AGI >$200K

### Documentation Required
- Operating Agreement specifying:
  - Profit/loss allocation
  - Guaranteed payment terms
  - Distribution priorities
- Capital account ledger per member
- Form K-1 issued by March 15

### Section 199A QBI Deduction
- Available to LLC members (pass-through income qualifies)
- Same phase-out thresholds as other pass-throughs

---

## owner-comp-protocol

**AI MUST when processing `owner-comp` form for LLC-multi member:**

1. Categorize payment: guaranteed payment vs distribution vs capital return
2. **Guaranteed Payment** journal entry:
   ```
   Dr. 6800 - Guaranteed Payments to Partners    $XXX.XX
       Cr. [Cash account]                                $XXX.XX
   ```
3. **Distribution** journal entry:
   ```
   Dr. 3501 - Member [Name] Distributions    $XXX.XX
       Cr. [Cash account]                            $XXX.XX
   ```
4. NO W-2 issued to member (this is the #1 mistake — partnerships don't payroll members)
5. NO payroll tax withheld (member self-pays via 1040-ES)
6. Update member's capital account
7. Verify allocation matches Operating Agreement (% may differ from ownership %)
8. Track YTD by member for K-1 prep
9. Save documentation to: `05_Payroll/Member_Compensation/`

**File naming:** `YYYYMMDD_MemberComp_[MemberName]_FY{year}.xlsx`

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Member added to W-2 payroll → MAJOR ERROR (not allowed in LLC-multi default treatment)
- ⚠️ Distribution to member exceeding capital account basis → taxable gain (need to flag)
- ⚠️ Profit allocation doesn't match Operating Agreement → audit risk
- ⚠️ Special allocation without "substantial economic effect" documentation → IRS may reallocate
- ⚠️ Capital account imbalance → 1065 K-1 will show errors
- ⚠️ Form 1065 not filed by March 15 → $235/member/month late penalty (max 12 months)
- ⚠️ K-1 not issued to member by March 15 → same penalty + member can't file 1040 timely
- ⚠️ Single member functionally (other members nominal) → IRS may reclassify as LLC-single
- ⚠️ Foreign member → withholding tax obligations (Form 8804/8805)
- ⚠️ New member admitted mid-year without proper allocation → 706 short-period issue
- ⚠️ Member loan to LLC at non-AFR rate → imputed interest issue

---

## validation-rules

### LLC-multi Specific Validation

- **Member count:** Must be ≥2 members (else convert to LLC-single rules)
- **K-1 issuance:** Verify all members receive K-1 by March 15
- **Capital account reconciliation:** Beginning + Contributions + Allocations - Distributions = Ending
- **Pro-rata vs special allocation:** If special, verify Operating Agreement permits
- **Foreign member withholding:** 37% (or treaty rate) on effectively connected income
- **Tax matters representative (TMP):** Must designate per BBA partnership audit rules (since 2018)
- **State partnership filing:** Most states require state-level partnership return separately

---

## estimated-tax

**Pass-through structure:** LLC-multi does NOT pay federal entity income tax. Each member pays personal estimated tax on their K-1 share.

### Member-Level Estimated Tax

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | Form 1040-ES |
| Q2 | June 15 | Form 1040-ES |
| Q3 | September 15 | Form 1040-ES |
| Q4 | January 15 (next year) | Form 1040-ES |

### Calculation per Member
**Estimated tax = (Income tax on K-1 share + SE tax on share + Additional Medicare) ÷ 4**

### Safe Harbor (per member)
- 100% of prior year tax (110% if AGI >$150K), OR
- 90% of current year tax

### State PTE (Pass-Through Entity) Tax Election
- Many states (including CA, NY) allow LLC to elect entity-level state tax
- Workaround for $10K SALT deduction cap
- Members get state tax credit for entity-paid tax
- Worth evaluating annually with CPA

**AI MUST when processing `estimated-tax` form for LLC-multi:**
1. Confirm payment is for MEMBER (Form 1040-ES), NOT entity
2. Exception: state-level PTE election if applicable
3. Allocate based on K-1 share
4. Account for guaranteed payments separately
5. Calculate SE tax + income tax + additional Medicare
6. Track YTD member-by-member
7. Recommend CPA for amounts >$10K/quarter
