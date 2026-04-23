# 🚀 Quickstart Guide — For Beginners (No IT Skills Needed)

> **This guide is for business owners, NOT programmers.** No coding. No command line. No technical jargon. If you can use email and a web browser, you can use this system.

**Languages:** 🇬🇧 English (this file) • 🇻🇳 [Tiếng Việt](QUICKSTART.vi.md) • 🇪🇸 [Español](QUICKSTART.es.md)

---

## 📋 What You Need Before Starting

Just 3 things — nothing to install:

1. **A web browser** — Chrome, Edge, Safari, or Firefox (you probably already have one)
2. **An AI chat account** — one of these free accounts works:
   - Claude: https://claude.ai (recommended — best for this workspace)
   - ChatGPT: https://chat.openai.com
   - Gemini: https://gemini.google.com
3. **Your company information** — have these ready:
   - Legal business name
   - Entity type (LLC, S-Corp, C-Corp, etc. — your CPA knows this)
   - State where you operate (e.g., California, Texas)
   - Your name + email + phone
   - Fiscal year (usually January–December)

**Time to set up:** 10–15 minutes. One-time only.

---

## 🎯 Part 1: First-Time Setup (10 minutes)

### Step 1: Download the template

1. Go to your GitHub page (or ask whoever gave you this link for the zip file)
2. Click the green button **"Code"** → **"Download ZIP"**
3. Find the downloaded zip file in your Downloads folder
4. **Right-click** the zip → **"Extract All"** → choose a location you'll remember (example: `Desktop/My_Business_Accounting/`)

You should now see a folder with files like `Accounting_Task_Form.html`, `_CONFIG/`, `_CORE/`, etc.

### Step 2: Open the setup wizard

1. Open the folder `_CONFIG`
2. **Double-click** the file `setup_wizard.html`
3. It will open in your web browser, showing a blue-and-white wizard

If it doesn't open automatically: right-click the file → **"Open with"** → choose Chrome or Edge.

### Step 3: Fill the 6-step wizard

The wizard will guide you through 6 screens. Most fields are optional — only fields marked with a red `*` are required.

| Step | What to enter |
|:----:|---------------|
| 1️⃣ Business Identity | Legal name, DBA (if any), EIN (if you have one), entity type, industry |
| 2️⃣ Location & Tax Setup | State of operation (e.g., CA for California), fiscal year |
| 3️⃣ Operations | Accounting software you use (QuickBooks / Excel / Google Sheets), accrual or cash basis, approval thresholds |
| 4️⃣ Owner Info | Your name, email, role (Owner), preferred language |
| 5️⃣ Compliance Snapshot | Check which items you already completed (EIN, BOI filing, state registration, etc.) |
| 6️⃣ Review | Check everything, then click **Download JSON** and **Download Checklist** |

💡 **Don't know an answer?** Leave it blank. You can update later. Contact your CPA for tax-specific questions (entity type, EIN).

### Step 4: Save your workspace

After downloading the 2 files from the wizard:

1. Go back to your template folder
2. Open the `_INSTANCES` folder
3. Create a new folder inside, named after your company (no spaces — use underscores): example `My_Coffee_Shop_LLC`
4. Move the 2 downloaded files (`_BUSINESS_CONFIG.json` and `ONBOARDING_CHECKLIST.md`) into that new folder

Your folder structure should look like this:
```
My_Business_Accounting/
├── _INSTANCES/
│   └── My_Coffee_Shop_LLC/           ← Your workspace lives here
│       ├── _BUSINESS_CONFIG.json     ← Moved from Downloads
│       └── ONBOARDING_CHECKLIST.md   ← Moved from Downloads
├── Accounting_Task_Form.html
└── ... (other template files)
```

### Step 5: Tell AI to build your workspace

1. Open https://claude.ai (or whichever AI you chose)
2. Start a new chat
3. **Upload your template files** (drag-and-drop the whole folder, or zip it first)
4. Copy-paste this exact prompt:

```
I'm setting up a new business workspace from the AI Accounting Template.
My config is at _INSTANCES/{your_folder_name}/_BUSINESS_CONFIG.json

Please read _CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md and follow the 7-step
protocol to render my workspace. When done, show me:
1. A summary of what was created
2. The 3 most urgent items from my onboarding checklist
3. What I should do next
```

Replace `{your_folder_name}` with your actual folder name.

The AI will read the template, understand your business, and create 5–6 personalized documents in your folder. Takes 3–5 minutes.

### Step 6: Verify the setup

