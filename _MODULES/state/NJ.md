# New Jersey (NJ) — State Module

> **Module này được include vào templates qua `{{INCLUDE:_MODULES/state/NJ.md#section-id}}` directives.**

**State:** New Jersey
**Tax Authority:** NJ Division of Taxation, NJ Department of Labor and Workforce Development (LWD)
**Last Updated:** 2026-04-22

> **⚠️ HIGH-TAX STATE:** NJ có high personal income tax (top 10.75%), high property tax, multiple employee benefit programs (NJ FLI, TDI, FLI). Strong worker protections, mandatory paid sick leave + family leave. Adjacent NY state but with own tax structure.

---

## tax-obligations

### Key New Jersey Tax Obligations

| Item | Rate / Amount | Authority | Deadline |
|------|---------------|-----------|----------|
| **NJ Corporate Business Tax (CBT)** | 9% (>$100K), 7.5% ($50K-$100K), 6.5% (<$50K) | Div of Tax | April 15 |
| **NJ Surtax on CBT** | 2.5% on income >$10M (sunsets eventually) | Div of Tax | April 15 |
| **NJ Personal Income Tax** | Progressive 1.4%–10.75% | Div of Tax | April 15 (Form NJ-1040) |
| **NJ Sales & Use Tax** | 6.625% statewide (uniform) | Div of Tax | Monthly/Quarterly |
| **NJ SUI (Unemployment)** | 0.5%–6.4% on first $43,300 (2026) | LWD | Quarterly |
| **NJ TDI (Temporary Disability)** | 0.0% employer (2025); employee 0.0% (eliminated 2023) | LWD | Per pay period |
| **NJ FLI (Family Leave Insurance)** | 0.09% employee only (2025) on first $165,400 | LWD | Per pay period |
| **NJ Workforce Development** | 0.0425% employer | LWD | Per pay period |
| **NJ Healthcare Subsidy** | 0.0% (sunset 2024) | LWD | N/A |
| **Workers' Compensation** | MANDATORY for all employers (1+ employee) | NJ Compensation Bureau | Per pay period |

> **⚠️ IMPORTANT:** NJ recently eliminated TDI employee contribution (2023) and continues adjusting rates. Verify current year rates with LWD.

---

## deadlines

| Date | Action | Form |
|------|--------|------|
| **January 31** | Q4 NJ payroll return | NJ-927 |
| **March 15** | NJ S-Corp / Partnership return | CBT-100S, NJ-1065 |
| **April 15** | NJ C-Corp tax return | CBT-100 |
| **April 15** | NJ Personal Income Tax | NJ-1040 |
| **April 30** | Q1 NJ payroll return | NJ-927 |
| **June 15** | Q2 NJ personal estimated tax | NJ-1040-ES |
| **July 31** | Q2 NJ payroll return | NJ-927 |
| **September 15** | Q3 NJ personal estimated tax | NJ-1040-ES |
| **October 31** | Q3 NJ payroll return | NJ-927 |
| **January 15** | Q4 NJ personal estimated tax | NJ-1040-ES |

**Sales tax filing:** Monthly (most), Quarterly (smaller).
**Sales tax due:** 20th of month following filing period.

---

## upcoming-deadlines

**Next 12 months NJ-specific (rolling — verify against `{{COMPUTED:TODAY}}`):**

| Date | Action |
|------|--------|
| Jan 15 | Q4 personal estimated (prior year) |
| Jan 31 | Q4 NJ-927 |
| **Mar 15** | NJ S-Corp / Partnership |
| **Apr 15** | NJ C-Corp + Personal Income |
| Apr 30 | Q1 NJ-927 |
| Jun 15 | Q2 personal estimated |
| Jul 31 | Q2 NJ-927 |
| Sep 15 | Q3 personal estimated |
| Oct 31 | Q3 NJ-927 |

---

## critical-reminders

