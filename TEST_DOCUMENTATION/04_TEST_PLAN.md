# Test Plan - AI CV Analyze

**Phiên bản:** 1.0  
**Ngày:** 30/01/2026  
**Người soạn:** QA Lead  
**Phê duyệt:** Project Manager  

---

## 1. Mục tiêu Test

Xác minh rằng hệ thống AI CV Analyze hoạt động đúng theo yêu cầu:

- Quản lý tài khoản người dùng (đăng ký, đăng nhập, quên mật khẩu)
- Phân tích tệp CV bằng AI
- Gợi ý công việc phù hợp dựa trên kỹ năng
- Quản lý lịch sử CV
- Bảo mật (SQL Injection, Session timeout)
- Hiệu năng tối thiểu (Load time < 3s)

---

## 2. Phạm vi Test (Scope)

### Các tính năng được test:

**In Scope (sẽ test):**
- Module Authentication (Login, Register, Password Reset)
- Module CV Analysis (Upload, Processing, History)
- Module Job Recommendation
- Module Resume Management
- Security & Performance

**Out of Scope (không test):**
- Payment/Billing module (chưa phát triển)
- API mobile (chưa release)
- Admin panel
- Reporting features (giai đoạn sau)

---

## 3. Kiểu Test (Testing Types)

| Kiểu Test | Mô tả | Tỷ lệ |
|-----------|-------|--------|
| **Functional Test** | Kiểm thử các chức năng chính | 60% |
| **Integration Test** | Kiểm thử tích hợp giữa các module | 20% |
| **Performance Test** | Kiểm thử tốc độ, tải | 10% |
| **Security Test** | Kiểm thử bảo mật, SQL Injection | 10% |

---

## 4. Môi trường Test (Test Environment)

### Staging Server

- **URL:** https://staging-aicv.example.com
- **Database:** PostgreSQL (copy production)
- **Browser:** Chrome, Firefox, Edge
- **OS:** Windows 11, macOS, Ubuntu 22.04
- **Network:** Stable internet connection (tối thiểu 10Mbps)

### Test Data

- 5 test user accounts pre-created
- 20 sample PDF resumes
- 500 job records in database
- Sample job categories (Development, Design, HR, etc.)

---

## 5. Chiến lược Test (Test Strategy)

### Giai đoạn 1: Unit Testing (Dev team - 1-2 tuần)
- Mỗi developer test code của chính mình
- Sử dụng xUnit.NET hoặc NUnit
- Target: 80% code coverage

### Giai đoạn 2: Integration Testing (QA team - 1 tuần)
- Test các module làm việc cùng nhau
- Test API endpoints
- Test database interactions

### Giai đoạn 3: System Testing (QA team - 2 tuần)
- Test toàn bộ hệ thống end-to-end
- Test scenarios thực tế
- Bug tracking & verification

### Giai đoạn 4: UAT (Business user - 1 tuần)
- User thực tế test hệ thống
- Feedback và minor fixes
- Go/No-go decision

---

## 6. Tính năng và Test Cases

### Authentication Module (7 test cases)

| Feature | Test Case | Type |
|---------|-----------|------|
| Register | Valid data → Success | Functional |
| Register | Duplicate email → Error | Functional |
| Register | Weak password → Error | Functional |
| Login | Valid credentials → Success | Functional |
| Login | Invalid email → Error | Functional |
| Login | Wrong password → Error | Functional |
| Password Reset | Request reset → Email sent | Functional |

### CV Analysis Module (5 test cases)

| Feature | Test Case | Type |
|---------|-----------|------|
| Upload | Valid PDF → Success | Functional |
| Upload | Invalid format → Error | Functional |
| Upload | File too large → Error | Functional |
| Analysis | Process & display results | Functional |
| History | View previous analyses | Functional |

### Job Recommendation Module (3 test cases)

| Feature | Test Case | Type |
|---------|-----------|------|
| Display | Show matching jobs | Functional |
| Details | View job information | Functional |
| Filter | Filter by category | Functional |

### Resume Management Module (4 test cases)

| Feature | Test Case | Type |
|---------|-----------|------|
| List | View all resumes | Functional |
| Delete | Remove resume | Functional |
| Download | Export resume | Functional |
| Edit | Update resume info | Functional |

### Security (2 test cases)

| Feature | Test Case | Type |
|---------|-----------|------|
| Session | Auto logout after 30 min | Security |
| SQL Injection | Prevent SQL injection attack | Security |

### Performance (1 test case)