1. Go back to your folder in File Explorer
2. Your workspace folder should now have many more files: `README.md`, `COMPANY_PROFILE.md`, `AI_AGENT_MEMORY.md`, etc.
3. Open `README.md` — it should show your company name at the top
4. Open `Accounting_Task_Form.html` (the main one, not the one in `_CONFIG`)
5. The header should display your company name

✅ **You're done with setup!** From now on, you'll use the Task Form + AI chat for daily accounting.

---

## 💬 Part 2: How to Talk to AI (Essential Tips)

### The Golden Rule

**Be specific. Give numbers. Give dates. Give names.**

❌ Bad: *"Record an expense"*
✅ Good: *"Record an expense of $45.80 for lunch at Starbucks with client ABC Corp on April 22, 2026. Paid by business credit card."*

### How to Start Every AI Session

At the beginning of each new AI conversation (not for every message — just the first of the day):

**Copy-paste this prompt:**

```
I'm opening my AI Accounting workspace for {your company name}.

Please read these files in order:
1. _INSTANCES/{your_folder_name}/_BUSINESS_CONFIG.json
2. _INSTANCES/{your_folder_name}/AI_AGENT_MEMORY.md
3. _INSTANCES/{your_folder_name}/COMPANY_PROFILE.md

Then confirm you loaded the context (tell me my entity type, state, fiscal year,
and next tax deadline), and ask what task I want to work on today.
```

AI will read, summarize back to you, and ask what you need. You're ready.

### Using the Task Form (easiest way)

Instead of typing prompts by hand, let the form build them for you:

1. Open `Accounting_Task_Form.html` in your browser
2. Click any of the task buttons (examples: "📥 Record Vendor Invoice", "💳 Expense Entry", "📅 Monthly Close")
3. Fill in the simple form (or just upload a photo for photo-tasks)
4. Click **"Copy to AI"** — the form automatically puts a perfect prompt in your clipboard
5. Paste into your AI chat (press `Ctrl+V` on Windows, `Cmd+V` on Mac)
6. AI will confirm what it understood, then process the task

---

## 📚 Part 3: 5 Daily Case Studies

Real scenarios with exact prompts to copy-paste. These are the 5 most common tasks for a small business.

---

### 📥 Case Study 1: I received a vendor invoice

**Scenario:** Your internet provider sent you a bill for $120. You want to record it so you can pay it next week.

**What you do:**

1. **Take a photo** of the invoice (use your phone) or save the PDF
2. Open your AI chat
3. Copy-paste this prompt + attach the photo:

```
📥 New vendor invoice to record.

Vendor: Comcast Business Internet
Amount: $120.00
Invoice date: April 22, 2026
Due date: May 22, 2026 (Net 30)
Payment status: Not paid yet
Category: Utilities / Internet

I'm attaching the invoice PDF. Please:
1. Verify the details against the photo
2. Ask me to confirm before posting
3. Create the journal entry
4. Save the PDF to the right folder
5. Update my AP (Accounts Payable) tracker
```

**What AI will do:**
1. Extract details from your photo
2. Show you a table: *"Is this correct?"*
3. After you say "yes": post `Dr. Utilities Expense / Cr. Accounts Payable $120`
4. Save PDF at `01_AP-AR_Management/Accounts_Payable/Vendor_Invoices/20260422_Invoice_Comcast_$120.00.pdf`
5. Add a row to your AP aging spreadsheet

**Time:** ~2 minutes.

---

### 💳 Case Study 2: I paid for lunch with a client (expense receipt)

**Scenario:** You had lunch with a potential client yesterday at Olive Garden, $68.50, paid with business credit card.

**What you do:**

1. **Take a photo** of the receipt
2. Open AI chat, copy-paste + attach photo:

```
💳 Expense to record.

Merchant: Olive Garden
Amount: $68.50
Date: April 22, 2026
Payment: Business credit card
Category: Meals & Entertainment (50% deductible per IRS)
Business purpose: Lunch with potential client ABC Corp to discuss Q3 contract

Please record this expense, save the receipt, and flag the 50% deduction rule.
```

**What AI will do:**
1. Record: `Dr. Meals & Entertainment $68.50 / Cr. Credit Card Payable $68.50`
2. Save receipt: `01_AP-AR_Management/Accounts_Payable/Receipts/20260422_Receipt_OliveGarden_$68.50.jpg`
3. Flag: *"Remember: Meals are only 50% deductible for tax purposes. I've noted this."*

**💡 Important tip:** Always include **business purpose** for meals/travel. IRS Publication 463 requires it for deductions. Generic "business meal" is NOT enough — name the person + topic.