- ⚠️ **Top NJ personal income tax rate 10.75%** — among highest in nation (after CA, HI, NY)
- ⚠️ **NJ CBT 9% top rate** — significant on profitable C-Corps
- ⚠️ **NJ Earned Sick Leave Law** — mandatory, 1 hour per 30 worked, max 40 hours/year
- ⚠️ **NJ Paid Family Leave** — up to 12 weeks, funded by employee (FLI premium 0.09%)
- ⚠️ **NJ Temporary Disability Insurance** — up to 26 weeks (employer pays starting 2024)
- ⚠️ **PTE Tax (BAIT) election** — strongly recommended for SALT cap workaround
- ⚠️ **NJ minimum wage $15.49/hour (2025)** — verify 2026 rate; agricultural lower
- ⚠️ **Workers' Comp mandatory** for any employer (1+ employee, including part-time)
- ⚠️ **Sales tax uniform statewide** at 6.625% (no city/county additions — simpler than CA/IL)
- ⚠️ **Property tax very high** — average effective 2.46% (highest in nation)
- ⚠️ **NJ does have reciprocity với PA** for personal income tax (but only PA, not NY/DE)
- ⚠️ **NJ Domestic Workers Bill of Rights** — special protections for household workers
- ⚠️ **Wage Theft Prevention Act** — enhanced employer record-keeping requirements

---

## flag-conditions

AI Agent flag warnings cho:

- ⚠️ NJ employer not deducting FLI premium → benefits unfunded for employees
- ⚠️ Hire NJ employee without Workers' Comp → state penalties + criminal liability
- ⚠️ NJ Sick Leave hours not tracked/granted → fines $250-$2,500 per violation
- ⚠️ PTE BAIT election deadline missed (March 15) → no SALT workaround
- ⚠️ Sales tax permit missing → operating illegally
- ⚠️ Multi-state nexus: $100K sales OR 200 transactions into NJ → economic nexus
- ⚠️ NJ minimum wage not honored ($15.49+) → wage theft action + treble damages
- ⚠️ Misclassifying NJ worker as 1099 (NJ ABC test stricter than IRS) → audit + back wages + penalties
- ⚠️ TDI premium not remitted → employee benefits unfunded
- ⚠️ NJ-PA reciprocity not honored for cross-border employees → over/under withholding

---

## validation-rules

### NJ-Specific Validation

- **CBT progressive rates:** <$50K = 6.5%, $50K-$100K = 7.5%, >$100K = 9%
- **Surtax:** 2.5% additional on CBT income >$10M
- **PTE BAIT election:** Must elect annually, by March 15
- **NJ-PA reciprocity:** PA residents working in NJ can elect to pay only PA tax (Form NJ-165)
- **ABC test for worker classification:** All 3 prongs must be met to be 1099 (stricter than IRS)
- **Sales tax sourcing:** Destination-based
- **Sales tax exemptions:** Clothing (no tax), groceries (no tax), prescriptions, manufacturing
- **Minimum wage tracking:** Standard, agricultural, seasonal, tipped — different rates

---

## sales-tax

**New Jersey Sales & Use Tax**

- **Authority:** NJ Division of Taxation
- **Rate:** **6.625% uniform statewide** (no local sales tax in NJ — simpler than most states)
- **Permit required:** Certificate of Authority from NJ Division of Taxation (free, online)
- **What's taxable:**
  - Tangible personal property
  - Some services (telecom, accommodations, parking, repair)
  - Prepared food (restaurants)
  - Digital products
- **What's NOT taxable:**
  - Most professional services
  - Clothing/footwear (NJ unique — no tax on clothing!)
  - Groceries (unprepared)
  - Prescription drugs
  - Newspapers
- **Filing frequency:**
  - Monthly: liability >$30,000/year
  - Quarterly: $500-$30,000/year
  - Annual: <$500/year
- **Due date:** 20th of month following filing period

**Notable:** NJ Urban Enterprise Zones (UEZ) have reduced 3.3125% rate (half) for qualified retailers.

---

## estimated-tax

### NJ CBT (C-Corp + Other Entities Subject to CBT)

For entities owing >$500 in NJ CBT:

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | CBT-150 |
| Q2 | June 15 | CBT-150 |
| Q3 | September 15 | CBT-150 |
| Q4 | December 15 | CBT-150 |

### NJ Personal Income Tax

| Quarter | Due Date | Form |
|---------|----------|------|
| Q1 | April 15 | NJ-1040-ES |
| Q2 | June 15 | NJ-1040-ES |
| Q3 | September 15 | NJ-1040-ES |
| Q4 | January 15 | NJ-1040-ES |

### PTE Tax Election (BAIT)

- NJ pass-through entities can elect Business Alternative Income Tax (BAIT)
- Strong SALT cap workaround
- Election made annually by March 15
- Quarterly entity-level estimated payments

