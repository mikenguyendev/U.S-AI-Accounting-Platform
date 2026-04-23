# 🏢 AI Accounting Controller — White-Label Template

> **Template AI Agent plug-and-play cho workflow kế toán US Small Business.**
> Điền wizard → Nhận workspace cá nhân hóa trong 5 phút → AI Agent đóng vai Corporate Controller cho công ty bạn.

**Phiên bản:** 1.0.0 (ổn định) • **Developer:** mikenguyen.dev@gmail.com • **License:** Xem [LICENSE](LICENSE)

**Ngôn ngữ:** 🇬🇧 [English](README.md) • 🇻🇳 Tiếng Việt (file này) • 🇪🇸 [Español](README.es.md)

**👉 Người mới bắt đầu? Đọc [QUICKSTART.vi.md](QUICKSTART.vi.md) trước — hướng dẫn chi tiết cho người không rành IT.**

---

## 🎯 Đây là gì?

Template tái sử dụng cho phép bạn deploy 1 AI Agent đóng vai **Corporate Accounting Controller** xử lý:

- ✅ **AP/AR Management** — Hóa đơn nhà cung cấp, hóa đơn khách hàng, báo cáo tuổi nợ
- ✅ **General Ledger** — Journal entries, adjusting entries, trial balance
- ✅ **Bank Reconciliation** — Worksheet đối soát hàng tháng
- ✅ **Tax Compliance** — Liên bang (1120/1120-S/1065/Schedule C) + State + Payroll
- ✅ **Payroll** — W-2/1099, khấu trừ thuế Federal + State
- ✅ **Financial Reporting** — P&L, Balance Sheet, Cash Flow theo US GAAP
- ✅ **Budget & Variance** — Phân tích theo phòng ban với đề xuất reforecast

**Chuẩn US GAAP + IRS**, thiết kế cho **chủ doanh nghiệp Mỹ nói tiếng Việt** (bilingual VN/EN), nhưng cũng phù hợp cho người dùng English-only (set `owner.preferred_language: "en"` trong config).

**Độ bao phủ:**
- 6 entity types × 10 detailed states × 5 industries = **300 cấu hình đầy đủ modeled**
- 41 states khác được support qua Lenient render mode (generic fallback)
- 10 Excel templates cho daily operations (JE, TB, Bank Recon, AR/AP Aging, P&L, BS, CF, Payroll, Budget)
- 18 loại task kế toán qua browser form với AI response protocols

---

## 🚀 Quickstart — 3 con đường

### 🅰️ Con đường A: Onboarding business mới (customer-facing)

**Khi nào dùng:** Bạn đang onboard khách hàng mới (hoặc business của chính bạn) vào template.

**Thời gian:** ~5 phút wizard + ~5 phút AI render.

1. **Điền wizard:**
   Mở [_CONFIG/setup_wizard.html](_CONFIG/setup_wizard.html) trong trình duyệt (khuyến nghị Chrome/Edge).
   Hoàn thành 6 bước: Business Identity → Location → Operations → Owner → Compliance → Review.
   Click **Download JSON** và **Download Checklist**.

2. **Lưu downloads** vào folder mới: `_INSTANCES/{your_instance_id}/`

3. **Prompt AI Agent:**
   > *"Đọc `_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md` và render workspace từ `_INSTANCES/{your_instance_id}/_BUSINESS_CONFIG.json`."*

4. **AI thực hiện 7 bước:** validate config → tạo folder tree → render 5 MDs → copy COA → báo cáo critical items.

5. **Xong.** Workspace của bạn đã live. Mở `Accounting_Task_Form.html` và bắt đầu task đầu tiên.

**📖 Không rành IT? Đọc [QUICKSTART.vi.md](QUICKSTART.vi.md) có hướng dẫn chi tiết từng bước với ảnh minh họa + case studies hàng ngày.**

### 🅱️ Con đường B: Fractional CFO / multi-client

**Khi nào dùng:** Bạn quản lý nhiều businesses (1 template, N instances).

1. Mỗi client, chạy Con đường A — mỗi client có folder `_INSTANCES/{client_id}/` riêng.
2. HTML form có nút **⚙️ switcher** ở header — click để upload config khác không cần reload.
3. URL-param shortcut: `Accounting_Task_Form.html?config=_INSTANCES/Client_A/_BUSINESS_CONFIG.json`
4. Recent configs lưu trong localStorage (last 5 hiện dưới dạng quick-switch buttons).

### 🅲 Con đường C: Customer delivery (zip + email)

**Khi nào dùng:** Bạn muốn đóng gói workspace của khách thành zip self-contained để gửi họ.

1. Sau Con đường A, hỏi AI: *"Tạo customer delivery package (Option A minimal) cho `{customer_id}`."*
2. AI tạo `_DELIVERIES/{customer_id}_v1.0_YYYY-MM-DD/` chứa tất cả những gì khách cần (instance + HTML forms + relevant modules).
3. Zip folder đó (Windows: click phải → Send to → Compressed folder) hoặc PowerShell: `Compress-Archive`.
4. Email zip cho khách. Họ unzip, mở `START_HERE.md`, chạy AI riêng của họ.

