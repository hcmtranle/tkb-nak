# TKB - Trường TH Nguyễn An Khương 2026-2027

## Kiến trúc hệ thống

```
Google Sheets (dữ liệu gốc)
        ↕ Apps Script (API)
GitHub repo tkb-nak
        ↓ auto-deploy
Netlify (web app public)
```

## File trong repo

| File | Mục đích |
|------|---------|
| `RULES.md` | Bộ quy tắc TKB — nguồn sự thật duy nhất |
| `setup.gs` | Apps Script khởi tạo Google Sheet (chạy 1 lần) |
| `api.gs` | Apps Script API — deploy as Web App |
| `index.html` | Web app (Admin + User tabs) |
| `README.md` | Tài liệu này |

## Google Sheet

**ID:** `1XsuzsI_EpVh_raaa2cyQ7uq66GYETvb3gclBKEZTzRc`
**Link:** https://docs.google.com/spreadsheets/d/1XsuzsI_EpVh_raaa2cyQ7uq66GYETvb3gclBKEZTzRc

**Sheets trong file:**
- `CONFIG` — cấu hình hệ thống, mật khẩu admin
- `GIAOVIEN` — 57 GV với số tiết phân công
- `TKB_MASTER` — toàn bộ TKB (dòng = 1 tiết học)
- `Lớp 1.1` → `Lớp 5.5` — 29 sheet hiển thị theo lớp

## Hướng dẫn vận hành

### Bước 1 — Khởi tạo Sheet (chạy 1 lần)
1. Mở Google Sheet → Extensions → Apps Script
2. Dán nội dung `setup.gs` → Chạy `setupAll()`

### Bước 2 — Deploy API
1. Dán nội dung `api.gs` → Deploy as Web App
2. Execute as: Me | Who has access: Anyone
3. Copy URL → dán vào CONFIG sheet, ô `apps_script_url`

### Bước 3 — Deploy Web App
1. Push code lên GitHub repo `tkb-nak`
2. Kết nối Netlify → auto deploy từ main branch
3. Copy Netlify URL → dán vào CONFIG sheet

## API Endpoints

```
?action=tkb_class&lop=1.1      → TKB lớp 1.1
?action=tkb_teacher&gv=Trang   → TKB cô Trang
?action=tkb_grade&khoi=3       → TKB toàn khối 3
?action=tkb_subject&mon=Toán   → Tất cả tiết Toán
?action=tkb_all                → Toàn bộ TKB
?action=conflicts              → Danh sách xung đột
?action=teachers               → Danh sách GV
?action=verify_admin&pw=***    → Xác thực admin
```

## Mật khẩu Admin
Xem trong CONFIG sheet, ô `admin_password`.