---

### 📤 Case Study 3: I need to invoice my client

**Scenario:** You completed a consulting project for Client ABC Corp and want to send them an invoice for $5,000.

**What you do:**

Open AI chat, copy-paste:

```
📤 Create a customer invoice.

Customer: ABC Corp
Customer address: 123 Main St, Los Angeles, CA 90001
Service: Consulting services — Q2 2026 (April 1 – April 15, 2026)
Amount: $5,000.00
Payment terms: Net 30 (due May 22, 2026)

Please:
1. Generate the next invoice number (format INV-2026-XXXX)
2. Create a PDF invoice using standard template
3. Post journal entry: Dr. A/R / Cr. Service Revenue
4. Save the invoice and tell me where
5. Schedule a payment follow-up reminder for 5 days before due date
```

**What AI will do:**
1. Assign invoice number (example: INV-2026-0043)
2. Generate PDF
3. Post: `Dr. 1200 Accounts Receivable $5,000 / Cr. 4010 Service Revenue $5,000`
4. Save: `01_AP-AR_Management/Accounts_Receivable/Customer_Invoices/20260422_INV-2026-0043_ABC-Corp_$5,000.00.pdf`
5. Add reminder: "Follow up with ABC Corp on May 17, 2026"

**What you do next:** Open the saved PDF, email it to the client. Done.

---

### 📅 Case Study 4: End of month — close the books

**Scenario:** It's May 3, 2026. You want to close April's books and see your financial performance.

**What you do:**

1. Gather these items first:
   - Bank statement for April (PDF from your bank website)
   - Credit card statement for April
   - Any receipts you haven't submitted yet

2. Open AI chat, copy-paste:

```
📅 Start monthly close for April 2026.

Please guide me through the complete monthly close process:

Step 1: Ask me to upload the bank statement for reconciliation
Step 2: Identify any transactions I haven't recorded yet
Step 3: Post recurring accruals (utilities, payroll accrual, interest)
Step 4: Calculate depreciation (if I have fixed assets)
Step 5: Review Trial Balance and investigate any issues
Step 6: Generate these reports:
   - P&L (Income Statement) for April
   - Balance Sheet as of April 30, 2026
   - Cash Flow Statement (YTD)
   - Variance vs Budget
Step 7: Give me a 1-page executive summary

Let's go step-by-step. Ask me for each input as you need it.
```

**What AI will do:** Guide you through each step one at a time. Expect 30–45 minutes total. At the end, you'll have a complete "month-end package" saved in `06_Financial_Reporting/Monthly_Close/2026-04/` — this is what your CPA or board will want to see.

**💡 Tip:** Do this on the first 5 business days of each month so nothing gets forgotten.

---

### 👤 Case Study 5: I'm hiring my first employee

**Scenario:** You're about to hire Sarah Johnson as a full-time employee, salary $65,000/year.

**What you do:**

1. Ask Sarah to fill out these 3 forms (print from IRS/state websites):
   - Federal W-4 (tax withholding)
   - State withholding form (e.g., CA DE-4 for California)
   - I-9 (employment eligibility verification)

2. **Take photos** of all 3 completed forms

3. Open AI chat, attach photos + copy-paste:

```
👤 New employee setup.

Employee: Sarah Johnson
Position: Marketing Manager
Annual salary: $65,000
Pay frequency: Semi-monthly (15th and last day of month)
Hire date: May 1, 2026
Benefits: Health insurance (yes), 401(k) 3% contribution

I'm attaching:
- W-4 (federal withholding)
- State withholding form
- I-9

Please:
1. Extract all info from the forms
2. Verify I-9 is complete (Section 1 + 2 + legal work authorization)
3. Add Sarah to the employee roster
4. Calculate her first paycheck withholding preview
5. Remind me of state new-hire reporting (must file within 20 days)
6. Remind me to enroll her in Workers' Comp insurance BEFORE her start date

CRITICAL: If I-9 is not complete, do NOT proceed — flag it so I can fix it.
```

**What AI will do:**
1. OCR all 3 forms
2. Check I-9 completeness
3. Add Sarah to `05_Payroll/Employees_Roster.xlsx`
4. Save forms to `05_Payroll/Employee_Files/Sarah_Johnson/`
5. Calculate: `Gross $2,708/paycheck → Federal tax: $X, State tax: $Y, FICA: $Z, Net: $W`
6. Flag any missing items

---

## ❓ Part 4: FAQ / Troubleshooting

