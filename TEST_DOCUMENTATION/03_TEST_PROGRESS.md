# Test Progress Tracker - AI CV Analyze

**Phiên bản:** 1.0  
**Ngày cập nhật:** 30/01/2026  
**URL Spreadsheet:** Google Sheets (chia sẻ với team)

---

## Summary Dashboard

```
Total Test Cases: 25
Passed: 18
Failed: 5
Blocked: 2
Pass Rate: 72%

Total Bugs Found: 10
Critical: 1
High: 5
Medium: 3
Low: 1
```

---

## Test Progress by Module

### Module 1: Authentication (Quản lý tài khoản)

| Test Case | Status | Assigned To | Start Date | End Date | Notes |
|-----------|--------|------------|-----------|----------|-------|
| TC-AUTH-001 | Pass | QA01 | 28/01 | 29/01 | ✓ Đăng ký thành công |
| TC-AUTH-002 | Pass | QA01 | 28/01 | 29/01 | ✓ Email validation working |
| TC-AUTH-003 | Fail | QA02 | 29/01 | 30/01 | Password validation missing (BUG-001) |
| TC-AUTH-004 | Pass | QA01 | 28/01 | 28/01 | ✓ Login working |
| TC-AUTH-005 | Pass | QA02 | 29/01 | 29/01 | ✓ Invalid email handled |
| TC-AUTH-006 | Pass | QA02 | 29/01 | 29/01 | ✓ Wrong password handled |
| TC-AUTH-007 | Pass | QA03 | 30/01 | 30/01 | ✓ Forgot password email sent |

**Module Status:** 86% (6/7 pass)

---

### Module 2: CV Analysis (Phân tích CV)

| Test Case | Status | Assigned To | Start Date | End Date | Notes |
|-----------|--------|------------|-----------|----------|-------|
| TC-CV-001 | Pass | QA04 | 28/01 | 28/01 | ✓ PDF upload successful |
| TC-CV-002 | Pass | QA04 | 28/01 | 28/01 | ✓ Rejects non-PDF |
| TC-CV-003 | Fail | QA04 | 29/01 | 30/01 | 6MB file accepted (BUG-003) |
| TC-CV-004 | Pass | QA05 | 29/01 | 30/01 | ✓ Analysis completed |
| TC-CV-005 | Blocked | QA05 | 30/01 | - | Waiting for history feature |

**Module Status:** 60% (3/5 pass)

---

### Module 3: Job Recommendation (Gợi ý công việc)

| Test Case | Status | Assigned To | Start Date | End Date | Notes |
|-----------|--------|------------|-----------|----------|-------|
| TC-JOB-001 | Pass | QA01 | 30/01 | 30/01 | ✓ Job list displayed |
| TC-JOB-002 | Pass | QA01 | 30/01 | 30/01 | ✓ Job details shown |
| TC-JOB-003 | Blocked | QA02 | 30/01 | - | Filter feature not implemented |

**Module Status:** 67% (2/3 pass)

---

### Module 4: Resume Management (Quản lý CV)

| Test Case | Status | Assigned To | Start Date | End Date | Notes |
|-----------|--------|------------|-----------|----------|-------|
| TC-RESUME-001 | Pass | QA03 | 29/01 | 30/01 | ✓ Resume list displayed |
| TC-RESUME-002 | Pass | QA03 | 30/01 | 30/01 | ✓ Delete working |
| TC-RESUME-003 | Fail | QA03 | 30/01 | 30/01 | Downloaded file corrupted (BUG-007) |
| TC-RESUME-004 | Blocked | QA04 | 30/01 | - | Edit feature not ready |

**Module Status:** 50% (2/4 pass)

---

### Module 5: Security & Performance

| Test Case | Status | Assigned To | Start Date | End Date | Notes |
|-----------|--------|------------|-----------|----------|-------|
| TC-SEC-001 | Blocked | QA02 | 30/01 | - | Need 30 min wait time |
| TC-SEC-002 | Pass | QA02 | 30/01 | 30/01 | ✓ SQL Injection protected |
| TC-PERF-001 | Fail | QA05 | 30/01 | 30/01 | Load time 4.5s, over 3s limit |

**Module Status:** 33% (1/3 pass)

---

## Team Workload

| Tester | Module | Cases Assigned | Completed | In Progress | Blocked |
|--------|--------|----------------|-----------|------------|---------|
| QA01 | Auth, Job | 7 | 6 | 0 | 0 |
| QA02 | Auth, Security | 5 | 3 | 1 | 1 |
| QA03 | Resume | 5 | 3 | 0 | 1 |
| QA04 | CV Analysis | 5 | 3 | 1 | 1 |
| QA05 | CV Analysis, Perf | 3 | 1 | 1 | 1 |

**Total:** 25 cases | 16 completed | 3 in progress | 5 blocked

---

## Risk & Blockers

### Blocking Issues

1. **History feature not ready** - Delays TC-CV-005
   - Impact: Cannot verify resume history tracking
   - Workaround: Schedule for UAT phase
   - Target fix: 05/02

2. **Edit Resume feature incomplete** - Delays TC-RESUME-004
   - Impact: Cannot verify data update
   - Workaround: Test manual SQL update
   - Target fix: 06/02

3. **Filter implementation missing** - Delays TC-JOB-003
   - Impact: Cannot verify filter functionality
   - Workaround: Test on beta branch
   - Target fix: 08/02

---

## Testing Velocity

### Trend (Test cases per day)

```
Day 1 (28/01): 4 cases completed
Day 2 (29/01): 7 cases completed
Day 3 (30/01): 5 cases completed
Average: 5.3 cases/day
```

**Projection:** All 25 cases should be completed by 05/02

---

## Known Issues Summary

| Priority | Count | Owner | Status |
|----------|-------|-------|--------|
| P0-Critical | 1 | DEV03 | Database race condition - IN PROGRESS |
| P1-High | 5 | Various | 1 fixed, 4 open |
| P2-Medium | 3 | Various | 2 open, 1 retest |
| P3-Low | 1 | DEV06 | Mobile UI - Backlog |

---

## Sign-off Readiness

| Criterion | Status | Notes |
|-----------|--------|-------|
| Functionality | 72% | 5 blockers pending |
| Performance | 50% | Load time issue needs optimization |
| Security | 100% | SQL injection protected, session timeout OK |
| UX/UI | 60% | Mobile responsive issues identified |
| Documentation | 80% | Most features documented |

**Go/No-Go Decision:** Not Ready (pending bug fixes and blocker resolution)

---

## Next Steps

1. **Week of 03/02:**
   - DEV team fixes P0 & P1 bugs
   - QA retests TC-CV-003 (file size validation)
   - Resume history feature completion

2. **Week of 10/02:**
   - Final regression testing
   - Performance optimization
   - UAT preparation

3. **Release Gate:**
   - 95% pass rate required
   - 0 critical/high bugs
   - Performance < 3s for main pages

---