---

## ⚙️ Cấu hình được support

### Entity types (6)

| Type | Tax form | Rule owner comp | Pass-through? |
|------|----------|------------------|:--------------:|
| C-Corp | Form 1120 | Salary HOẶC dividends | ❌ (double taxation) |
| S-Corp | Form 1120-S | **Reasonable comp TRƯỚC distributions** (IRS audit trigger #1) | ✅ qua K-1 |
| LLC-single | Schedule C | Owner draw + SE tax | ✅ |
| LLC-multi | Form 1065 | Guaranteed payments + K-1 | ✅ |
| Partnership | Form 1065 | Guaranteed payments + K-1 | ✅ |
| Sole-Prop | Schedule C | Owner draw + SE tax | ✅ |

Chi tiết rules trong [_MODULES/entity/](_MODULES/entity/).

### States (10 detailed + 41 via fallback)

**Full modules** (tax-obligations, deadlines, payroll rates, withholding, entity-specific tax):

CA, NY, TX, FL, DE, WA, IL, GA, NJ, MA

Xem [_state_matrix.csv](_MODULES/state/_state_matrix.csv) cho bảng quick lookup.

**40 states còn lại:** Render vẫn hoạt động nhưng state-specific rules cần lookup thủ công (AI flag điều này). Phase 2.5 sẽ fill gaps — xem [CONTRIBUTING.md](CONTRIBUTING.md#add-a-new-state-module).

### Industries (5)

| Industry | Số COA | Key accounts |
|----------|:------:|--------------|
| Service | 60 | Consulting/agency, không inventory |
| Retail | 75 | Inventory + Sales Tax Payable + Gift Cards |
| Restaurant | 70 | Food/Bev/Beer/Wine/Spirits split + Tips Payable |
| Manufacturing | 80 | 3-tier inventory (Raw/WIP/Finished) + overhead |
| SaaS | 65 | Deferred Revenue + Capitalized Commissions (ASC 606) |

---

## 🤖 AI Agent compatibility

Đã test + khuyến nghị:

- **Claude (Anthropic)** — Primary tested platform, Opus 4.7 / Sonnet 4.6
- **ChatGPT (OpenAI)** — GPT-4o class, compatible với minor prompt tweaks
- **Gemini (Google)** — 1.5 Pro / 2.0 tested

**Context window:** ≥200K tokens khuyến nghị. Core docs + relevant modules tổng ~80–120 KB (~25–35K tokens) tùy entity × state.

**Prompt đầu tiên** cho AI session mới (copy-paste):
> *"Đọc các file theo thứ tự: `_BUSINESS_CONFIG.json`, `AI_AGENT_MEMORY.md`, `COMPANY_PROFILE.md`, `FORM_SCHEMA.md`. Confirm đã load context (entity, state, FY, next deadline), rồi hỏi tôi muốn làm task gì."*

---

## 📚 Tài liệu

| File | Mục đích |
|------|----------|
| [README.md](README.md) | Tổng quan (English) |
| **[QUICKSTART.vi.md](QUICKSTART.vi.md)** | **Hướng dẫn chi tiết cho người mới (tiếng Việt)** ⭐ |
| [CHANGELOG.md](CHANGELOG.md) | Lịch sử phiên bản + feature list v1.0.0 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Cách mở rộng template (cho developers) |
| [_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md](_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md) | AI agent 7-step workflow |
| [_CORE/RENDER_PROTOCOL.md](_CORE/RENDER_PROTOCOL.md) | 7-pass template resolution algorithm |

---

## ⚠️ Disclaimers

- **Không phải tư vấn pháp lý/thuế.** Template cung cấp automation workflow kế toán. **Luôn tham vấn CPA có license** cho quyết định thuế phức tạp, audit, hoặc các vấn đề jurisdiction-specific.
- **Độ chính xác compliance.** Tax rates và rules current theo 2026. Luật thay đổi — verify với CPA trước khi filing. Xem [CONTRIBUTING.md](CONTRIBUTING.md#update-existing-modules-annual-tax-refresh) cho quy trình annual refresh.
- **Rủi ro AI hallucination.** AI Agents có thể sai. Luôn double-check critical numbers, đặc biệt trước month-end close hoặc tax filing. Dùng **Confirm** phase của 5-phase AI protocol — không bao giờ skip.
- **Bảo mật dữ liệu.** Workspace chứa PII (SSN, EIN, bank accounts). Bạn chịu trách nhiệm bảo vệ data khi share với AI Agents. Cân nhắc on-prem hoặc enterprise AI plans với data privacy guarantees cho khách hàng nhạy cảm.

---

## 👤 Developer

**mikenguyen.dev@gmail.com**

- Bug reports + feature requests: email
- Commercial licensing (multi-tenant SaaS deployment, white-label resale): email
- Đề xuất đóng góp (state module mới, industry mới, v.v.): xem [CONTRIBUTING.md](CONTRIBUTING.md)

---

*Được build với ❤️ cho chủ doanh nghiệp Mỹ nói tiếng Việt — và mọi người khác.*
