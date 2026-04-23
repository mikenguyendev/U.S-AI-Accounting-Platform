# Washington (WA) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/WA.md#section-id}}` directives.**

**State:** Washington
**Tax Authority:** Washington Department of Revenue (DOR), Employment Security Department (ESD), Department of Labor & Industries (L&I)
**Last Updated:** 2026-04-22

> **🎯 UNIQUE TAX MODEL:** Washington có **NO state income tax** but has the unusual **Business & Occupation (B&O) Tax** — gross receipts tax on revenue regardless of profit. Plus high sales tax (6.5%+) and unique L&I Workers' Comp run by the state (not private).

---

## tax-obligations

### Key Washington Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **WA B&O Tax (Business & Occupation)** | 0.13%–3.3% on gross revenue (varies by classification) | DOR | Monthly/Quarterly/Annual |
| **WA Personal Income Tax** | **0%** (NO state personal income tax) | N/A | N/A |
| **WA Capital Gains Tax** | 7% on long-term gains >$262K (2024 threshold; verify 2026) | DOR | April 15 |
| **WA Sales & Use Tax** | 6.5% state + up to 4.1% local (Seattle 10.35%) | DOR | Same as B&O |
| **WA SUI (Unemployment)** | 0.27%–6.03% on first $72,800 wages (2026) | ESD | Quarterly |
| **WA L&I (Workers' Comp)** | Hourly rate by risk class (state monopoly) | L&I | Quarterly |
| **WA PFML (Paid Family & Medical Leave)** | 0.74% of wages (employer + employee shared 28.57%/71.43%) | ESD | Quarterly |
| **WA Cares Fund (Long-Term Care)** | 0.58% of wages (employee only, opt-out window passed) | ESD | Per pay period |

> **⚠️ CRITICAL:** B&O Tax = gross receipts tax. Pay even when business is unprofitable. Major consideration for low-margin businesses.

### B&O Tax Classifications (Common)

| Classification | Rate |
|----------------|------|
| Retailing | 0.471% |
| Wholesaling | 0.484% |
| Service & Other Activities | 1.5% (or 1.75% if income >$1M) |
| Manufacturing | 0.484% |
| Professional Services | 1.5% (or 1.75% if income >$1M) |
| Insurance Agent Commissions | 1.5% |

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 WA combined excise (B&O + sales) + Q4 SUI | Combined Excise Tax Return |
| **April 15** | WA Capital Gains Tax | DOR online filing |
| **April 30** | Q1 WA combined excise + Q1 SUI | Combined Excise Tax Return |
| **April 30** | Q1 PFML report | ESD portal |
| **April 30** | Q1 L&I quarterly report | L&I portal |
| **July 31** | Q2 WA combined excise + Q2 SUI + PFML + L&I | Same |
| **October 31** | Q3 WA combined excise + Q3 SUI + PFML + L&I | Same |

**B&O/Sales tax filing frequency:**
- Monthly: annual liability >$4,800
- Quarterly: $1,050-$4,800
- Annual: <$1,050

**Due:** 25th of month following filing period (most common).

---

## upcoming-deadlines

**Next 12 months WA-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 Combined Excise + SUI + L&I + PFML |
| **Apr 15** | **WA Capital Gains Tax** |
| Apr 30 | Q1 Combined Excise + SUI + L&I + PFML |
| Jul 31 | Q2 reports |
| Oct 31 | Q3 reports |

---

## critical-reminders

- ⚠️ **B&O Tax on gross revenue** — pay even when losing money. High burden for low-margin businesses
- ⚠️ **No income tax BUT 7% capital gains tax** on long-term gains >$262K (passed 2021, court-upheld 2023)
- ⚠️ **L&I (Workers' Comp) is STATE MONOPOLY** — must use state insurance fund (not private). Hourly rate by risk class
- ⚠️ **PFML mandatory** since 2020 (0.74% combined employer+employee)
- ⚠️ **WA Cares Fund** — 0.58% employee tax for long-term care (opt-out window closed 2021)
- ⚠️ **Sales tax very high** — Seattle 10.35%, statewide minimum 6.5%
- ⚠️ **Sales tax destination-based** since 2008 — collect based on buyer's location
- ⚠️ **Unemployment wage base $72,800 (2026)** — much higher than most states
- ⚠️ **WA minimum wage $16.66/hour (2025)** — verify 2026; cities like Seattle ($20.76 large employer) higher
- ⚠️ **Paid sick leave** — 1 hour per 40 worked, accrual no cap (state law)
- ⚠️ **No reciprocity** — out-of-state remote workers withhold for their state

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ Operating in WA without B&O tax registration → fines + back taxes
- ⚠️ B&O classification incorrect (using lower rate when higher applies) → audit assessment
- ⚠️ Capital gains transaction not reported → 7% tax + penalty
- ⚠️ L&I rate not paid quarterly → state can suspend Workers' Comp coverage
- ⚠️ PFML premiums not withheld/remitted → fines + employee claims unfunded
- ⚠️ Hire WA employee without PFML deduction setup → premium liability still owed
- ⚠️ Sales tax sourcing incorrect (origin vs destination) → significant audit exposure
- ⚠️ WA Cares Fund deduction missed → employee tax liability falls on employer
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into WA → economic nexus
- ⚠️ B&O credit/exemption not claimed (e.g., small business credit, manufacturing) → overpayment

---

## validation-rules

### WA-Specific Validation

- **B&O classification:** Use correct activity code (DOR has detailed lookup)
- **Multiple activities:** If business has multiple revenue streams, classify each separately
- **B&O credits:** Small Business Credit available (sliding scale)
- **Sales tax sourcing:** Destination-based (buyer's address)
- **Sales tax exemptions:** Most professional services, some manufacturing inputs
- **L&I risk classifications:** Audit annually — wrong class = wrong rate
- **PFML wage cap:** $168,600 (matches federal SS cap, 2026)
- **Capital gains exemptions:** Real estate, retirement accounts, certain small business stock

---

## sales-tax

**Washington Sales & Use Tax**

- **Authority:** Washington DOR
- **Base rate:** 6.5% state
- **Local taxes:** Up to 4.1% additional
- **Total range:** 6.5%–10.35% (Seattle highest)
- **Sourcing:** Destination-based (since 2008)
- **Permit required:** Combined Business License Application (DOR + 50+ city/state agencies)
- **What's taxable:**
  - Tangible personal property
  - Some services (construction, telecom, repair, landscaping)
  - Digital goods (since 2009)
  - Restaurant meals
- **What's NOT taxable:**
  - Most professional services (legal, medical, accounting)
  - Groceries (unprepared)
  - Prescription drugs
  - Manufacturing machinery (with certificate)
- **Filing frequency:** Same as B&O (combined excise tax return)
- **Due date:** 25th of month following filing period

**Use tax:** Self-assess on out-of-state purchases used in WA where no sales tax was charged.

**City B&O Tax:** Some cities (Seattle, Bellevue, Tacoma) ALSO impose city-level B&O on top of state — additional filing.

---

## estimated-tax

**No state personal income tax = no state estimated tax for owners.**

**B&O Tax:** Filed and paid with regular sales tax return (no separate quarterly estimate).

**Capital Gains Tax:**
- 7% on long-term gains >$262K threshold
- Filed with annual return April 15
- No quarterly estimates (annual lump sum)

**For C-Corps:**
- B&O Tax only at state level (no separate state corporate income tax)
- Federal Form 1120 estimated tax (Form 1120-W) still required

**AI MUST when processing `estimated-tax` form for WA:**
1. Confirm: NO Washington state income tax estimated payments needed
2. B&O Tax paid with regular monthly/quarterly excise return
3. If owner has long-term capital gains >$262K → Capital Gains Tax due April 15
4. Owners of pass-through entities: no WA state estimated tax (only federal 1040-ES)
5. Multi-state filers: track per-state separately

---

## withholding-form

**WA has NO state personal income tax → NO state withholding form**

- Federal W-4 only
- I-9 within 3 days of hire
- New Hire Reporting via Washington State Support Registry within 20 days

**However, WA requires:**
- WA Cares Fund deduction setup (0.58% from employee paycheck)
- PFML premium deduction (employee share of 0.74%)

---

## withholding-tables

**N/A — Washington has no state income tax withholding.**

Federal withholding only:
- Use IRS Pub 15-T (2026)

**Special situations:**
- Bonuses: Federal supplemental rate 22%
- Out-of-state remote workers for WA employer: Withhold for their state of residence
- WA Cares Fund: 0.58% on all wages (employee deduction)
- PFML premium: Employee share of 0.74% (split with employer)

---

## payroll-taxes

### Employer-Side WA Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **WA SUI (Unemployment)** | 0.27%–6.03% | First $72,800 (2026) | New employer ~1.5% |
| **WA L&I (Workers' Comp)** | Per hour by risk class | All hours | STATE MONOPOLY (no private option) |
| **WA PFML (employer share)** | 0.21% (28.57% of 0.74%) | $168,600 cap | Mandatory since 2020 |
| **WA PFML (employee share)** | 0.53% (71.43% of 0.74%) | $168,600 cap | Withhold from employee |
| **WA Cares Fund** | 0.58% | All wages | EMPLOYEE only (no opt-out anymore) |
| **No state income tax withholding** | N/A | N/A | Federal only |

### New Employer Default Rates
- New employer SUI: ~1.5% Year 1 (then experience-rated)
- L&I: Risk class assigned based on industry (must report accurately)
- WA minimum wage: $16.66/hour (2025) — verify 2026 + city minimums (Seattle $20.76 large)

### Quarterly Reporting
- **Combined Excise Tax Return** (DOR) — B&O + sales tax
- **EAMS** (ESD) — SUI + PFML reporting
- **L&I Quarterly Report** — Workers' Comp hours + premium
- All due: Last day of month after quarter end

### E-file
- Required for all WA employers
- Use My DOR (Department of Revenue) + EAMS (Employment Security)

### Other WA Employment Requirements
- New Hire Reporting: 20 days
- Workers' Comp: MANDATORY via L&I (state monopoly)
- WA Cares Fund: All employees automatically enrolled
- Paid Sick Leave: 1 hour per 40 worked
- Paid Family/Medical Leave: Up to 12 weeks/year

---

## entity-specific-tax

### S-Corporation in WA
- **B&O Tax: ~1.5%** (Service classification) on gross revenue
- NO state income tax for entity OR shareholders
- Federal Form 1120-S still required
- WA Capital Gains Tax may apply if shareholder sells stock at gain

### C-Corporation in WA
- **B&O Tax: ~1.5%** on gross revenue (Service) — gross, not net
- NO traditional state corporate income tax
- Federal Form 1120 still required

### LLC in WA
- **B&O Tax** based on activity classification
- NO state income tax (pass-through)
- LLC formation: $200 (Secretary of State)
- Annual Report: $60 (Secretary of State)
- Federal Form 1065/Schedule C

### Partnership in WA
- **B&O Tax** based on activity
- NO state income tax (pass-through)
- LP/LLP: register with WA Secretary of State

### Sole Proprietor in WA
- **B&O Tax** even for sole prop (gross revenue tax)
- NO state income tax
- Federal Schedule C

### Out-of-State Entities Operating in WA
- B&O Tax applies if >$100K WA sales OR 200+ transactions (economic nexus)
- L&I + SUI for any WA-based employees
- PFML for any WA workers