| Feature | Test Case | Type |
|---------|-----------|------|
| Load Time | Homepage loads < 3 seconds | Performance |

**Total: 25 test cases**

---

## 7. Tiêu chí Pass/Fail

### Pass Criteria (Tiêu chí qua):
- Test case thực hiện bước như kế hoạch
- Kết quả thực tế khớp kết quả mong đợi
- Không có unexpected errors

### Fail Criteria (Tiêu chí rớt):
- Bước không thực hiện được
- Kết quả thực tế khác kết quả mong đợi
- Unexpected exceptions hoặc crashes

### Blocked Criteria (Tiêu chí chặn):
- Tính năng chưa sẵn sàng
- Test data không available
- Test environment down

---

## 8. Người phụ trách (Resources)

### QA Team

| Vai trò | Người | Trách nhiệm |
|---------|-------|-----------|
| QA Lead | Alice | Quản lý test plan, report |
| Senior QA | Bob | Setup test env, review cases |
| QA01 | Charlie | Test Auth, Job modules |
| QA02 | Diana | Test CV Analysis module |
| QA03 | Eve | Test Resume, Security |
| QA04 | Frank | Performance, mobile testing |

### Dev Team Support

- Bug fixing feedback
- Test environment maintenance
- Data reset between test cycles

---

## 9. Timeline

### Lịch trình Chi tiết

```
Week 1 (27/01 - 02/02):
  - Test environment setup
  - Test case development
  - Smoke testing

Week 2 (03/02 - 09/02):
  - Functional testing (modules 1-4)
  - Bug logging & verification
  - Blocker resolution

Week 3 (10/02 - 16/02):
  - Regression testing
  - Performance optimization
  - Final bug verification

Week 4 (17/02 - 23/02):
  - UAT preparation
  - Documentation
  - Go/No-go review
```

### Milestone Dates

| Milestone | Target Date | Owner |
|-----------|-------------|-------|
| Test Plan Approved | 30/01 | QA Lead + PM |
| Test Environment Ready | 02/02 | QA Lead |
| 50% Test Cases Pass | 05/02 | QA Team |
| 90% Test Cases Complete | 09/02 | QA Team |
| All Critical Bugs Fixed | 12/02 | Dev Team |
| Final Test Report | 16/02 | QA Lead |
| Go/No-go Decision | 20/02 | PM + Business |

---

## 10. Tiêu chí Đóng Test (Exit Criteria)

### Phải thỏa mãn tất cả:

- [ ] 95% test cases passed (minimum 24/25)
- [ ] 0 critical bugs remaining
- [ ] 0 high-priority bugs remaining (or workaround approved)
- [ ] All P2 bugs documented for hotfix
- [ ] Performance benchmarks met (< 3s load time)
- [ ] Security testing passed
- [ ] Test report signed off by QA Lead
- [ ] Stakeholder approval received

---

## 11. Risk & Contingency

### Identified Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|-----------|
| Feature incomplete | High | High | Early communication, frequent sync with Dev |
| Test data unavailable | Medium | Medium | Pre-create test data, backup data sources |
| Environment instability | Low | High | Regular environment checks, 2nd env ready |
| Tester unavailable | Low | Medium | Cross-training, documentation, knowledge sharing |
| Performance issues | Medium | High | Early performance testing, optimization prep |

### Contingency Plans

1. **If feature not ready:** Skip and schedule for UAT/post-release
2. **If env down:** Use backup environment or dev environment
3. **If critical bug:** Hotfix or document workaround
4. **If performance fails:** Defer to optimization phase

---

## 12. Công cụ & Tài nguyên

### Test Automation Tools

- Test Framework: xUnit.NET / NUnit
- Test Data: SQL scripts, CSV files
- Test Tracking: Jira / Azure DevOps
- Bug Reporting: Email + shared spreadsheet

### Manual Testing Tools

- Browsers: Chrome DevTools, Firefox Inspector
- Network: Fiddler, Charles Proxy
- Performance: Lighthouse, WebPageTest
- Security: OWASP ZAP

### Documentation

- Test Cases: Google Sheets / Markdown
- Test Reports: Google Docs / PDF
- Bug Tracking: Google Sheets

---

## 13. Approval & Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| QA Lead | Alice | ________ | 30/01/2026 |
| Project Manager | Bob | ________ | 30/01/2026 |
| Tech Lead | Charlie | ________ | 30/01/2026 |
| Business Owner | Dave | ________ | 30/01/2026 |

---

