# 🚀 Hướng dẫn Bắt đầu — Dành cho Người mới (Không cần biết IT)

> **Hướng dẫn này dành cho chủ doanh nghiệp, KHÔNG phải lập trình viên.** Không code. Không command line. Không thuật ngữ kỹ thuật. Nếu bạn biết dùng email và trình duyệt web, bạn dùng được hệ thống này.

**Ngôn ngữ:** 🇬🇧 [English](QUICKSTART.md) • 🇻🇳 Tiếng Việt (file này) • 🇪🇸 [Español](QUICKSTART.es.md)

---

## 📋 Bạn cần chuẩn bị gì trước khi bắt đầu

Chỉ 3 thứ — không cần cài đặt gì:

1. **Một trình duyệt web** — Chrome, Edge, Safari, hoặc Firefox (chắc chắn máy bạn đã có)
2. **Tài khoản AI chat** — một trong các tài khoản miễn phí sau là được:
   - Claude: https://claude.ai (khuyến nghị — phù hợp nhất với workspace này)
   - ChatGPT: https://chat.openai.com
   - Gemini: https://gemini.google.com
3. **Thông tin công ty của bạn** — chuẩn bị sẵn:
   - Tên pháp lý của doanh nghiệp
   - Loại entity (LLC, S-Corp, C-Corp... — CPA của bạn biết rõ)
   - Tiểu bang bạn đang hoạt động (VD: California, Texas)
   - Họ tên + email + số điện thoại của bạn
   - Năm tài chính (thường là tháng 1 – tháng 12)

**Thời gian setup:** 10–15 phút. Chỉ làm 1 lần.

---

## 🎯 Phần 1: Setup lần đầu (10 phút)

### Bước 1: Tải template về máy

1. Vào trang GitHub (hoặc hỏi người đưa bạn link để lấy file zip)
2. Click nút màu xanh **"Code"** → **"Download ZIP"**
3. Tìm file zip vừa tải trong thư mục Downloads
4. **Click chuột phải** vào file zip → **"Extract All"** → chọn vị trí bạn nhớ được (VD: `Desktop/Ke_Toan_Cua_Toi/`)

Bây giờ bạn sẽ thấy một folder có các file như `Accounting_Task_Form.html`, `_CONFIG/`, `_CORE/`, v.v.

### Bước 2: Mở wizard setup

1. Mở folder `_CONFIG`
2. **Double-click** file `setup_wizard.html`
3. File sẽ mở trong trình duyệt, hiển thị wizard màu xanh-trắng

Nếu không tự mở: click chuột phải → **"Open with"** → chọn Chrome hoặc Edge.

### Bước 3: Điền wizard 6 bước

Wizard hướng dẫn bạn qua 6 màn hình. Đa số field là tùy chọn — chỉ field có dấu `*` đỏ là bắt buộc.

| Bước | Nhập gì |
|:----:|---------|
| 1️⃣ Business Identity | Tên pháp lý, DBA (nếu có), EIN (nếu đã có), entity type, industry |
| 2️⃣ Location & Tax Setup | Tiểu bang hoạt động (VD: CA cho California), fiscal year |
| 3️⃣ Operations | Phần mềm kế toán đang dùng (QuickBooks / Excel / Google Sheets), cơ sở accrual/cash, ngưỡng phê duyệt |
| 4️⃣ Owner Info | Họ tên, email, vai trò (Owner), ngôn ngữ ưa thích |
| 5️⃣ Compliance Snapshot | Tick những mục đã hoàn thành (EIN, BOI filing, state registration...) |
| 6️⃣ Review | Kiểm tra, rồi click **Download JSON** và **Download Checklist** |

💡 **Không biết trả lời?** Cứ để trống. Sau này cập nhật được. Các câu hỏi thuế (entity type, EIN) nên hỏi CPA.

### Bước 4: Lưu workspace của bạn

Sau khi download 2 file từ wizard:

1. Quay về folder template
2. Mở folder `_INSTANCES`
3. Tạo folder mới bên trong, đặt tên theo công ty (không dấu cách — dùng underscore): VD `Quan_Ca_Phe_Cua_Toi`
4. Di chuyển 2 file đã download (`_BUSINESS_CONFIG.json` và `ONBOARDING_CHECKLIST.md`) vào folder đó

Cấu trúc folder phải giống thế này:
```
Ke_Toan_Cua_Toi/
├── _INSTANCES/
│   └── Quan_Ca_Phe_Cua_Toi/          ← Workspace của bạn ở đây
│       ├── _BUSINESS_CONFIG.json     ← Di chuyển từ Downloads
│       └── ONBOARDING_CHECKLIST.md   ← Di chuyển từ Downloads
├── Accounting_Task_Form.html
└── ... (các file template khác)
```