**AI MUST when processing `estimated-tax` form for NJ:**
1. Distinguish entity type
2. C-Corp: CBT-150 quarterly
3. Pass-through: depends on BAIT election
4. Owners: NJ-1040-ES quarterly (combined with NJ + city if applicable)
5. Verify PTE BAIT election status

---

## withholding-form

**NJ Employee State Withholding Form: NJ-W4**

- **Purpose:** Determines NJ state income tax withholding
- **Default if no NJ-W4:** Single, 0 allowances
- **Update:** Employee can submit anytime
- **PA reciprocity:** PA residents working in NJ file Form NJ-165 to be exempt from NJ withholding (PA only)

**Required at hire:**
- Federal W-4 + NJ-W4
- I-9 (within 3 days)
- New Hire Reporting via NJ Child Support within 20 days

---

## withholding-tables

**NJ Withholding Calculation:**

Use NJ Division of Taxation NJ-WT (Employer Withholding Tax Tables, annually updated).

- Progressive brackets: 1.4%–10.75%
- Standard deduction by filing status
- Multiple withholding methods

**Tools:**
- NJ Division of Taxation Withholding Calculator
- NJ-WT booklet
- Most payroll software handles automatically (NJ + FLI + SUI)

**Special situations:**
- Bonuses: Aggregate or supplemental rate (varies — check NJ-WT)
- Out-of-state remote workers for NJ employer: NJ does have ConvenienceOfEmployer-style rule (varies)

---

## payroll-taxes

### Employer-Side NJ Payroll Taxes

| Tax | Rate | Wage Base | Notes |
|-----|------|-----------|-------|
| **NJ SUI (Unemployment)** | 0.5%–6.4% | First $43,300 (2026) | New employer ~3.4% |
| **NJ Workforce Development** | 0.0425% | First $43,300 | Employer pays |
| **NJ TDI (Temporary Disability)** | 0.0% (2025) | $165,400 cap | Employer rate (employee eliminated 2023) |
| **NJ FLI (Family Leave Insurance)** | 0.09% (2025) | $165,400 cap | EMPLOYEE only |
| **NJ Income Tax PIT** | 1.4%–10.75% | All wages | Employer withholds |

### New Employer Default Rates
- New employer SUI: ~3.4% Year 1
- NJ minimum wage: $15.49/hour (2025) — verify 2026; agricultural $13.40 (2025)

### Quarterly Reporting
- **Form NJ-927** — Combined Quarterly Withholding/Unemployment
- Due: Last day of month after quarter end

### E-file
- Required for employers with 100+ employees
- Recommended for all (NJ ELO portal)

### Other NJ Employment Requirements
- New Hire Reporting: 20 days
- Workers' Comp: MANDATORY (any employer)
- Earned Sick Leave: 1 hour per 30 worked (40 hours max/year)
- Paid Family Leave: Up to 12 weeks (FLI funded)
- Wage Theft Prevention Act compliance

---

## entity-specific-tax

### S-Corporation in NJ
- **NJ does NOT automatically recognize federal S-Corp election** — must file CBT-2553 separately
- If NJ S-election made: CBT minimum tax based on gross receipts ($375-$2,000)
- Federal Form 1120-S still required
- Shareholders: NJ personal tax on K-1
- Strongly recommend BAIT election

### C-Corporation in NJ
- **NJ CBT: 9%** (>$100K), 7.5% ($50K-$100K), 6.5% (<$50K)
- **Surtax: 2.5%** on income >$10M
- CBT minimum tax: $375-$2,000 (based on gross receipts)
- Form CBT-100 due April 15

### LLC in NJ
- **CBT** if elected as corporation; otherwise pass-through
- LLC formation: $125 (NJ Division of Revenue)
- Annual Report: $75
- Federal Form 1065/Schedule C
- BAIT election available

### Partnership in NJ
- **No entity-level income tax** (pass-through)
- LP/LLP: register with NJ
- Federal Form 1065 + K-1s
- BAIT election available

### Sole Proprietor in NJ
- No entity tax filing
- NJ personal income tax via NJ-1040
- Just federal Schedule C

### Out-of-State Entities Operating in NJ
- Subject to NJ CBT based on apportionment
- Sales tax nexus rules apply
- Foreign Qualification required