### "The Task Form doesn't show my company name — it says 'Loading…'"

Your browser blocked the config from loading automatically. Fix it:
1. Click the **⚙️** button at the top-right of the form
2. Click **"Upload config file"**
3. Navigate to `_INSTANCES/{your_folder}/_BUSINESS_CONFIG.json`
4. Select it → form updates immediately

### "AI says it can't find my files"

Make sure you uploaded the WHOLE folder (including `_CONFIG/`, `_CORE/`, `_MODULES/`, `_INSTANCES/{your_folder}/`) to the AI chat. Drag-and-drop the zip directly.

### "AI gave me an answer but it's wrong about tax rules"

Always verify tax advice with a licensed CPA. The AI + template is a workflow tool, not a legal/tax advisor. The template tax rates are accurate as of 2026 but laws change.

### "I made a mistake in a journal entry — how do I fix it?"

Tell AI: *"I need to reverse Journal Entry #JE-2026-0042. Post a reversing entry with the opposite debit/credit, dated today, with explanation 'Correcting JE-2026-0042 — [reason]'."*

Never manually edit posted journal entries — always use reversing entries for audit trail.

### "I don't know my entity type / EIN / etc."

Ask your CPA or attorney. Or check these documents:
- **Entity type:** Look at your formation documents (Articles of Incorporation, Certificate of Formation, Operating Agreement)
- **EIN:** IRS Form SS-4 confirmation letter, or your tax return header
- **State ID:** Your state Secretary of State filing confirmation

Leave these blank in the wizard if unsure — you can update later.

### "I want to add a second business"

Repeat Steps 3–6 from Part 1. Create a new folder `_INSTANCES/Second_Company/` with its own config. The Task Form has a ⚙️ switcher to flip between them.

### "How often should I update this workspace?"

- **Daily:** Record transactions as they happen (or photo them, process later same day)
- **Weekly:** Review AP aging, send customer reminders for unpaid invoices
- **Monthly:** Do the monthly close (Case Study 4)
- **Quarterly:** Estimated tax payments (Apr 15, Jun 15, Sep 15, Jan 15)
- **Annually:** Year-end close, tax prep with CPA, annual report filing

---

## 🆘 Part 5: Where to Get Help

- **Template technical questions:** Read `CONTRIBUTING.md` (for developers) or email: mikenguyen.dev@gmail.com
- **Tax / accounting advice:** Consult a licensed **CPA (Certified Public Accountant)** — the template does NOT replace a CPA
- **Legal questions:** Consult a business attorney
- **Daily AI workflow:** Check `USE_CASES_GUIDE.md` in your workspace for 20 more scenarios
- **Update your config:** Re-run `_CONFIG/setup_wizard.html`, download new JSON, replace the file in your instance folder, tell AI to re-render

---

## 🎯 Your First Week Checklist

After setup, spend your first week doing these:

- [ ] Day 1: Complete the setup (Parts 1–2 of this guide)
- [ ] Day 1: Open `ONBOARDING_CHECKLIST.md` and review the 30 items — tick off what you've already done
- [ ] Day 2: Enter any transactions from the last 30 days (Case Studies 1–3)
- [ ] Day 3: Set up bank account connections OR upload first bank statement
- [ ] Day 5: Review your first P&L report (ask AI: *"Show me a P&L for this month so far"*)
- [ ] Day 7: Schedule recurring calendar reminders:
  - 1st of month: Monthly close
  - 15th & last of month: Payroll (if applicable)
  - Apr 15 / Jun 15 / Sep 15 / Jan 15: Quarterly estimated tax

---

## 💡 Final Tips for Non-Technical Users

1. **Don't aim for perfect — aim for consistent.** Missing a day is OK. Not recording transactions for 2 weeks = bad (you'll forget details).

2. **Photos are your friend.** Take photos of EVERY receipt, invoice, check, statement — immediately. You can process them later. A photo with a date stamp is audit-proof.

3. **If unsure, ask AI first — then verify with CPA.** AI gives you a starting point + options. CPA confirms the final decision for complex issues.

4. **Backup your workspace monthly.** Right-click your `_INSTANCES/{your_folder}/` → Send to → Compressed folder → save a copy to Google Drive or external drive. Your financial data is irreplaceable.

5. **You don't need to memorize anything.** Every common task is in Part 3 above. Bookmark this file.

---

**🎉 Welcome to the workspace. You're not alone — the AI is here to help every step of the way.**

*AI Accounting Template v1.0.0 • For questions: mikenguyen.dev@gmail.com*