### Bước 5: Bảo AI build workspace

1. Mở https://claude.ai (hoặc AI bạn chọn)
2. Tạo chat mới
3. **Upload các file template** (kéo-thả cả folder, hoặc zip trước rồi upload)
4. Copy-paste prompt này:

```
Tôi đang setup workspace mới từ AI Accounting Template.
Config của tôi ở _INSTANCES/{ten_folder_cua_ban}/_BUSINESS_CONFIG.json

Hãy đọc _CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md và thực hiện protocol 7 bước
để render workspace cho tôi. Khi xong, báo cho tôi:
1. Tóm tắt những gì đã tạo
2. 3 mục khẩn cấp nhất trong onboarding checklist
3. Tôi nên làm gì tiếp theo
```

Thay `{ten_folder_cua_ban}` bằng tên folder thật.

AI sẽ đọc template, hiểu business của bạn, và tạo 5–6 tài liệu cá nhân hóa trong folder. Mất 3–5 phút.

### Bước 6: Kiểm tra setup

1. Quay về folder trong File Explorer
2. Folder workspace của bạn bây giờ phải có nhiều file hơn: `README.md`, `COMPANY_PROFILE.md`, `AI_AGENT_MEMORY.md`...
3. Mở `README.md` — phải hiển thị tên công ty bạn ở đầu file
4. Mở `Accounting_Task_Form.html` (file chính, không phải file trong `_CONFIG`)
5. Header phải hiện tên công ty bạn

✅ **Xong phần setup!** Từ giờ, bạn chỉ dùng Task Form + AI chat cho công việc kế toán hàng ngày.

---

## 💬 Phần 2: Cách "Nói chuyện" với AI (Mẹo quan trọng)

### Quy tắc vàng

**Cụ thể. Cho số liệu. Cho ngày tháng. Cho tên.**

❌ Kém: *"Ghi nhận một khoản chi phí"*
✅ Tốt: *"Ghi nhận chi phí $45.80 cho bữa trưa tại Starbucks với khách hàng ABC Corp ngày 22/4/2026. Thanh toán bằng thẻ tín dụng công ty."*

### Cách bắt đầu mỗi phiên làm việc với AI

Đầu mỗi cuộc chat mới với AI (không phải mỗi tin nhắn — chỉ tin nhắn đầu của ngày):

**Copy-paste prompt này:**

```
Tôi đang mở workspace AI Accounting cho {tên công ty của bạn}.

Hãy đọc các file sau theo thứ tự:
1. _INSTANCES/{ten_folder_cua_ban}/_BUSINESS_CONFIG.json
2. _INSTANCES/{ten_folder_cua_ban}/AI_AGENT_MEMORY.md
3. _INSTANCES/{ten_folder_cua_ban}/COMPANY_PROFILE.md

Sau đó confirm bạn đã load context (báo cho tôi entity type, state, fiscal year,
và deadline thuế kế tiếp), rồi hỏi tôi muốn làm task gì hôm nay.
```

AI sẽ đọc, tóm tắt lại cho bạn, và hỏi cần giúp gì. Xong, sẵn sàng làm việc.

### Dùng Task Form (cách dễ nhất)

Thay vì tự gõ prompt, cho form build giúp:

1. Mở `Accounting_Task_Form.html` trong trình duyệt
2. Click 1 nút task bất kỳ (VD: "📥 Ghi nhận Hóa đơn đến", "💳 Chi phí lẻ", "📅 Đóng sổ cuối tháng")
3. Điền form đơn giản (hoặc chỉ upload ảnh với các task photo)
4. Click **"Gửi cho AI"** — form tự động copy prompt hoàn chỉnh vào clipboard
5. Paste vào AI chat (Windows: `Ctrl+V`, Mac: `Cmd+V`)
6. AI sẽ confirm hiểu đúng chưa, rồi xử lý task

---

## 📚 Phần 3: 5 Case Studies hàng ngày

Tình huống thật với prompt chính xác để copy-paste. Đây là 5 task phổ biến nhất cho doanh nghiệp nhỏ.

---

### 📥 Case Study 1: Nhận hóa đơn từ nhà cung cấp

**Tình huống:** Nhà mạng Comcast gửi bạn hóa đơn $120. Bạn muốn ghi nhận để tuần sau thanh toán.

