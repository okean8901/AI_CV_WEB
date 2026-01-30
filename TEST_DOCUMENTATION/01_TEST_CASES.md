# Test Cases - AI CV Analyze

**Phiên bản:** 1.0  
**Ngày tạo:** 30/01/2026  
**Người tạo:** QA Team  

---

## Module 1: Authentication (Quản lý tài khoản)

### TC-AUTH-001: Đăng ký tài khoản thành công

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-001 |
| Mô tả | Người dùng đăng ký tài khoản mới với thông tin hợp lệ |
| Tiền điều kiện | Chưa có tài khoản trong hệ thống |
| **Bước thực hiện** | |
| 1 | Truy cập trang Register |
| 2 | Nhập Email: test@example.com |
| 3 | Nhập Password: Test@1234 |
| 4 | Nhập Confirm Password: Test@1234 |
| 5 | Click button "Register" |
| **Kết quả mong đợi** | Tài khoản được tạo thành công, chuyển hướng tới trang Login |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-002: Đăng ký với email đã tồn tại

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-002 |
| Mô tả | Hệ thống từ chối đăng ký khi email đã được sử dụng |
| Tiền điều kiện | Email test@example.com đã tồn tại trong hệ thống |
| **Bước thực hiện** | |
| 1 | Truy cập trang Register |
| 2 | Nhập Email: test@example.com |
| 3 | Nhập Password: Test@1234 |
| 4 | Click button "Register" |
| **Kết quả mong đợi** | Hiển thị lỗi "Email đã được sử dụng" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-003: Đăng ký với password yếu

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-003 |
| Mô tả | Hệ thống từ chối password không đủ mạnh |
| Tiền điều kiện | Không có |
| **Bước thực hiện** | |
| 1 | Truy cập trang Register |
| 2 | Nhập Email: newuser@test.com |
| 3 | Nhập Password: 123456 |
| 4 | Click button "Register" |
| **Kết quả mong đợi** | Hiển thị lỗi yêu cầu password phải chứa chữ hoa, số, ký tự đặc biệt |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-004: Đăng nhập thành công

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-004 |
| Mô tả | Người dùng đăng nhập với tài khoản hợp lệ |
| Tiền điều kiện | Tài khoản test@example.com đã tồn tại |
| **Bước thực hiện** | |
| 1 | Truy cập trang Login |
| 2 | Nhập Email: test@example.com |
| 3 | Nhập Password: Test@1234 |
| 4 | Click button "Login" |
| **Kết quả mong đợi** | Đăng nhập thành công, chuyển hướng tới trang Home |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-005: Đăng nhập với email sai

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-005 |
| Mô tả | Hệ thống từ chối đăng nhập khi email không tồn tại |
| Tiền điều kiện | Email invalid@test.com không tồn tại |
| **Bước thực hiện** | |
| 1 | Truy cập trang Login |
| 2 | Nhập Email: invalid@test.com |
| 3 | Nhập Password: Test@1234 |
| 4 | Click button "Login" |
| **Kết quả mong đợi** | Hiển thị lỗi "Email hoặc mật khẩu không đúng" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-006: Đăng nhập với password sai

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-006 |
| Mô tả | Hệ thống từ chối đăng nhập khi mật khẩu sai |
| Tiền điều kiện | Tài khoản test@example.com đã tồn tại |
| **Bước thực hiện** | |
| 1 | Truy cập trang Login |
| 2 | Nhập Email: test@example.com |
| 3 | Nhập Password: WrongPassword@123 |
| 4 | Click button "Login" |
| **Kết quả mong đợi** | Hiển thị lỗi "Email hoặc mật khẩu không đúng" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-AUTH-007: Quên mật khẩu

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-AUTH-007 |
| Mô tả | Người dùng yêu cầu đặt lại mật khẩu |
| Tiền điều kiện | Email test@example.com đã tồn tại |
| **Bước thực hiện** | |
| 1 | Truy cập trang Login |
| 2 | Click link "Quên mật khẩu?" |
| 3 | Nhập Email: test@example.com |
| 4 | Click button "Gửi link đặt lại" |
| **Kết quả mong đợi** | Hiển thị thông báo "Email đặt lại mật khẩu đã được gửi" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | Kiểm tra email trong hộp thư |

