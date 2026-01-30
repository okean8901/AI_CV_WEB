# Tài liệu Hướng dẫn Sử dụng & Mô tả Chức năng - AI CV Analyze

**Phiên bản:** 1.0  
**Ngày cập nhật:** 30/01/2026  
**Dành cho:** Testers, End Users  

---

## Mục lục

1. [Giới thiệu Chung](#giới-thiệu-chung)
2. [Yêu cầu Hệ thống](#yêu-cầu-hệ-thống)
3. [Module 1: Quản lý Tài khoản](#module-1-quản-lý-tài-khoản)
4. [Module 2: Phân tích CV](#module-2-phân-tích-cv)
5. [Module 3: Gợi ý Công việc](#module-3-gợi-ý-công-việc)
6. [Module 4: Quản lý CV](#module-4-quản-lý-cv)
7. [Tính năng Bảo mật](#tính-năng-bảo-mật)
8. [Troubleshooting](#troubleshooting)

---

## Giới thiệu Chung

### AI CV Analyze là gì?

AI CV Analyze là một nền tảng web giúp người dùng:
- Phân tích CV/Resume bằng công nghệ AI
- Nhận được gợi ý cải thiện CV
- Tìm kiếm công việc phù hợp với kỹ năng của mình

### Kiến trúc Hệ thống

```
Frontend (ASP.NET MVC)
    ↓
Backend API (C# Controllers)
    ↓
Services Layer (Business Logic)
    ↓
Database (PostgreSQL)
    ↓
Azure AI Services (CV Analysis)
```

---

## Yêu cầu Hệ thống

### Để sử dụng hệ thống:

| Yêu cầu | Tối thiểu | Khuyên dùng |
|--------|----------|-----------|
| **Browser** | Chrome 100+ | Chrome 120+, Edge 120+ |
| **Internet** | 5 Mbps | 10 Mbps+ |
| **RAM** | 2 GB | 4+ GB |
| **Disk Space** | 100 MB | 500 MB |
| **OS** | Windows 8 + | Windows 11, macOS, Linux |

### Trình duyệt hỗ trợ:

- Google Chrome 100+
- Mozilla Firefox 115+
- Microsoft Edge 120+
- Safari 16+

---

## Module 1: Quản lý Tài khoản

### 1.1 Trang Chủ (Home)

**URL:** `https://aicv.example.com/`

**Chức năng:**
- Hiển thị tổng quan về hệ thống
- Navigation menu chính
- Tin tức & hướng dẫn

**Các phần chính:**

```
┌─────────────────────────────┐
│    AI CV Analyze            │
│    Home | Features | Help   │
├─────────────────────────────┤
│                             │
│  Welcome! Start analyzing   │
│  your CV with AI            │
│                             │
│  [Upload CV]  [Sign Up]     │
│                             │
└─────────────────────────────┘
```

---

### 1.2 Đăng Ký (Register)

**URL:** `https://aicv.example.com/auth/register`

**Bước thực hiện:**

1. Click "Sign Up" hoặc truy cập trang Register
2. Nhập thông tin:
   - Email: địa chỉ email hợp lệ
   - Password: tối thiểu 8 ký tự (chứa chữ hoa, chữ thường, số, ký tự đặc biệt)
   - Confirm Password: nhập lại password

3. Click button "Register"

**Yêu cầu Password:**
```
✓ Tối thiểu 8 ký tự
✓ Chứa ít nhất 1 chữ hoa (A-Z)
✓ Chứa ít nhất 1 chữ thường (a-z)
✓ Chứa ít nhất 1 số (0-9)
✓ Chứa ít nhất 1 ký tự đặc biệt (!@#$%^&*)
```

**Ví dụ password hợp lệ:** `MyPassword@123`  
**Ví dụ password không hợp lệ:** `password123` (không chữ hoa, ký tự đặc biệt)

**Thông báo lỗi có thể gặp:**

| Lỗi | Nguyên nhân | Cách khắc phục |
|-----|-----------|----------------|
| "Email không hợp lệ" | Format email sai | Nhập đúng định dạng: user@domain.com |
| "Email đã được sử dụng" | Email đã đăng ký | Sử dụng email khác hoặc đăng nhập |
| "Password không đủ mạnh" | Password yếu | Thêm chữ hoa, số, ký tự đặc biệt |
| "Password không khớp" | Xác nhận password sai | Kiểm tra lại password và xác nhận |

---

### 1.3 Đăng Nhập (Login)

**URL:** `https://aicv.example.com/auth/login`

**Bước thực hiện:**

1. Nhập Email đã đăng ký
2. Nhập Password
3. (Tùy chọn) Chọn "Remember me" để lưu tên đăng nhập
4. Click button "Login"

**Sau khi đăng nhập thành công:**
- Chuyển hướng tới trang Home đã xác thực
- Hiển thị Menu người dùng
- Có thể truy cập các tính năng

**Thông báo lỗi:**

| Lỗi | Nguyên nhân |
|-----|-----------|
| "Email hoặc mật khẩu không đúng" | Email/Password sai |
| "Tài khoản không tồn tại" | Email chưa đăng ký |
| "Tài khoản bị khóa" | Đăng nhập sai quá nhiều lần |

---

### 1.4 Quên Mật khẩu (Forgot Password)

**URL:** `https://aicv.example.com/auth/forgot-password`

**Bước thực hiện:**

1. Click link "Quên mật khẩu?" trên trang Login
2. Nhập Email tài khoản
3. Click button "Gửi link đặt lại"
4. Kiểm tra email (inbox hoặc spam folder)
5. Click link trong email
6. Nhập password mới
7. Click button "Đặt lại mật khẩu"

**Lưu ý:**
- Link email hết hạn sau 1 giờ
- Nếu không nhận email, kiểm tra folder Spam
- Password mới phải tuân theo quy tắc password policy

---

### 1.5 Tài khoản Người dùng (User Profile)

**URL:** `https://aicv.example.com/account/profile`

**Chức năng:**
- Xem thông tin cá nhân
- Chỉnh sửa email, tên
- Thay đổi mật khẩu
- Xem lịch sử hoạt động
- Xóa tài khoản

---

## Module 2: Phân tích CV

### 2.1 Trang Phân tích CV (CV Analysis Index)

**URL:** `https://aicv.example.com/analysis/index`

**Chức năng chính:**

1. Upload CV mới
2. Xem lịch sử phân tích
3. Chọn CV để phân tích lại

**Giao diện:**

```
┌────────────────────────────────────┐
│ CV Analysis - Upload & Analyze     │
├────────────────────────────────────┤
│                                    │
│ Drop file here or:                 │
│ [Browse File]                      │
│                                    │
│ Hỗ trợ: PDF files, max 5MB         │
│                                    │
│ ────────────────────────────────── │
│                                    │
│ LỊCH SỬ PHÂN TÍCH:                │
│ ┌──────────────────────────────┐  │
│ │ resume_v1.pdf - 28/01/2026  │  │
│ │ resume_v2.pdf - 29/01/2026  │  │
│ └──────────────────────────────┘  │
└────────────────────────────────────┘
```

---

### 2.2 Upload CV

**Các bước:**

1. **Chọn file:**
   - Click "Browse File" hoặc kéo file vào vùng designated area
   - Chọn file PDF từ máy tính

2. **Kiểm tra yêu cầu:**
   - Format: PDF chỉ
   - Dung lượng: Tối đa 5 MB
   - Nội dung: Phải là CV/Resume

3. **Upload:**
   - Click button "Upload" hoặc "Analyze Now"
   - Chờ file được tải lên (progress bar sẽ hiển thị)

4. **Xác nhận:**
   - Hiển thị thông báo "Upload thành công"
   - Chuyển hướng tới trang phân tích

**Thông báo lỗi:**

| Lỗi | Nguyên nhân | Cách khắc phục |
|-----|-----------|----------------|
| "File quá lớn, tối đa 5MB" | File > 5MB | Nén file hoặc lựa chọn file khác |
| "Chỉ hỗ trợ file PDF" | File không phải PDF | Chuyển file sang PDF |
| "File bị lỗi, không đọc được" | PDF corrupted | Thử file khác |
| "Timeout, vui lòng thử lại" | Network chậm | Kiểm tra internet, thử lại |

---

### 2.3 Kết quả Phân tích CV

**URL:** `https://aicv.example.com/analysis/result/{id}`

**Hiển thị các thông tin:**

#### A. Thông tin Cơ bản (Basic Info)

```
Tên: [Tên từ CV]
Email: [Email từ CV]
Điện thoại: [Số điện thoại]
Địa chỉ: [Địa chỉ từ CV]
```

#### B. Điểm Số (Score)

```
Overall Score: 75/100

Breakdown:
├─ Professional Experience: 85/100
├─ Skills & Competencies: 70/100
├─ Education & Certifications: 75/100
├─ Resume Format: 65/100
└─ Keyword Optimization: 70/100
```

#### C. Kỹ năng Được Tìm thấy (Skills Extracted)

```
Top Skills:
1. Python (80% match with job market)
2. Data Analysis (75%)
3. Machine Learning (70%)
4. SQL (68%)
5. Project Management (65%)
```

#### D. Kinh Nghiệm (Experience)

```
Total Years: 5+ years

Work History:
- Software Developer (ABC Company) - 3 years
- Junior Developer (XYZ Corp) - 2 years
```

#### E. Gợi ý Cải thiện (Recommendations)

```
✓ Thêm kỹ năng leadership
✓ Rõ ràng hóa achievements (sử dụng metrics)
✓ Bổ sung sertifications
✓ Optimize keywords cho ATS
✓ Cải thiện format: thêm dấu bullet points
```

#### F. So sánh với Market (Market Comparison)

```
Kỹ năng của bạn vs Market Demand:
├─ Python: 80% (Cao)
├─ Java: 40% (Thấp - Đang thiếu)
├─ Cloud (AWS): 50% (Trung bình)
└─ DevOps: 30% (Nên học thêm)
```

---

### 2.4 Xem Lịch sử Phân tích

**URL:** `https://aicv.example.com/analysis/history`

**Chức năng:**
- Danh sách tất cả CV đã phân tích
- Sắp xếp theo ngày (mới nhất trước)
- Nhấp để xem kết quả cũ
- Xóa hoặc tải xuống kết quả

**Bảng thông tin:**

| Tệp | Ngày Phân tích | Điểm | Công việc Gợi ý | Hành động |
|-----|----------------|------|----------------|----------|
| resume_v1.pdf | 28/01/2026 | 72 | 15 jobs | View / Edit / Delete |
| resume_v2.pdf | 29/01/2026 | 75 | 18 jobs | View / Edit / Delete |

---

## Module 3: Gợi ý Công việc

### 3.1 Trang Gợi ý Công việc (Job Prediction)

**URL:** `https://aicv.example.com/jobs/prediction`

**Chức năng:**
- Hiển thị danh sách công việc phù hợp
- Sắp xếp theo mức độ phù hợp
- Lọc theo tiêu chí

**Danh sách công việc:**

```
┌─────────────────────────────────────────────┐
│ CÔNG VIỆC PHÙ HỢP NHẤT                     │
├─────────────────────────────────────────────┤
│                                             │
│ Senior Python Developer                  ★  │
│ ABC Tech Company | Hà Nội                   │
│ Salary: 25-35 million VND                   │
│ Match: 95%                                  │
│ Skills: Python, Django, PostgreSQL          │
│ [View Details]                              │
│                                             │
│ ─────────────────────────────────────────── │
│                                             │
│ Data Analyst                              ★ │
│ XYZ Corp | HCM                              │
│ Salary: 18-25 million VND                   │
│ Match: 87%                                  │
│ Skills: Python, SQL, Data Analysis          │
│ [View Details]                              │
│                                             │
└─────────────────────────────────────────────┘
```

---

### 3.2 Chi tiết Công việc (Job Details)

**Bước xem chi tiết:**

1. Click vào một công việc từ danh sách
2. Trang chi tiết hiển thị:

**Thông tin công việc:**

```
Position: Senior Python Developer
Company: ABC Tech Company
Location: Hà Nội, Vietnam
Salary: 25-35 million VND / month
Posted: 25/01/2026
Application Deadline: 28/02/2026

JOB DESCRIPTION:
Chúng tôi tìm kiếm một Senior Python Developer...
[Full description...]

REQUIREMENTS:
- 5+ years of Python experience
- Experience with Django/FastAPI
- PostgreSQL proficiency
- AWS or Azure experience
- Strong problem-solving skills

NICE TO HAVE:
- Leadership experience
- Open source contributions
- Microservices architecture

COMPANY INFO:
Website: www.abc-tech.com
Company Size: 200-500 employees
Industry: Technology / Software

HOW TO APPLY:
1. Click "Apply Now"
2. Submit your resume
3. Wait for company response

MATCH ANALYSIS:
Your Profile vs Job Requirements:
✓ Python: 95% match
✓ Django: 80% match
✓ PostgreSQL: 85% match
✗ AWS: 40% match (Missing)
✗ Leadership: 50% match (Could improve)

RECOMMENDATION:
Bạn rất phù hợp với vị trí này. Bổ sung AWS
knowledge sẽ tăng khả năng ứng tuyển.
```

---

### 3.3 Lọc Công việc (Filter Jobs)

**Các tiêu chí lọc:**

| Tiêu chí | Tùy chọn |
|----------|---------|
| **Danh mục** | Development, Design, HR, Marketing, etc. |
| **Mức lương** | < 15M, 15-25M, 25-40M, > 40M |
| **Địa điểm** | Hà Nội, HCM, Đà Nẵng, Remote |
| **Loại công việc** | Full-time, Part-time, Contract |
| **Kinh nghiệm** | Intern, Junior, Senior, Lead |
| **Mức độ phù hợp** | > 90%, > 80%, > 70% |

**Ví dụ sử dụng filter:**

1. Click "Advanced Filter"
2. Chọn: Danh mục = Development, Lương > 25M
3. Click "Apply Filter"
4. Xem danh sách công việc đã lọc

---

## Module 4: Quản lý CV

### 4.1 Danh sách CV (My Resumes)

**URL:** `https://aicv.example.com/resumes/`

**Giao diện:**

```
┌─────────────────────────────────────────┐
│ MY RESUMES - Quản lý CV của tôi        │
├─────────────────────────────────────────┤
│ [Upload New Resume]                     │
├─────────────────────────────────────────┤
│                                         │
│ Resume                          Ngày   │ Kích thước │ Hành động │
│ ─────────────────────────────────────── │
│ resume_2024.pdf                29/01   │ 245 KB     │ ▼ Menu    │
│ resume_2025.pdf                30/01   │ 234 KB     │ ▼ Menu    │
│                                         │
└─────────────────────────────────────────┘
```

---

### 4.2 Tải xuống CV (Download)

**Bước thực hiện:**

1. Trên bảng danh sách CV
2. Click menu (3 chấm) trên CV muốn tải
3. Chọn "Download"
4. File sẽ được tải xuống máy tính

**Vị trí tải xuống:** `C:\Users\[Username]\Downloads\`

---

### 4.3 Xóa CV (Delete)

**Cảnh báo:** Không thể hoàn tác

**Bước thực hiện:**

1. Click menu (3 chấm) trên CV muốn xóa
2. Chọn "Delete"
3. Xác nhận "Yes, delete this resume"
4. CV sẽ bị xóa khỏi danh sách

---

### 4.4 Chỉnh sửa Thông tin CV (Edit Resume)

**URL:** `https://aicv.example.com/resumes/{id}/edit`

**Các trường có thể chỉnh sửa:**

```
Thông tin Cá nhân:
├─ Tên đầy đủ
├─ Email
├─ Điện thoại
├─ Địa chỉ
└─ Website portfolio

Mục Tiêu Nghề nghiệp (Optional)

Kinh Nghiệm Làm việc:
├─ Công ty
├─ Vị trí
├─ Từ - Đến
└─ Mô tả công việc

Giáo Dục:
├─ Trường
├─ Bằng cấp
├─ Chuyên ngành
└─ Năm tốt nghiệp

Kỹ Năng:
├─ Tên kỹ năng
└─ Mức độ (Basic, Intermediate, Advanced)

Chứng chỉ:
├─ Tên chứng chỉ
├─ Tổ chức cấp
└─ Ngày cấp
```

**Bước chỉnh sửa:**

1. Click menu CV → "Edit"
2. Chỉnh sửa các trường cần thiết
3. Click "Save Changes"
4. Xác nhận thay đổi

---

## Tính năng Bảo mật

### 4.1 Session Timeout

**Thời gian:** 30 phút không hoạt động

**Behavior:**
- Tự động đăng xuất
- Chuyển hướng tới trang Login
- Session sẽ được xóa

**Cách tránh:**
- Thực hiện hành động thường xuyên
- Không đóng browser lâu
- Lưu công việc trước khi timeout

---

### 4.2 Bảo vệ Chống SQL Injection

**Cấp độ:** Toàn hệ thống

**Biện pháp:**
- Parameterized Queries sử dụng cho tất cả database access
- Input validation trên server
- Output encoding khi hiển thị dữ liệu

**Cho người dùng:**
- Không cần lo lắng, hệ thống đã được bảo vệ
- Có thể nhập dữ liệu bình thường

---

### 4.3 Mã hóa Dữ liệu (Encryption)

**Dữ liệu được mã hóa:**
- Tất cả kết nối HTTPS (TLS 1.3)
- Password lưu trữ: Bcrypt hashing
- Sensitive data: AES-256 encryption

---

## Troubleshooting

### Lỗi Chung Gặp Phải

#### 1. "Cannot connect to server"

**Nguyên nhân:** 
- Server down
- Network không kết nối
- DNS issue

**Cách khắc phục:**
1. Kiểm tra kết nối internet
2. Refresh browser (Ctrl + R)
3. Xóa cache browser
4. Thử URL khác hoặc incognito mode
5. Chờ 5 phút rồi thử lại
6. Liên hệ support nếu vẫn không được

#### 2. "File upload failed"

**Nguyên nhân:**
- Network interrupted
- File too large
- File format wrong

**Cách khắc phục:**
1. Kiểm tra file size (max 5MB)
2. Đảm bảo format PDF
3. Thử lại với file khác
4. Kiểm tra internet connection
5. Thử browser khác

#### 3. "Analysis taking too long"

**Nguyên nhân:**
- Server busy
- Large CV file
- Network slow

**Cách khắc phục:**
1. Chờ thêm 5-10 phút
2. Nếu còn stuck, refresh page
3. Kiểm tra internet speed
4. Thử lại sau

#### 4. "Cannot download resume"

**Nguyên nhân:**
- Browser blocked download
- Disk space full
- Permission issue

**Cách khắc phục:**
1. Kiểm tra browser download settings
2. Kiểm tra dung lượng ổ đĩa
3. Thử browser khác
4. Kiểm tra folder download permissions

---

### Performance Tips

**Để hệ thống chạy nhanh hơn:**

1. Dùng Chrome hoặc Firefox
2. Xóa cache định kỳ (Ctrl + Shift + Delete)
3. Kiểm tra internet speed (đạt 10Mbps+)
4. Đóng tab/app không cần thiết
5. Chạy trên máy mạnh hơn nếu có thể

---

### Contact Support

**Liên hệ hỗ trợ:**

- Email: support@aicv.example.com
- Phone: +84 (0) 1234-5678
- Chat: Website chat (góc dưới phải)
- Response time: < 24 hours

---

## Phụ lục: Câu hỏi Thường gặp (FAQ)

### Q: Dữ liệu CV của tôi có an toàn không?

**A:** Có. Tất cả dữ liệu:
- Mã hóa trong quá trình truyền (HTTPS)
- Mã hóa trong lưu trữ
- Chỉ bạn có thể xem
- Không chia sẻ với bên thứ ba
- Tuân theo GDPR

### Q: Tôi có thể xóa tài khoản không?

**A:** Có. Vào Account Settings → Delete Account. Tất cả dữ liệu sẽ bị xóa vĩnh viễn.

### Q: Phân tích mất bao lâu?

**A:** Thường 30 giây - 2 phút tùy kích thước CV.

### Q: Có thể upload nhiều CV cùng lúc không?

**A:** Không. Phải upload từng cái một.

### Q: Có bao nhiêu công việc được gợi ý?

**A:** 50+ công việc mỗi lần, phụ thuộc kỹ năng và filter.

### Q: Giá cả?

**A:** Hiện tại miễn phí. Có thể sẽ có premium plan sau.

---

**Tài liệu này được cập nhật thường xuyên. Lần cuối: 30/01/2026**