**Việc bạn làm:**

1. **Chụp ảnh** hóa đơn (dùng điện thoại) hoặc lưu file PDF
2. Mở AI chat
3. Copy-paste prompt này + đính kèm ảnh:

```
📥 Hóa đơn mới từ vendor cần ghi nhận.

Vendor: Comcast Business Internet
Amount: $120.00
Invoice date: 22/04/2026
Due date: 22/05/2026 (Net 30)
Payment status: Chưa thanh toán
Category: Utilities / Internet

Tôi đính kèm file PDF hóa đơn. Hãy:
1. Verify thông tin với ảnh
2. Hỏi tôi confirm trước khi post
3. Tạo journal entry
4. Lưu PDF vào folder đúng
5. Update AP (Accounts Payable) tracker
```

**AI sẽ:**
1. Extract thông tin từ ảnh
2. Hiện bảng: *"Thông tin đúng không?"*
3. Sau khi bạn OK: post `Dr. Utilities Expense / Cr. Accounts Payable $120`
4. Lưu PDF tại `01_AP-AR_Management/Accounts_Payable/Vendor_Invoices/20260422_Invoice_Comcast_$120.00.pdf`
5. Thêm 1 dòng vào AP aging spreadsheet

**Thời gian:** ~2 phút.

---

### 💳 Case Study 2: Bạn ăn trưa với khách (receipt chi phí)

**Tình huống:** Bạn ăn trưa với khách hàng tiềm năng hôm qua tại Olive Garden, $68.50, thanh toán bằng thẻ tín dụng công ty.

**Việc bạn làm:**

1. **Chụp ảnh** receipt
2. Mở AI chat, copy-paste + đính ảnh:

```
💳 Chi phí cần ghi nhận.

Merchant: Olive Garden
Amount: $68.50
Date: 22/04/2026
Payment: Thẻ tín dụng công ty
Category: Meals & Entertainment (50% deductible per IRS)
Business purpose: Ăn trưa với khách hàng tiềm năng ABC Corp để thảo luận hợp đồng Q3

Ghi nhận chi phí này, lưu receipt, và flag rule 50% deduction.
```

**AI sẽ:**
1. Ghi: `Dr. Meals & Entertainment $68.50 / Cr. Credit Card Payable $68.50`
2. Lưu receipt: `01_AP-AR_Management/Accounts_Payable/Receipts/20260422_Receipt_OliveGarden_$68.50.jpg`
3. Flag: *"Nhắc nhở: Meals chỉ được deduct 50% cho tax. Đã note lại."*

**💡 Mẹo quan trọng:** Luôn ghi **business purpose** cho meals/travel. IRS Publication 463 bắt buộc để được deduct. Nói chung chung "business meal" KHÔNG đủ — phải nêu tên người + chủ đề.

---

### 📤 Case Study 3: Xuất hóa đơn cho khách

**Tình huống:** Bạn hoàn thành dự án tư vấn cho ABC Corp và muốn gửi hóa đơn $5,000.

**Việc bạn làm:**

Mở AI chat, copy-paste:

```
📤 Tạo customer invoice.

Customer: ABC Corp
Customer address: 123 Main St, Los Angeles, CA 90001
Service: Dịch vụ tư vấn — Q2 2026 (01/04 – 15/04/2026)
Amount: $5,000.00
Payment terms: Net 30 (due 22/05/2026)

Hãy:
1. Generate số invoice kế tiếp (format INV-2026-XXXX)
2. Tạo PDF invoice theo template chuẩn
3. Post journal entry: Dr. A/R / Cr. Service Revenue
4. Lưu invoice và báo cho tôi biết lưu ở đâu
5. Schedule reminder follow-up thanh toán 5 ngày trước due date
```

**AI sẽ:**
1. Gán số invoice (VD: INV-2026-0043)
2. Generate PDF
3. Post: `Dr. 1200 Accounts Receivable $5,000 / Cr. 4010 Service Revenue $5,000`
4. Lưu: `01_AP-AR_Management/Accounts_Receivable/Customer_Invoices/20260422_INV-2026-0043_ABC-Corp_$5,000.00.pdf`
5. Thêm reminder: "Follow-up với ABC Corp ngày 17/05/2026"

**Việc bạn làm tiếp:** Mở PDF đã lưu, email cho khách. Xong.

---

### 📅 Case Study 4: Cuối tháng — đóng sổ

**Tình huống:** Hôm nay 03/05/2026. Bạn muốn đóng sổ tháng 4 và xem performance tài chính.

**Việc bạn làm:**