---

## Module 2: CV Analysis (Phân tích CV)

### TC-CV-001: Upload file PDF thành công

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-CV-001 |
| Mô tả | Người dùng upload file CV (PDF) thành công |
| Tiền điều kiện | Đã đăng nhập, file PDF hợp lệ (< 5MB) |
| **Bước thực hiện** | |
| 1 | Truy cập trang "CV Analysis" |
| 2 | Click button "Upload Resume" |
| 3 | Chọn file resume.pdf |
| 4 | Click button "Analyze" |
| **Kết quả mong đợi** | File được upload, hệ thống bắt đầu phân tích, hiển thị progress |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-CV-002: Upload file không hỗ trợ

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-CV-002 |
| Mô tả | Hệ thống từ chối file không phải PDF |
| Tiền điều kiện | Không có |
| **Bước thực hiện** | |
| 1 | Truy cập trang "CV Analysis" |
| 2 | Click button "Upload Resume" |
| 3 | Chọn file document.txt |
| 4 | Click button "Analyze" |
| **Kết quả mong đợi** | Hiển thị lỗi "Chỉ hỗ trợ file PDF" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-CV-003: Upload file vượt quá dung lượng

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-CV-003 |
| Mô tả | Hệ thống từ chối file có dung lượng > 5MB |
| Tiền điều kiện | File có dung lượng 10MB |
| **Bước thực hiện** | |
| 1 | Truy cập trang "CV Analysis" |
| 2 | Click button "Upload Resume" |
| 3 | Chọn file large_resume.pdf (10MB) |
| 4 | Click button "Analyze" |
| **Kết quả mong đợi** | Hiển thị lỗi "File quá lớn, tối đa 5MB" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-CV-004: Phân tích CV hoàn thành

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-CV-004 |
| Mô tả | Hệ thống phân tích CV và hiển thị kết quả chi tiết |
| Tiền điều kiện | File CV đã được upload thành công |
| **Bước thực hiện** | |
| 1 | Chờ quá trình phân tích hoàn thành |
| 2 | Xem trang "Analysis Result" |
| **Kết quả mong đợi** | Hiển thị: kỹ năng, kinh nghiệm, điểm số, gợi ý cải thiện |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-CV-005: Xem lịch sử phân tích CV

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-CV-005 |
| Mô tả | Người dùng xem được lịch sử các lần phân tích CV |
| Tiền điều kiện | Đã phân tích ít nhất 2 file CV |
| **Bước thực hiện** | |
| 1 | Truy cập trang "CV Analysis" |
| 2 | Click tab "History" |
| **Kết quả mong đợi** | Hiển thị danh sách 2 lần phân tích trước đó với ngày giờ |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

## Module 3: Job Recommendation (Gợi ý công việc)

### TC-JOB-001: Xem danh sách gợi ý công việc

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-JOB-001 |
| Mô tả | Người dùng xem được danh sách công việc gợi ý dựa trên kỹ năng |
| Tiền điều kiện | Đã phân tích CV, hệ thống có dữ liệu công việc |
| **Bước thực hiện** | |
| 1 | Truy cập trang "Job Prediction" |
| 2 | Xem danh sách công việc |
| **Kết quả mong đợi** | Hiển thị danh sách công việc phù hợp với kỹ năng của người dùng |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | Công việc nên được sắp xếp theo mức độ phù hợp |

---

### TC-JOB-002: Xem chi tiết công việc gợi ý

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-JOB-002 |
| Mô tả | Người dùng xem chi tiết một công việc gợi ý |
| Tiền điều kiện | Đã xem danh sách công việc |
| **Bước thực hiện** | |
| 1 | Click vào một công việc trong danh sách |
| 2 | Xem chi tiết công việc |
| **Kết quả mong đợi** | Hiển thị: tên việc, công ty, kỹ năng yêu cầu, mức lương, mô tả chi tiết |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-JOB-003: Lọc công việc theo danh mục

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-JOB-003 |
| Mô tả | Người dùng lọc công việc theo danh mục |
| Tiền điều kiện | Đã xem danh sách công việc |
| **Bước thực hiện** | |
| 1 | Click filter "Danh mục" |
| 2 | Chọn "Software Development" |
| 3 | Xem kết quả lọc |
| **Kết quả mong đợi** | Danh sách chỉ hiển thị công việc trong danh mục "Software Development" |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

