# Bug Report - AI CV Analyze

**Phiên bản:** 1.0  
**Ngày tạo:** 30/01/2026  

---

## Bug Tracking Table

| Bug ID | Tiêu đề | Mô tả lỗi | Bước tái hiện | Mức độ | Trạng thái | Người giao | Người xử lý | Ghi chú |
|--------|--------|----------|---------------|--------|-----------|-----------|-----------|---------|
| BUG-001 | Register: Password không valid | Hệ thống cho phép tạo tài khoản với password chỉ chứa số | 1. Mở trang Register 2. Nhập password "123456" 3. Click Register | High | Open | QA01 | DEV01 | Cần validate password strength |
| BUG-002 | Login: Timeout lỗi không rõ ràng | Khi timeout, hiển thị lỗi generic "Error" thay vì "Session expired" | 1. Đăng nhập 2. Chờ > 30 phút 3. Thực hiện hành động | Medium | Open | QA02 | DEV02 | Cần cải thiện error message |
| BUG-003 | CV Upload: File size check không chính xác | Upload file 6MB nhưng hệ thống vẫn chấp nhận (limit 5MB) | 1. Prepare file 6MB 2. Upload tại CV Analysis 3. Observe | High | Open | QA01 | DEV03 | File validation cần kiểm tra lại |
| BUG-004 | CV Analysis: Progress bar bị stuck | Progress bar hiển thị 99% và không hoàn thành | 1. Upload PDF 2. Watch progress bar 3. Wait 5 minutes | Medium | Retest | QA03 | DEV04 | Đã fix, cần test lại |
| BUG-005 | Job Prediction: API timeout khi có nhiều công việc | Trang Job Prediction bị blank khi dữ liệu > 1000 records | 1. Truy cập Job Prediction 2. Observe loading | High | Fixed | QA02 | DEV01 | Đã optimize query, fixed |
| BUG-006 | Edit CV: Email update không reflect trên profile | Chỉnh sửa email nhưng profile vẫn hiển thị email cũ | 1. Edit CV email 2. Save 3. Check profile | Medium | Open | QA04 | DEV05 | Cần clear cache hoặc update logic |
| BUG-007 | Resume Download: File bị corrupt | File PDF tải xuống không mở được | 1. Click Download CV 2. Mở file 3. Error | High | Open | QA01 | DEV02 | Kiểm tra PDF generation service |
| BUG-008 | Mobile UI: Button overlap trên screen nhỏ | Nút Login và Register bị đè lên nhau trên mobile | 1. Open app trên mobile 2. View Auth page | Medium | Open | QA05 | DEV06 | Cần responsive design fix |
| BUG-009 | Database: Duplicate user creation | Có thể tạo 2 tài khoản với email giống nhau (race condition) | 1. Open 2 browser 2. Register cùng email đồng thời 3. Observe | High | Open | QA03 | DEV03 | Thêm unique constraint DB hoặc transaction |
| BUG-010 | Email notification: Email không gửi | Người dùng quên mật khẩu nhưng không nhận email | 1. Click Forgot Password 2. Submit 3. Check email | High | Closed | QA02 | DEV04 | Đã fix email service configuration |

---

## Bug Severity Legend

| Mức độ | Mô tả | Ưu tiên | Ví dụ |
|--------|-------|--------|--------|
| **Critical** | Không thể sử dụng hệ thống, dữ liệu bị mất | P0 - Fix ngay lập tức | Không thể đăng nhập, database bị corrupt |
| **High** | Chức năng chính không hoạt động đúng | P1 - Fix trong sprint này | Upload file fail, tính toán sai, bảo mật lỏng |
| **Medium** | Chức năng phụ hoặc UX không hoàn hảo | P2 - Fix trong vài sprint tới | Error message không rõ, delay 5s |
| **Low** | Typo, UI nhỏ, feature yêu cầu mới | P3 - Có thể đợi | Lỗi chính tả, icon không align |

---

## Bug Status Workflow

```
Open → In Progress → Fix Deployed → Retest → Verified Fixed → Closed
  ↓
   Duplicate / Invalid → Won't Fix → Closed
```

| Status | Meaning |
|--------|---------|
| **Open** | Vừa tạo, chưa ai xử lý |
| **In Progress** | Developer đang fix |
| **Fix Deployed** | Fix đã deploy lên dev/staging |
| **Retest** | QA đang verify fix |
| **Verified Fixed** | QA xác nhận bug đã fix |
| **Closed** | Bug fix hoàn thành, không mở lại được |
| **Duplicate** | Trùng với bug khác |
| **Invalid** | Không phải bug thực sự |
| **Won't Fix** | Quyết định không fix |

---

## Bug Report Template (Chi tiết)

### Ví dụ Bug Report chi tiết:

**BUG ID:** BUG-001  
**Tiêu đề:** Register: Password không validate strength  
**Mô tả:** Hệ thống cho phép tạo tài khoản với password yếu (chỉ số)  

**Bước tái hiện lỗi:**
1. Truy cập trang Register
2. Nhập Email: test@example.com
3. Nhập Password: 123456 (chỉ chứa số)
4. Confirm Password: 123456
5. Click "Register"

**Kết quả mong đợi:** Hiển thị lỗi "Password phải chứa chữ hoa, chữ thường, số, ký tự đặc biệt"

**Kết quả thực tế:** Tài khoản được tạo thành công

**Mức độ:** High  
**Tần suất:** 100% (luôn xảy ra)  

**Môi trường test:**
- OS: Windows 11
- Browser: Chrome 120
- Server: Staging

**Đính kèm:** Screenshot, video, log

**Người report:** QA01 (30/01/2026)  
**Người assigned:** DEV01  
**Ghi chú:** Cần kiểm tra hàm validatePassword

---

## Metrics Tracking

### Dashboard hàng tuần:

| Tuần | Total Bugs | Open | In Progress | Fixed | Retest | Closed | Pass Rate |
|------|-----------|------|------------|-------|--------|--------|-----------|
| 30/01 | 10 | 6 | 2 | 1 | 1 | 0 | 60% |
| 06/02 | 15 | 8 | 4 | 2 | 1 | 0 | 53% |
| 13/02 | 12 | 3 | 2 | 5 | 2 | 0 | 75% |

---