1. Chuẩn bị sẵn những thứ này:
   - Sao kê ngân hàng tháng 4 (PDF từ website bank)
   - Sao kê thẻ tín dụng tháng 4
   - Các receipt chưa submit

2. Mở AI chat, copy-paste:

```
📅 Bắt đầu monthly close cho tháng 4/2026.

Hãy guide tôi qua toàn bộ quy trình đóng sổ:

Step 1: Yêu cầu tôi upload sao kê bank để reconciliation
Step 2: Tìm các transactions tôi chưa ghi nhận
Step 3: Post recurring accruals (utilities, payroll accrual, interest)
Step 4: Tính depreciation (nếu có fixed assets)
Step 5: Review Trial Balance và điều tra issues
Step 6: Generate các báo cáo:
   - P&L (Income Statement) cho tháng 4
   - Balance Sheet tại 30/04/2026
   - Cash Flow Statement (YTD)
   - Variance vs Budget
Step 7: Tóm tắt executive 1 trang

Làm từng bước, hỏi input khi cần.
```

**AI sẽ:** Hướng dẫn từng bước một. Mất 30–45 phút tổng cộng. Cuối cùng, bạn có "month-end package" đầy đủ lưu tại `06_Financial_Reporting/Monthly_Close/2026-04/` — đây là thứ CPA hoặc board sẽ muốn xem.

**💡 Mẹo:** Làm việc này trong 5 ngày làm việc đầu tháng để không quên gì.

---

### 👤 Case Study 5: Tuyển employee đầu tiên

**Tình huống:** Bạn sắp tuyển Sarah Johnson làm full-time employee, lương $65,000/năm.

**Việc bạn làm:**

1. Yêu cầu Sarah điền 3 form này (in từ IRS/state website):
   - W-4 Federal (tax withholding)
   - State withholding form (VD: CA DE-4 cho California)
   - I-9 (xác minh việc làm hợp pháp)

2. **Chụp ảnh** cả 3 form đã điền

3. Mở AI chat, đính ảnh + copy-paste:

```
👤 Setup employee mới.

Employee: Sarah Johnson
Position: Marketing Manager
Annual salary: $65,000
Pay frequency: Semi-monthly (ngày 15 và ngày cuối tháng)
Hire date: 01/05/2026
Benefits: Health insurance (yes), 401(k) 3% contribution

Tôi đính kèm:
- W-4 (federal withholding)
- State withholding form
- I-9

Hãy:
1. Extract thông tin từ forms
2. Verify I-9 hoàn chỉnh (Section 1 + 2 + legal work authorization)
3. Thêm Sarah vào employee roster
4. Tính paycheck đầu tiên preview withholding
5. Nhắc về state new-hire reporting (phải nộp trong 20 ngày)
6. Nhắc tôi enroll Sarah vào Workers' Comp insurance TRƯỚC ngày vào làm

CRITICAL: Nếu I-9 chưa hoàn chỉnh, KHÔNG proceed — flag để tôi sửa.
```

**AI sẽ:**
1. OCR cả 3 forms
2. Check I-9 đầy đủ
3. Thêm Sarah vào `05_Payroll/Employees_Roster.xlsx`
4. Lưu forms tại `05_Payroll/Employee_Files/Sarah_Johnson/`
5. Tính: `Gross $2,708/paycheck → Federal tax: $X, State tax: $Y, FICA: $Z, Net: $W`
6. Flag các items thiếu

---

## ❓ Phần 4: FAQ / Xử lý sự cố

### "Task Form không hiện tên công ty tôi — chỉ hiện 'Loading…'"

Trình duyệt chặn auto-load config. Khắc phục:
1. Click nút **⚙️** góc trên-phải form
2. Click **"Upload config file"**
3. Tìm đến `_INSTANCES/{folder_cua_ban}/_BUSINESS_CONFIG.json`
4. Chọn file → form update ngay

### "AI báo không tìm thấy file của tôi"

Chắc chắn bạn upload CẢ folder (bao gồm `_CONFIG/`, `_CORE/`, `_MODULES/`, `_INSTANCES/{folder_cua_ban}/`) lên AI chat. Kéo-thả zip trực tiếp.

### "AI trả lời nhưng sai về tax rules"

Luôn verify lời khuyên thuế với CPA. AI + template là công cụ workflow, KHÔNG phải tư vấn pháp lý/thuế. Tax rates trong template chính xác tới 2026 nhưng luật có thể thay đổi.

### "Tôi ghi sai journal entry — sửa thế nào?"

