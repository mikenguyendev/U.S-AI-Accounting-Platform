# Florida (FL) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/FL.md#section-id}}` directives.**

**State:** Florida
**Tax Authority:** Florida Department of Revenue (DOR), Florida Department of Economic Opportunity (DEO)
**Last Updated:** 2026-04-22

> **🎯 KEY ADVANTAGE:** Florida có **NO state personal income tax**. Corporate income tax 5.5% chỉ áp dụng cho C-Corps. Pass-through entities (S-Corp, LLC, Partnership) hoàn toàn tax-free at state level for owners. Top destination cho high-income business owner relocation.

---

## tax-obligations

### Key Florida Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **FL Corporate Income Tax (C-Corp only)** | 5.5% on net income (>$50K exemption) | DOR | May 1 (Form F-1120) |
| **FL Personal Income Tax** | **0%** (NO state personal income tax) | N/A | N/A |
| **FL Sales & Use Tax** | 6% state + up to 2.5% local (max 8.5%) | DOR | Monthly/Quarterly |
| **FL Reemployment Tax (SUTA)** | 0.1%–5.4% on first $7,000 wages | DEO | Quarterly (Form RT-6) |
| **No SDI** | N/A (Florida does NOT have State Disability Insurance) | N/A | N/A |
| **Workers' Compensation** | MANDATORY for most employers (4+ employees in non-construction; 1+ in construction) | DFS | Per pay period |
| **FL Documentary Stamp Tax** | $0.70 per $100 (deed) / $0.35 per $100 (notes) | DOR | At transaction |
| **FL Tangible Personal Property Tax** | Varies by county (typical 0.5%-2%) | County | April 1 |

> **⚠️ IMPORTANT:** S-Corps, Partnerships, LLCs in FL DO NOT pay state income tax. Only C-Corps pay 5.5% corporate tax.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 FL Reemployment Tax | RT-6 |
| **April 1** | Tangible Personal Property Tax Return | DR-405 |
| **April 30** | Q1 FL Reemployment Tax | RT-6 |
| **May 1** | **FL Corporate Income Tax (C-Corp only)** | F-1120 |
| **July 31** | Q2 FL Reemployment Tax | RT-6 |
| **October 31** | Q3 FL Reemployment Tax | RT-6 |

**Sales tax filing frequency:**
- Monthly: annual liability >$1,000
- Quarterly: $501–$1,000 annual
- Semi-annual: $101–$500 annual
- Annual: ≤$100/year

**Sales tax due:** 20th of month following filing period.

---

## upcoming-deadlines

**Next 12 months FL-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 31 | Q4 RT-6 |
| Apr 1 | Tangible Personal Property Tax (DR-405) |
| Apr 30 | Q1 RT-6 |
| **May 1** | **F-1120 (C-Corp only)** |
| Jul 31 | Q2 RT-6 |
| Oct 31 | Q3 RT-6 |

---

## critical-reminders

- ⚠️ **No state personal income tax** — major reason for relocation from CA/NY/NJ
- ⚠️ **C-Corps STILL pay 5.5%** state corporate tax (verify entity type before assuming "tax-free")
- ⚠️ **Sales tax permit required** — Florida Department of Revenue (online application, free)
- ⚠️ **Tangible Personal Property Tax** — annual filing if business owns equipment >$25K (county-level)
- ⚠️ **Workers' Comp threshold:** 4+ employees (non-construction) OR 1+ employee (construction)
- ⚠️ **No SDI, no PFML** — Florida is one of few states without state-mandated paid leave programs
- ⚠️ **FL minimum wage** — $13.00/hour (2025), increasing to $14.00 (Sept 2026), $15.00 (Sept 2026 — verify)
- ⚠️ **Documentary Stamp Tax** — sneaky tax on deeds + promissory notes (often missed in real estate transactions)
- ⚠️ **No reciprocity** since no income tax — out-of-state remote workers withhold for their state of residence
- ⚠️ **Hurricane prep:** State + IRS may grant deadline extensions during declared emergencies — check FEMA + IRS notices

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ C-Corp not filing F-1120 by May 1 → late penalty + interest
- ⚠️ Sales tax collected without DOR permit → operating illegally
- ⚠️ Hire 4th employee (non-construction) without Workers' Comp → state stop-work order + fines
- ⚠️ Tangible Personal Property >$25K without DR-405 filing → $1,000+ penalty
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into FL → economic nexus
- ⚠️ Real estate transaction missing Documentary Stamp Tax → recording delay + penalty
- ⚠️ Out-of-state remote employee for FL employer → no FL withholding (FL has none) but check employee's state

---

## validation-rules

### FL-Specific Validation

- **Corporate tax exemption:** First $50,000 of net income exempt for C-Corps
- **Sales tax sourcing:** Destination-based for most transactions
- **Sales tax exemptions:** Many — groceries, prescription drugs, agricultural items, manufacturing machinery
- **No reciprocity issues** since no income tax
- **Minimum wage:** Verify current rate (escalating annually through 2026)
- **Tip credit:** Allowed (tipped wages $9.98/hour with tip credit, must reach $13/hour total)

---

## sales-tax

**Florida Sales & Use Tax**