## Module 4: Resume Management (Quản lý CV)

### TC-RESUME-001: Xem danh sách CV đã lưu

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-RESUME-001 |
| Mô tả | Người dùng xem danh sách tất cả CV đã upload |
| Tiền điều kiện | Đã upload ít nhất 2 file CV |
| **Bước thực hiện** | |
| 1 | Truy cập trang "My Resumes" |
| 2 | Xem danh sách |
| **Kết quả mong đợi** | Hiển thị danh sách 2+ CV với tên file, ngày upload |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-RESUME-002: Xóa CV

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-RESUME-002 |
| Mô tả | Người dùng xóa một file CV |
| Tiền điều kiện | Đã có CV trong danh sách |
| **Bước thực hiện** | |
| 1 | Truy cập trang "My Resumes" |
| 2 | Click nút "Delete" trên một CV |
| 3 | Xác nhận xóa |
| **Kết quả mong đợi** | CV bị xóa khỏi danh sách |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-RESUME-003: Tải xuống CV

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-RESUME-003 |
| Mô tả | Người dùng tải xuống file CV |
| Tiền điều kiện | Đã có CV trong danh sách |
| **Bước thực hiện** | |
| 1 | Truy cập trang "My Resumes" |
| 2 | Click nút "Download" trên một CV |
| **Kết quả mong đợi** | File CV được tải xuống máy tính |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-RESUME-004: Chỉnh sửa thông tin CV

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-RESUME-004 |
| Mô tả | Người dùng chỉnh sửa thông tin CV (tên, email, điện thoại) |
| Tiền điều kiện | Đã có CV trong danh sách |
| **Bước thực hiện** | |
| 1 | Click vào CV để xem chi tiết |
| 2 | Click nút "Edit" |
| 3 | Sửa tên thành "John Doe" |
| 4 | Sửa email thành "john@example.com" |
| 5 | Click button "Save" |
| **Kết quả mong đợi** | Thông tin CV được cập nhật thành công |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

## Module 5: Security & Performance

### TC-SEC-001: Session timeout

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-SEC-001 |
| Mô tả | Hệ thống tự động đăng xuất sau 30 phút không hoạt động |
| Tiền điều kiện | Đã đăng nhập vào hệ thống |
| **Bước thực hiện** | |
| 1 | Đăng nhập vào hệ thống |
| 2 | Không hoạt động trong 30 phút |
| 3 | Cố gắng thực hiện hành động |
| **Kết quả mong đợi** | Hệ thống tự động đăng xuất, chuyển hướng tới trang Login |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-SEC-002: SQL Injection Protection

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-SEC-002 |
| Mô tả | Hệ thống bảo vệ chống SQL Injection |
| Tiền điều kiện | Không có |
| **Bước thực hiện** | |
| 1 | Truy cập trang Login |
| 2 | Nhập Email: ' OR '1'='1 |
| 3 | Nhập Password: test |
| 4 | Click button "Login" |
| **Kết quả mong đợi** | Không có lỗi SQL Injection, hiển thị lỗi login thông thường |
| Kết quả thực tế | ☐ Pass / ☐ Fail |
| Ghi chú | |

---

### TC-PERF-001: Load time trang chính

| Trường | Giá trị |
|--------|--------|
| Test Case ID | TC-PERF-001 |
| Mô tả | Trang chính tải trong thời gian < 3 giây |
| Tiền điều kiện | Kết nối internet ổn định |
| **Bước thực hiện** | |
| 1 | Mở browser, xóa cache |
| 2 | Truy cập trang Home |
| 3 | Đo thời gian tải |
| **Kết quả mong đợi** | Trang tải trong < 3 giây |
| Kết quả thực tế | ☐ Pass / ☐ Fail (Thời gian: ___s) |
| Ghi chú | |

---