Nói với AI: *"Tôi cần reverse Journal Entry #JE-2026-0042. Post reversing entry với debit/credit ngược lại, ngày hôm nay, memo 'Correcting JE-2026-0042 — [lý do]'."*

Không bao giờ tự sửa tay journal entries đã post — luôn dùng reversing entries để giữ audit trail.

### "Tôi không biết entity type / EIN của mình"

Hỏi CPA hoặc luật sư. Hoặc check các tài liệu này:
- **Entity type:** Xem giấy tờ thành lập (Articles of Incorporation, Certificate of Formation, Operating Agreement)
- **EIN:** Thư confirm IRS Form SS-4, hoặc header của tax return
- **State ID:** Xác nhận filing tại Secretary of State

Không chắc thì để trống trong wizard — update sau cũng được.

### "Muốn thêm công ty thứ 2"

Lặp lại Bước 3–6 Phần 1. Tạo folder mới `_INSTANCES/Cong_Ty_Thu_Hai/` với config riêng. Task Form có nút ⚙️ switcher để chuyển qua lại.

### "Bao lâu cần update workspace 1 lần?"

- **Hàng ngày:** Ghi nhận giao dịch khi phát sinh (hoặc chụp ảnh, xử lý cùng ngày)
- **Hàng tuần:** Review AP aging, nhắc khách trả invoices chưa thanh toán
- **Hàng tháng:** Đóng sổ cuối tháng (Case Study 4)
- **Hàng quý:** Nộp estimated tax (15/4, 15/6, 15/9, 15/1)
- **Hàng năm:** Đóng sổ năm, chuẩn bị tax với CPA, nộp annual report

---

## 🆘 Phần 5: Cần giúp đỡ ở đâu

- **Câu hỏi kỹ thuật về template:** Đọc `CONTRIBUTING.md` (cho developer) hoặc email: mikenguyen.dev@gmail.com
- **Tư vấn thuế / kế toán:** Hỏi **CPA (Certified Public Accountant) có license** — template KHÔNG thay thế CPA
- **Câu hỏi pháp lý:** Hỏi business attorney
- **Daily workflow với AI:** Xem `USE_CASES_GUIDE.md` trong workspace có thêm 20 tình huống
- **Update config:** Chạy lại `_CONFIG/setup_wizard.html`, download JSON mới, thay thế file trong instance folder, bảo AI render lại

---

## 🎯 Checklist Tuần đầu

Sau setup, tuần đầu làm những việc này:

- [ ] Ngày 1: Hoàn thành setup (Phần 1–2 hướng dẫn này)
- [ ] Ngày 1: Mở `ONBOARDING_CHECKLIST.md` review 30 items — tick những gì đã xong
- [ ] Ngày 2: Nhập giao dịch 30 ngày gần nhất (Case Studies 1–3)
- [ ] Ngày 3: Kết nối bank account HOẶC upload sao kê bank đầu tiên
- [ ] Ngày 5: Review báo cáo P&L đầu tiên (hỏi AI: *"Cho tôi xem P&L tháng này tới giờ"*)
- [ ] Ngày 7: Setup calendar nhắc nhở:
  - Ngày 1 mỗi tháng: Đóng sổ
  - Ngày 15 & cuối tháng: Payroll (nếu có)
  - 15/4, 15/6, 15/9, 15/1: Nộp quarterly estimated tax

---

## 💡 Mẹo cuối cho người không rành IT

1. **Không cần hoàn hảo — cần đều đặn.** Bỏ 1 ngày OK. Bỏ 2 tuần = tệ (quên chi tiết).

2. **Ảnh chụp là bạn thân.** Chụp ảnh MỌI receipt, hóa đơn, check, sao kê — ngay lập tức. Xử lý sau cũng được. Ảnh có timestamp là audit-proof.

3. **Không chắc thì hỏi AI trước — rồi verify với CPA.** AI cho bạn starting point + options. CPA confirm quyết định cuối cho issues phức tạp.

4. **Backup workspace hàng tháng.** Click phải vào `_INSTANCES/{folder_cua_ban}/` → Send to → Compressed folder → lưu copy vào Google Drive hoặc external drive. Data tài chính không thể replace được.

5. **Không cần nhớ gì cả.** Mọi task phổ biến đều ở Phần 3 trên. Bookmark file này lại.

---

**🎉 Chào mừng đến workspace. Bạn không cô đơn — AI luôn ở đây giúp từng bước.**

*AI Accounting Template v1.0.0 • Câu hỏi: mikenguyen.dev@gmail.com*