- **Authority:** Florida Department of Revenue (DOR)
- **Base rate:** 6% state
- **Local taxes:** Up to 2.5% additional discretionary surtax (county-level)
- **Total range:** 6%–8.5%
- **Permit required:** Florida Sales Tax Number from DOR (online, free)
- **What's taxable:**
  - Tangible personal property
  - Some services (commercial cleaning, detective, security)
  - Hotel/lodging (transient)
  - Admissions to entertainment
  - Prepared food (restaurants)
- **What's NOT taxable:**
  - Most professional services (legal, medical, accounting, consulting)
  - Groceries (unprepared)
  - Prescription drugs
  - Agricultural products
  - Manufacturing machinery (with exemption certificate)
  - Newspapers
- **Filing frequency:**
  - Monthly: annual liability >$1,000
  - Quarterly: $501-$1,000
  - Semi-annual: $101-$500
  - Annual: ≤$100
- **Due date:** 20th of month following filing period
- **Surtax cap:** $5,000 surtax cap on single sale of tangible property over $5K (most counties)

**Online filing:** Required for businesses with >$20K annual liability.

---

## estimated-tax

**No state personal income tax = no state estimated tax for OWNERS of pass-through entities.**

**For C-Corps owing >$2,500 in FL corporate tax:**

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | May 1 (estimated) | F-1120ES |
| Q2 | July 1 | F-1120ES |
| Q3 | October 1 | F-1120ES |
| Q4 | January 1 (next year) | F-1120ES |

**Calculation:** Generally 25% of expected annual liability per quarter.

**Safe Harbor:** 100% of prior year tax (if business had FL nexus prior year).

**AI MUST when processing `estimated-tax` form for FL:**
1. Confirm entity type:
   - C-Corp: file F-1120ES quarterly
   - S-Corp/LLC/Partnership/Sole Prop: NO Florida state estimated tax
2. Owners of pass-through entities: only federal estimated tax (Form 1040-ES)
3. If owner is FL resident: significant tax savings vs CA/NY/NJ
4. Multi-state filers: track per-state estimated tax separately

---

## withholding-form

**FL has NO state personal income tax → NO state withholding form**

- Federal W-4 only
- I-9 within 3 days of hire
- New Hire Reporting via Florida Child Support Program within 20 days

**No state withholding tax to calculate or remit.**

---

## withholding-tables

**N/A — Florida has no state income tax withholding.**

Federal withholding only:
- Use IRS Pub 15-T (2026)
- Calculation methods: percentage method or wage bracket method

**Special situations:**
- Bonuses: Federal supplemental rate 22% (no state addition)
- Out-of-state remote workers for FL employer: Withhold based on workplace state, not residence (typically)

---

## payroll-taxes

### Employer-Side FL Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **FL Reemployment Tax (SUTA)** | 0.1%–5.4% | First $7,000 | New employer 2.7% Year 1 |
| **No SDI** | N/A | N/A | Florida does not have State Disability Insurance |
| **No state income tax withholding** | N/A | N/A | Federal only |
| **No PFML** | N/A | N/A | Florida has no state paid family/medical leave |

### New Employer Default Rates
- New employer Reemployment Tax: 2.7% for first 10 quarters (then experience-rated)
- No state minimum wage law beyond federal $7.25 — but FL constitutional amendment sets higher

### Quarterly Reporting
- **Form RT-6** — Florida Quarterly Tax and Wage Report
- Due: Last day of month after quarter end (Apr 30, Jul 31, Oct 31, Jan 31)

### E-file
- Required for employers with 10+ employees
- Recommended for all (DEO online portal)

### Other FL Employment Requirements
- New Hire Reporting: Within 20 days (Florida Child Support Program)
- Workers' Comp: MANDATORY (4+ non-construction, 1+ construction)
- E-Verify: REQUIRED for all FL employers (since 2023)

---

## entity-specific-tax

### S-Corporation in FL
- **NO state income tax** at entity level (FL doesn't tax pass-through entities)
- **NO state income tax** for shareholders (no FL personal income tax)
- Federal Form 1120-S still required
- ✅ Most tax-favorable state for S-Corp owners

### C-Corporation in FL
- **FL Corporate Income Tax: 5.5%** on net income (after $50K exemption)
- Form F-1120 due May 1
- Quarterly estimated tax via F-1120ES if liability >$2,500
- Federal Form 1120 still required

### LLC in FL
- **NO state income tax** (LLC pass-through)
- LLC formation fee: $125 (one-time, FL Secretary of State)
- Annual report fee: $138.75 (due May 1 — late = $400 fine)
- Members file federal Form 1065 (multi) or Schedule C (single) — no FL state filing

### Partnership in FL
- **NO state income tax**
- Federal Form 1065 + K-1s
- General Partnership: no state filing
- LP/LLP: register with FL DOS, annual report

### Sole Proprietor in FL
- **NO state income tax** (or any state filing)
- Just federal Schedule C
- Optional: DBA registration ($50, county-level)
- Best state for solo entrepreneurs

### Out-of-State Entities Operating in FL
- Must register with FL Secretary of State if doing business in FL
- C-Corps subject to FL Corporate Income Tax based on FL-apportioned income
- Sales tax nexus rules apply
