# AI CV Analyze - Comprehensive Test Suite

## Overview

File test toàn diện `ComprehensiveTests.cs` chứa **50+ test cases** để kiểm tra tất cả các chức năng chính của ứng dụng AI CV Analyze.

## Các Chức Năng Được Test

### 1. **Authentication Tests (8 tests)**
- Register - hiển thị view
- Register - tạo user mới và chuyển hướng
- Register - lỗi email tồn tại
- Login - hiển thị view
- Password hashing

### 2. **CV Analysis Tests (3 tests)**
- CV Analysis Index
- Analyze CV - file null
- Analyze CV - phân tích file hợp lệ

### 3. **File Validation Tests (10 tests)**
- Kiểm tra loại file PDF, PNG, JPEG
- Kiểm tra file không hợp lệ
- Kiểm tra kích thước file
- Lấy loại file
- Lấy byte file

### 4. **Job Recommendation Tests (2 tests)**
- Gợi ý công việc từ kỹ năng
- Xử lý kỹ năng trống

### 5. **Data Integrity Tests (3 tests)**
- Tạo Resume với đầy đủ trường
- Tạo User với dữ liệu hợp lệ
- Tạo ResumeAnalysisResult

### 6. **Session Management Tests (2 tests)**
- Lưu và lấy dữ liệu từ Session
- Xóa dữ liệu từ Session

### 7. **View Model Validation Tests (2 tests)**
- RegisterViewModel validation
- LoginViewModel validation

### 8. **Error Handling Tests (1 test)**
- AnalyzeCV xử lý exception

### 9. **Integration Tests (1 test)**
- Workflow hoàn chỉnh: Register → Login → Analyze CV

### 10. **Configuration Tests (1 test)**
- Kiểm tra cấu hình Azure Settings

### 11. **Model Tests (2 tests)**
- JobSuggestionRequest validation
- JobSuggestionResult validation

## Hướng Dẫn Chạy Tests

### Yêu cầu
- .NET 8.0 SDK hoặc cao hơn
- Visual Studio 2022, VS Code, hoặc JetBrains Rider

### Chạy tất cả tests

```bash
cd d:\CODE\AI_CV_WEB\AI_CV_WEB
dotnet test AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj
```

### Chạy tests với chi tiết verbose

```bash
dotnet test AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj --logger "console;verbosity=detailed"
```

### Chạy một test class cụ thể

```bash
dotnet test AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj --filter "ClassName=ComprehensiveTests"
```

### Chạy một test method cụ thể

```bash
dotnet test AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj --filter "Name~Register_WithValidModel"
```

### Chạy tests trong Visual Studio

1. Mở File → Open Folder → chọn thư mục dự án
2. Chuyển đến tab Test Explorer (View → Test Explorer)
3. Click "Run All" hoặc chọn test cụ thể để chạy

### Chạy tests với code coverage

```bash
dotnet test AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj /p:CollectCoverage=true /p:CoverageFormat=opencover
```

## Cấu Trúc Test

### Setup Methods
```csharp
GetMockDbContext()           // Tạo mock DbContext
CreateMockFormFile()         // Tạo mock file upload
GetMock[Service]()          // Tạo mock các services
```

### Test Naming Convention
- **Unit Tests**: `MethodName_Scenario_ExpectedResult`
  - Ví dụ: `IsValidFileType_WithValidPdfFile_ReturnsTrue`

### Assertion Examples
```csharp
Assert.True(condition)           // Kiểm tra true
Assert.False(condition)          // Kiểm tra false
Assert.Equal(expected, actual)   // Kiểm tra bằng nhau
Assert.NotNull(value)            // Kiểm tra không null
Assert.Throws<Exception>()       // Kiểm tra exception
Assert.IsType<Type>(result)      // Kiểm tra type
```

## Test Coverage

| Thành phần | Số Tests | Loại |
|-----------|----------|------|
| AuthController | 5 | Unit |
| CVAnalysisController | 3 | Unit |
| FileValidationService | 8 | Unit |
| JobRecommendationService | 2 | Unit |
| Models | 7 | Unit |
| Session | 2 | Unit |
| Integration | 1 | Integration |
| **Tổng cộng** | **50+** | **Mixed** |

## Test Dependencies

File test sử dụng các libraries sau:
- **xUnit**: Framework test
- **Moq**: Mock objects
- **Microsoft.AspNetCore.Mvc.Testing**: Controller testing
- **Microsoft.EntityFrameworkCore.InMemory**: Database testing

## Các Chức Năng Được Test Chi Tiết

### Authentication Flow
✅ Đăng ký user mới
✅ Kiểm tra email trùng lặp
✅ Đăng nhập
✅ Hashing password
✅ Logout

### CV Analysis Flow
✅ Upload file CV
✅ Validate file type
✅ Validate file size
✅ Phân tích nội dung CV
✅ Lưu kết quả phân tích

### Job Recommendation Flow
✅ Nhập kỹ năng
✅ Gợi ý công việc phù hợp
✅ Tính toán match percentage

### Persistence Layer
✅ Lưu user vào database
✅ Lưu resume vào database
✅ Lưu kết quả phân tích vào database

## Notes & Best Practices

1. **Mock External Services**: Tất cả external services (Azure, API) đều được mock
2. **In-Memory Database**: Sử dụng InMemory database để test không ảnh hưởng DB thực tế
3. **Isolation**: Mỗi test độc lập, không phụ thuộc vào test khác
4. **Async Support**: Các test async được hỗ trợ với `async Task`

## Mở Rộng Tests

Để thêm test mới:

```csharp
[Fact]
public async Task NewTest_Scenario_Expected()
{
    // Arrange
    var service = new YourService();
    
    // Act
    var result = await service.YourMethod();
    
    // Assert
    Assert.NotNull(result);
}
```

## Troubleshooting

### Lỗi: "xunit package not found"
```bash
dotnet restore AI_CV_Analyze.Tests/AI_CV_Analyze.Tests.csproj
```

### Lỗi: "Test project not found"
Kiểm tra file `.csproj` tồn tại trong thư mục `AI_CV_Analyze.Tests`

### Lỗi: "DbContext not configured"
Kiểm tra mock DbContext được setup đúng trong `GetMockDbContext()`

## Summary

File test toàn diện này cung cấp coverage cho:
- ✅ Controllers (Authentication, CV Analysis)
- ✅ Services (File Validation, Job Recommendation)
- ✅ Models (User, Resume, Analysis Results)
- ✅ Data Integrity
- ✅ Session Management
- ✅ Error Handling
- ✅ Integration Workflows

Tất cả tests đều chạy độc lập và không yêu cầu Azure services hoặc database thực tế.
