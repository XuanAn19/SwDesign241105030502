# LAB2: PHÂN TÍCH CÁC CA SỬ DỤNG TRONG PAYROLL SYSTEM

## 1. Ca sử dụng Create Administrative Report

### a. Các lớp phân tích
- **Lớp Boundary**: `PayrollAdministratorUI`
- **Lớp Controller**: `ReportController`
- **Lớp Entities**: `ReportGenerator`, `Report`, `ReportStorage`

### b. Biểu đồ Sequence
![CreateAdministrativeReport](https://www.planttext.com/api/plantuml/png/f9InJkD048RxVOefEGbU8BeWWf5yI5T43XIKZhEALonhv8mZkJnTGK6LYkAQS152GegWeB8BYaMynpu1ht2pkyab4LPq9roil3kVv_zdTkJt-kLWX76EnOLaB4umow4RbtacPMTm8PGOOHxRmtW4tGvZ_QnGWpWl6w7JOukT7hCaKqXHYFXbbcFWTvAxB570k4A1vI8QSiN_IaJXPj2TRHxr28s7t4LwZBNRS6AgsmmEDIs9NTfjrkt0tZuvQS6PVYWWCTLz0UYu_f9ZP9UWADW6mTZKlmIWS4Igvx0ZCqB42ja5DTJJ4lgcUaHudTWqoxDpKxqWOAghP1TGFoXGgVwjO4pvr1SM1Sv1s5hKi99Tg7mYDuibmf6f7q4AKryLa9fwTWcItXdG4uLEUobDkUi95VhsH9WQhhN9mG5ytVD6SrFDR5T-hBbzdUYPxvoZgR6MfiP-8-cVYaoQ-dej9PSZlk7jFDNF9DfiaVAS-BZBGE4RiKq7Fy1S3ToaV7zxAlvXKAJ5ckOaDFLSGBb9Bc-nr_BvFyoElPgndjejcSlrtD-DWydhLAM4asDVSw-nvaPsLVzsrhLx8MUgExJZT2ksoTck-UB-fy_-2zVi0rhjB-KF0000__y30000)

### c. Nhiệm vụ của từng lớp phân tích:
- **PayrollAdministratorUI**: Lớp giao diện hiển thị form nhập tiêu chí báo cáo và tùy chọn lưu hoặc hủy báo cáo.
- **ReportController**: Xử lý yêu cầu tạo và lưu báo cáo, kiểm tra dữ liệu và điều phối các thao tác.
- **ReportGenerator**: Tạo báo cáo dựa trên tiêu chí đầu vào.
- **Report**: Chứa nội dung báo cáo được tạo.
- **ReportStorage**: Xử lý việc lưu báo cáo vào vị trí chỉ định.

### d. Một số thuộc tính và phương thức của các lớp phân tích:
- **PayrollAdministratorUI**:
  + `requestReportCreation()`: Gửi yêu cầu tạo báo cáo đến ReportController.
  + `displayReport(report: Report)`: Hiển thị báo cáo đã tạo.
  + `requestSaveReport()`: Gửi yêu cầu lưu báo cáo.
  + `displayErrorMessage()`: Hiển thị thông báo lỗi.
- **ReportController**:
  + `report`: Đối tượng báo cáo.
  + `createReport()`: Tạo báo cáo với các tiêu chí được cung cấp.
  + `saveReport()`: Lưu báo cáo.
  + `displayError()`: Hiển thị thông báo lỗi.
- **ReportGenerator**:
  + `generateReport()`: Tạo và trả về đối tượng báo cáo.
  + `validateCriteria()`: Kiểm tra tính hợp lệ của các tiêu chí.
- **Report**:
  + `content`: Nội dung báo cáo.
  + `getContent()`: Trả về nội dung báo cáo.
  + `getSummary()`: Tóm tắt báo cáo.
- **ReportStorage**:
  + `fileName`: Tên tệp báo cáo.
  + `saveReport()`: Lưu báo cáo.
  + `validateLocation()`: Kiểm tra tính hợp lệ của vị trí lưu trữ.

### e. Mối quan hệ giữa các lớp:
- **PayrollAdministratorUI** tương tác với **ReportController** để yêu cầu tạo và lưu báo cáo.
- **ReportController** gọi **ReportGenerator** để tạo báo cáo và **ReportStorage** để lưu báo cáo.
- **ReportGenerator** tạo đối tượng **Report** dựa trên các tiêu chí và trả về cho **ReportController**.

### f. Biểu đồ lớp mô tả lớp phân tích
![ReportAdminitrative](https://www.planttext.com/api/plantuml/png/L8x13S8m34Nldi8BT8UcJOMu8H0316AXIAc37FUGsJWm4YkGjBtqzEJ_REl_Fjy-gnDTvWZmI0jx9mKlhaYAqVWvSCWgJfFSp-Wo6dWcrYhnIkyaEcvJ96bs068DMdPv8gRrjhdnw5faZz6jRheNDJC16Eow-d1e676ZtJc1NO48q1FxrluF003__mC0)

## 2. Ca sử dụng Create Employee Report

### a. Các lớp phân tích
- **Lớp Boundary**: `EmployeeUI`
- **Lớp Controller**: `EmployeeReportController`
- **Lớp Entities**: `ReportGenerator`, `Report`, `ReportStorage`

### b. Biểu đồ Sequence
![CreateEmployeeReport](https://www.planttext.com/api/plantuml/png/Z5JDYXD14BxtKnHxqiE-G0wocIIx2gk8Hj1ZfzDaHcUwGwSdx1p5moABXnn4H0HZa8M5u8gAE7tmq67Vev_0Lx2w9_zcqJaqpLTVVLLVTJ6_pQ-3WQPAvrbAADDIGIlhfxBWd7HaBhfK5KlaqHsW0wWJ9eLMCbtY3tXVAjseq9Ghpue85phH1LJ18owuebuUOutDc8UQcz13PD8Uzv4MwL9DEtJ0uRwIJpdJTwd0M8O9pSWp3WbPT0Bxjw1UWyYLdpNCHguypw6m5pcmSDMk74leM3mO7gJk-L4DZfoP9g2Jm8pjT8r2Kmt74lEI5GYf_G1xRMTUYnuCd1b1Bt7clOSp6EBrbA6CXCoPjngwpdm1EnPx1F2BVCd36hHLNi19xifFoA0YXe4TinWoEwaKcVs6ufLOI3o4_QhPjdBb1DBGqdzbHlEft4ReXG0TEtFspynWu5viFme4x8K8IbjZRg3IAt5DPIww95HkOCkRSmyZeQ0LwgvDdJGylVaNdJHtML-fpKROG7XQijFgYhdjQV7-JrOhabvTvciPDxJzMM2UDtgpac_Lu7YJD7Jc7QwFTpF4pHZwecXkMdNcar_wPJHd8YQjXPV7E7iGiIkdOjlBR7HrwSo4XMQMdjfn66zdXn5VyZcSh2bksY1XZUS2EX7mhBeo-nLVhlmk8COL_y4ME7OywUESpUdr2wJNsa7ccsJNXhIHEfq_sBm48kS5PbE94njNUq8EyCG_q1y0003__mC0)

### c. Nhiệm vụ của từng lớp phân tích:
- **EmployeeUI**: Giao diện người dùng hiển thị các form và nhận các yêu cầu từ nhân viên.
- **EmployeeReportController**: Xử lý yêu cầu từ EmployeeUI và tạo báo cáo bằng **ReportGenerator**.
- **ReportGenerator**: Chịu trách nhiệm tạo báo cáo dựa trên các tiêu chí và thông tin từ cơ sở dữ liệu.
- **Report**: Đại diện cho báo cáo đã tạo ra, chứa nội dung và các chi tiết liên quan.
- **ReportStorage**: Lưu báo cáo vào vị trí chỉ định.

### d. Một số thuộc tính và phương thức của các lớp phân tích:
- **EmployeeUI**:
  + `reportType`: Loại báo cáo.
  + `startDate`: Ngày bắt đầu.
  + `endDate`: Ngày kết thúc.
  + `chargeNumber`: Mã công việc (nếu có).
  + `displayReport(report: Report)`: Hiển thị báo cáo.
  + `requestCreateReport()`: Gửi yêu cầu tạo báo cáo.
  + `displayErrorMessage()`: Hiển thị thông báo lỗi.
- **EmployeeReportController**:
  + `createReport()`: Tạo báo cáo cho nhân viên dựa trên yêu cầu.
  + `validateReportCriteria()`: Kiểm tra tính hợp lệ của các tiêu chí.
  + `saveReport()`: Lưu báo cáo vào **ReportStorage**.
  + `displayError()`: Hiển thị thông báo lỗi.
- **ReportGenerator**:
  + `generateReport()`: Tạo báo cáo.
  + `validateCriteria()`: Kiểm tra tính hợp lệ của các tiêu chí đầu vào.
- **Report**:
  + `content`: Nội dung báo cáo.
  + `getContent()`: Trả về nội dung báo cáo.
  + `getSummary()`: Tóm tắt báo cáo.
- **ReportStorage**:
  + `saveReport()`: Lưu báo cáo vào một tệp.
  + `validateLocation()`: Kiểm tra vị trí lưu trữ.

### e. Mối quan hệ giữa các lớp:
- **EmployeeUI** yêu cầu báo cáo từ **EmployeeReportController** và nhận kết quả.
- **EmployeeReportController** gọi **ReportGenerator** để tạo báo cáo và **ReportStorage** để lưu báo cáo.

## 3. Ca sử dụng Login

### a. Các lớp phân tích
- **Lớp Boundary**: `LoginUI`
- **Lớp Controller**: `LoginController`
- **Lớp Entities**: `Authenticator`, `User`

### b. Biểu đồ Sequence

### c. Nhiệm vụ của từng lớp phân tích:

- **LoginUI (Boundary)**: Giao diện người dùng thực hiện quá trình đăng nhập. Lớp này nhận thông tin đăng nhập (tên người dùng và mật khẩu) và cung cấp các chức năng hiển thị lỗi khi thông tin không hợp lệ.
  
- **LoginController (Controller)**: Lớp này quản lý logic đăng nhập. Sau khi nhận thông tin đăng nhập từ **LoginUI**, nó gọi **Authenticator** để xác thực tên và mật khẩu. Nếu thông tin hợp lệ, nó thực hiện đăng nhập, nếu không sẽ xử lý lỗi.

- **Authenticator (Entity)**: Lớp này thực hiện việc kiểm tra tính hợp lệ của tên đăng nhập và mật khẩu. Nó xác thực thông qua cơ sở dữ liệu hoặc danh sách các thông tin hợp lệ và trả kết quả về **LoginController**.

- **User (Entity)**: Đại diện cho thông tin của người dùng trong hệ thống, bao gồm tên đăng nhập, mật khẩu và vai trò (ví dụ: quản trị viên, nhân viên). Nó cung cấp các phương thức để kiểm tra mật khẩu và lấy vai trò của người dùng.

### d. Một số thuộc tính và phương thức của các lớp phân tích:

- **LoginUI**:
  - `username`: Tên người dùng.
  - `password`: Mật khẩu.
  - `getCredentials()`: Nhận tên và mật khẩu từ người dùng.
  - `displayError(message: String)`: Hiển thị thông báo lỗi nếu thông tin đăng nhập không hợp lệ.
  - `displayLoginScreen()`: Hiển thị giao diện đăng nhập cho người dùng.

- **LoginController**:
  - `authenticator`: Đối tượng thực hiện xác thực tên và mật khẩu.
  - `processLogin(username: String, password: String)`: Nhận tên và mật khẩu từ **LoginUI**, gọi **Authenticator** để kiểm tra tính hợp lệ và thực hiện đăng nhập.
  - `handleLoginError()`: Xử lý khi tên hoặc mật khẩu không hợp lệ, yêu cầu người dùng nhập lại hoặc hủy đăng nhập.

- **Authenticator**:
  - `validUsernames`: Danh sách tên người dùng hợp lệ.
  - `validPasswords`: Danh sách mật khẩu hợp lệ (hoặc kiểm tra với cơ sở dữ liệu).
  - `validateCredentials(username: String, password: String)`: Kiểm tra tính hợp lệ của tên người dùng và mật khẩu.

- **User**:
  - `username`: Tên đăng nhập của người dùng.
  - `password`: Mật khẩu của người dùng.
  - `role`: Vai trò của người dùng (ví dụ: quản trị viên, nhân viên).
  - `isValidPassword(password: String)`: Kiểm tra mật khẩu có đúng với người dùng không.
  - `getRole()`: Lấy vai trò của người dùng sau khi đăng nhập thành công.

### e. Mối quan hệ giữa các lớp:
- **LoginUI** (Boundary): Tương tác với người dùng, nhận thông tin đăng nhập và hiển thị lỗi khi cần thiết.
- **LoginController** (Controller): Quản lý quá trình đăng nhập, sử dụng **Authenticator** để xác thực tên và mật khẩu, sau đó thực hiện đăng nhập hoặc xử lý lỗi.
- **Authenticator** (Entity): Kiểm tra tính hợp lệ của tên người dùng và mật khẩu, trả về kết quả cho **LoginController**.
- **User** (Entity): Đại diện cho người dùng trong hệ thống, chứa thông tin đăng nhập, mật khẩu và vai trò.

### f. Biểu đồ lớp mô tả lớp phân tích
![login](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XTNKdvfNafYKQM2JtvwPbwefq9YiO8ZLt9-NabHVWv4q1d2oKaj0aawSQNcbMIML2eubfPaW9Z9YINvO1bdc4neCKIf2nUNeuAkBb2B4uXoXb0kNCvWIe6Boo4rBmNa2W00003__mC0)


## 4. Ca sử dụng Maintain Employee Information
### a. Các lớp phân tích
- **Lớp Boundary:** PayrollAdministratorInterface, EmployeeInformationForm
- **Lớp Controller:** MaintainEmployeeController
- **Lớp entities:** Employee

### b. Biểu đồ Sequence
![MaintainEmployeeInformation](https://www.planttext.com/api/plantuml/png/v5OzRzD06DxlLxpAGZ8Wzaf1ZKAX4IBA4A4odXstFjK-1-UCwfa98IGG0mCBeQeg1JgLoHuwNF_8_OB-1TwpJU9pxDQ2RaHAx7llUTxFvnpVf5Ux2q534VaUeRO8GkXCQ1m6dWU3cSyuMuYGeha3T06J0I5M4F4P3UCrpe2Dk732Gsex6NwzAh7s_BaNn8upueT1w5F10luKRpAylY5sm0NwXSuBohZ0xn_6CD_md3oPpP8uN31HyftjuuAG1p1rvSe7xihl7DumkUAato-CuypuKXkXtoUJ0JnylCaPTc3eglG3XywMZmxPm92pIGL9h-Gg0bibvr4jiOIjH2iHXIj_yICGZ1kP6q5riv2rprJwbYD3fU_1qei8V9NyQ7IIyP2FvMA54I8mvjdyBhXHupELNh0cXbaXZW49KvKi0x1KSihXo6LbF6QRVcMtz6KQ8WqyzC1WzCIWTh71txWBjawafySzLCd5735u4TMfvtlZVA_ry0sFzIMtbKChLwq4OlR135yTR0LREvumYk4aGdXJNcXs0dH5DA5QOtb2hKHnFzf5sZiS_WB5IEzDld3zIPxgpgqdLTinOvIrkcwfw6ELN0bu7MdBjfmFv2MjoZYpjPPlrKDRhMxp_WTXDbHr8fTsFcoEzvUqfgxRqDlJEQX2weg__YYNg8OPLXzL98f79USLLTz9G4rR-fJL1FiRPL9FmFEYeVAdhuzmSXQRp-Ro4NcavTGZW9_cuCRZe1YN9V5_mrFf5mRTSSdxSH5SfP-HeVFjuMl0BCziNwNdSLOgTFyfSEOYwvkhNUOHTl4NNvT-0m00__y30000)

### c. Nhiệm vụ của từng lớp phân tích:
- **PayrollAdministratorInterface:**
  + Cung cấp giao diện để Quản trị viên tiền lương lựa chọn thao tác muốn thực hiện (thêm, cập nhật, hoặc xóa nhân viên).
  + Hiển thị các tùy chọn và yêu cầu Quản trị viên cung cấp thông tin liên quan (ví dụ: ID nhân viên khi cập nhật hoặc xóa).
  + Quản lý việc hiển thị thông báo lỗi hoặc xác nhận khi cần thiết (ví dụ: khi không tìm thấy nhân viên hoặc khi Quản trị viên xác nhận xóa).
  
- **EmployeeInformationForm:** 
  + Hiển thị biểu mẫu để Quản trị viên nhập thông tin nhân viên (bao gồm tên, địa chỉ, lương, số an sinh xã hội, và các thông tin khác).
  + Thu thập thông tin từ Quản trị viên và chuyển tiếp cho lớp Controller để xử lý (khi thêm hoặc cập nhật nhân viên).
  + Cung cấp giao diện để chỉnh sửa thông tin nhân viên khi thực hiện thao tác cập nhật.

- **MaintainEmployeeController:**
  + Xử lý các yêu cầu từ PayrollAdministratorInterface (chọn thao tác thêm, cập nhật, hoặc xóa nhân viên).
  + Khi thao tác là thêm hoặc cập nhật, yêu cầu EmployeeInformationForm thu thập thông tin nhân viên từ Quản trị viên.
  + Sau khi nhận thông tin, MaintainEmployeeController sẽ xử lý và thực hiện các thay đổi cần thiết trong lớp Employee (thêm, cập nhật, hoặc xóa).
  + Quản lý các thông báo và trạng thái kết quả (thành công hoặc lỗi) sau khi hoàn thành thao tác.
  + Cung cấp các thông tin phản hồi (ví dụ: trả lại ID nhân viên khi thêm mới hoặc kết quả xóa khi thao tác hoàn tất).
  
- **Employee:**
  + Lưu trữ thông tin về nhân viên như tên, địa chỉ, loại nhân viên, lương, và các dữ liệu liên quan khác.
  + Cung cấp các phương thức để tạo mới, cập nhật và xóa thông tin nhân viên từ cơ sở dữ liệu.
  + Khi thao tác là xóa, sẽ đánh dấu nhân viên là đã bị xóa trong hệ thống (thay vì xóa hoàn toàn).

### d. Một số thuộc tính và phương thức của các lớp phân tích:
- **PayrollAdministratorInterface:**
  + selectedAction: Lưu trữ thao tác mà Quản trị viên chọn (thêm, cập nhật, xóa nhân viên).
  + employeeId: ID của nhân viên khi Quản trị viên thực hiện cập nhật hoặc xóa.
  + chooseAction(): Cho phép Quản trị viên chọn thao tác (thêm, cập nhật, xóa).
  + displayEmployeeForm(): Hiển thị biểu mẫu thông tin nhân viên.
  + showMessage(String message): Hiển thị thông báo cho Quản trị viên (ví dụ: thông báo lỗi hoặc thành công).
  + getEmployeeDetails(): Thu thập thông tin nhân viên từ Quản trị viên.

- **EmployeeInformationForm:**
  + employeeName: Tên của nhân viên.
  + employeeType: Loại nhân viên (giờ, lương cố định, hoa hồng).
  + salaryOrHourlyRate: Lương hoặc mức lương theo giờ.
  + displayForm(): Hiển thị biểu mẫu nhập thông tin nhân viên.
  + getInput(): Thu thập thông tin từ Quản trị viên và trả về dưới dạng đối tượng.

- **MaintainEmployeeController:**
  + action: Hành động mà Quản trị viên muốn thực hiện (thêm, cập nhật, xóa).
  + employee: Đối tượng nhân viên để thao tác (thêm, cập nhật, xóa).
  + handleAddEmployee(): Xử lý thêm mới nhân viên vào hệ thống.
  + handleUpdateEmployee(): Xử lý cập nhật thông tin nhân viên.
  + handleDeleteEmployee(): Xử lý xóa nhân viên khỏi hệ thống.
  + validateEmployeeData(): Kiểm tra tính hợp lệ của thông tin nhân viên (trước khi thêm hoặc cập nhật).

- **Employee:**
  + employeeId: ID của nhân viên.
  + name: Tên nhân viên.
  + employeeType: Loại nhân viên (giờ, lương cố định, hoa hồng).
  + salary: Lương của nhân viên (dành cho nhân viên lương cố định).
  + hourlyRate: Mức lương theo giờ (dành cho nhân viên làm theo giờ).
  + commissionRate: Mức hoa hồng (dành cho nhân viên hoa hồng).
  + status: Trạng thái nhân viên (đã xóa hay không).
  + createEmployee(): Tạo bản ghi nhân viên mới.
  + updateEmployee(): Cập nhật thông tin nhân viên.
  + deleteEmployee(): Đánh dấu nhân viên là đã xóa.
  + getEmployeeById(String employeeId): Truy xuất thông tin nhân viên theo ID.
  + validateData(): Kiểm tra tính hợp lệ của thông tin nhân viên.

### e. Mối quan hệ giữa các lớp:
- **PayrollAdministratorInterface:** Giao tiếp trực tiếp với Quản trị viên tiền lương. Gửi yêu cầu và nhận phản hồi từ MaintainEmployeeController. Hiển thị biểu mẫu và thông báo cho người dùng.
- **EmployeeInformationForm:** Được PayrollAdministratorInterface gọi để hiển thị biểu mẫu thông tin nhân viên. Gửi thông tin nhân viên đã nhập tới MaintainEmployeeController.
- **MaintainEmployeeController:** Xử lý các yêu cầu từ PayrollAdministratorInterface (thêm, cập nhật, xóa nhân viên). Tương tác với Employee để thực hiện thao tác trên dữ liệu (thêm, cập nhật, xóa). Cập nhật kết quả và phản hồi lại cho PayrollAdministratorInterface.
- **Employee:** Là thực thể dữ liệu, lưu trữ thông tin nhân viên. MaintainEmployeeController thao tác trên Employee để thêm, cập nhật hoặc xóa thông tin nhân viên.

### f. Biểu đồ lớp mô tả lớp phân tích
![maintainEmployee](https://www.planttext.com/api/plantuml/png/L90nRW9134Lxdy8Nu0AfM1Q8A2Abo0NCxi1QclMWMI_IdY27e4hAI8Y6YYaezYHp0gwG6KK1KLYodj__XM_XEksKlFQj1LYxNcho0xxJu9srHTsoSAUUrFcLgF4RgWnIXyN3NRGxwmPZLh9nlYLb9ykqP6i6bHDDJVX6B9hcNox_k3K-UoKOKTP7LuPpW08d4opn1L-P72h7otK7ipkCuSYepNYMRJeAIZD-2-vv_14eipLFraUJe-DNXViO3enr32Uq7CDd_nI0gP4wV-4N003__mC0)


## 5. Ca sử dụng Maintain Purchase Order

### a. Các lớp phân tích
- **Lớp Boundary**: CommissionedEmployeeInterface, PurchaseOrderForm
- **Lớp Controller**: MaintainPurchaseOrderController
- **Lớp Entities**: PurchaseOrder

### b. Biểu đồ Sequence
![MaintainPurchaseOrder](https://www.planttext.com/api/plantuml/png/l5IzRjim4Dxv53UcGFe26GBRSf86QDeE6TAHaTcGY4Iw56NKOz6fA39axX8dA0guyDG21QGX0uEy1vyWhv2Z5FzGbJ9MW21GzttVVNT7yg6yxMM6QfEd2Q6nKHeYbQOYouIIRBINZXCrPOoGKvNB4TNJrl2XD4n_e343ca5_ZNsNwvZJZBtL8wRtbKvzV41Y9OrM2HnH8Gs-0IogWmdJ7XmH9eqm3IaV6HBIPWLUxa8VTY3YhhoGO3XLOEmiXgrZRkVfDaIkM8n1SloORJYnl-aBqlUi25a7hbm8cDfv3h4hVkO1tnKprSwFbbdVRpBj7ta6HaYukxoVIU3s2jTRXyDWpPKh_iQRw9WB_BhYrZmP6w3mA-7ABxuSLtw3Kx_88NN5hwuyPB2qz8PNXZjWZSexK8Gc1ghwWz-0JrNw40N-2QE_yhkeGCDbbcFjYXkOkF8pX7rOQrN3ov6ERVmnRi2mEGfxRwybJ8ITIyAIZ0KZwJRu6lMcWPZXJ662JeiTtV3mzi5Cx1KwTELNoI73Xj8DYOesQAamo69lQc9eFIZm6LUh8axyZgtmqcTPaV4qZUff-etxFtlLTFNfsVojxbghypfrLNMQjYkXCQLpVxRWO-wzhyut8JrKyRVW8m000F__0m00)

### c. Nhiệm vụ của từng lớp phân tích:
- **CommissionedEmployeeInterface**:
  - Cho phép nhân viên có hoa hồng chọn thao tác họ muốn thực hiện (thêm, cập nhật, hoặc xóa đơn hàng).
  - Hiển thị thông báo và yêu cầu nhập thông tin liên quan đến đơn hàng (ví dụ: ID đơn hàng, thông tin khách hàng, sản phẩm, v.v.).
  - Hiển thị các thông báo lỗi hoặc xác nhận (ví dụ: đơn hàng không tồn tại, không phải của nhân viên này, hoặc đơn hàng đã đóng).

- **PurchaseOrderForm**:
  - Hiển thị biểu mẫu để nhân viên nhập thông tin chi tiết về đơn hàng (ví dụ: khách hàng, sản phẩm, địa chỉ thanh toán, ngày mua).
  - Thu thập dữ liệu từ nhân viên và chuyển tiếp cho Controller để xử lý.

- **MaintainPurchaseOrderController**:
  - Xử lý các yêu cầu từ CommissionedEmployeeInterface (thêm, cập nhật, xóa đơn hàng).
  - Khi thao tác là Create, yêu cầu PurchaseOrderForm thu thập thông tin đơn hàng từ nhân viên.
  - Kiểm tra tính hợp lệ của thông tin đơn hàng (ví dụ: đảm bảo đơn hàng không bị đóng, là của nhân viên này).
  - Tương tác với PurchaseOrder (lớp thực thể) để tạo, cập nhật, hoặc xóa đơn hàng.
  - Trả về kết quả thành công hoặc lỗi cho CommissionedEmployeeInterface.

- **PurchaseOrder**:
  - Quản lý và xử lý dữ liệu liên quan đến đơn hàng, bao gồm việc tạo, cập nhật, xóa và truy vấn thông tin.

### d. Một số thuộc tính và phương thức của các lớp phân tích:

- **CommissionedEmployeeInterface**:
  - `selectedAction`: Lưu trữ hành động mà nhân viên chọn (Tạo, Cập nhật, Xóa đơn hàng).
  - `employeeId`: ID của nhân viên đang thực hiện thao tác.
  - `selectAction()`: Cho phép nhân viên chọn thao tác (Tạo, Cập nhật, Xóa).
  - `displayOrderForm()`: Hiển thị biểu mẫu để nhân viên nhập thông tin đơn hàng.
  - `displayMessage(String message)`: Hiển thị thông báo thành công hoặc lỗi cho nhân viên.
  - `getEnteredOrderInfo()`: Lấy thông tin đơn hàng mà nhân viên đã nhập vào biểu mẫu.

- **PurchaseOrderForm**:
  - `orderId`: ID của đơn hàng cần cập nhật hoặc xóa.
  - `customerName`: Tên khách hàng.
  - `billingAddress`: Địa chỉ thanh toán của khách hàng.
  - `products`: Danh sách các sản phẩm trong đơn hàng.
  - `orderDate`: Ngày tạo đơn hàng.
  - `collectOrderDetails()`: Thu thập thông tin chi tiết về đơn hàng từ nhân viên.
  - `displayOrderDetails(PurchaseOrder order)`: Hiển thị chi tiết đơn hàng để nhân viên xem và chỉnh sửa.
  - `getOrderDetails()`: Trả về thông tin đơn hàng mà nhân viên đã nhập.

- **MaintainPurchaseOrderController**:
  - `currentAction`: Hành động hiện tại mà nhân viên đang thực hiện (Tạo, Cập nhật, Xóa).
  - `currentEmployeeId`: ID của nhân viên thực hiện thao tác.
  - `orderService`: Dịch vụ hoặc đối tượng giúp xử lý các thao tác liên quan đến đơn hàng (tạo, cập nhật, xóa).
  - `handleCreateOrder()`: Xử lý thao tác tạo đơn hàng mới.
  - `handleUpdateOrder()`: Xử lý thao tác cập nhật thông tin đơn hàng.
  - `handleDeleteOrder()`: Xử lý thao tác xóa đơn hàng.
  - `validateOrderInfo()`: Kiểm tra tính hợp lệ của thông tin đơn hàng (đảm bảo thông tin hợp lệ trước khi tạo hoặc cập nhật).
  - `getOrderById()`: Lấy thông tin đơn hàng từ ID.
  - `confirmDeletion()`: Xác nhận việc xóa đơn hàng từ nhân viên.

- **PurchaseOrder**:
  - `orderId`: ID của đơn hàng.
  - `customerName`: Tên khách hàng.
  - `customerBillingAddress`: Địa chỉ thanh toán của khách hàng.
  - `products`: Danh sách các sản phẩm trong đơn hàng.
  - `orderDate`: Ngày tạo đơn hàng.
  - `status`: Trạng thái đơn hàng (Mở, Đã đóng).
  - `commissionedEmployeeId`: ID của nhân viên có hoa hồng đã tạo đơn hàng.
  - `createOrder()`: Tạo đơn hàng mới và lưu vào hệ thống.
  - `updateOrder()`: Cập nhật thông tin đơn hàng.
  - `deleteOrder()`: Xóa đơn hàng khỏi hệ thống.
  - `getOrderById(String orderId)`: Lấy thông tin đơn hàng bằng ID.
  - `validateOrder()`: Kiểm tra tính hợp lệ của đơn hàng (còn mở, là của nhân viên hiện tại, v.v.).
  - `closeOrder()`: Đóng đơn hàng sau khi hoàn thành giao dịch.

### e. Mối quan hệ giữa các lớp
- **CommissionedEmployeeInterface** gửi yêu cầu từ nhân viên (chọn thao tác và cung cấp thông tin đơn hàng) đến **MaintainPurchaseOrderController**, nơi xử lý các thao tác như tạo, cập nhật, và xóa đơn hàng.
- **MaintainPurchaseOrderController** yêu cầu **PurchaseOrderForm** hiển thị biểu mẫu cho nhân viên nhập thông tin đơn hàng hoặc hiển thị thông tin đơn hàng cần cập nhật.
- **MaintainPurchaseOrderController** tương tác với **PurchaseOrder** để tạo, cập nhật, hoặc xóa đơn hàng trong hệ thống.
- **PurchaseOrderForm** thu thập thông tin từ nhân viên và cung cấp cho **PurchaseOrder** để tạo hoặc cập nhật thông tin đơn hàng.

### f. Biểu đồ lớp mô tả lớp phân tích
![MaintainPurchaseOrder](https://www.planttext.com/api/plantuml/png/N8wn3G8n34LxJ-45ReUxou54WM25a1WHAR6HunGt6mKZiG842WJ5ro_UqzT_tEvZDQ_MIWOuIUFeTKKdfQHQap35JRbcMObsRAHd7mXznUdh7fk6Ywzqq4Yw5IsTpn24JINZtYUsLtuqzu6PjCiEY2tPtrGd2y24mu0EONutk5uB0ep4iPz-0W00__y30000)

## 6. Ca sử dụng Run Payroll

### a. Các lớp phân tích
- **Lớp Boundary**: `PayrollInterface`, `BankSystemInterface`
- **Lớp Controller**: `RunPayrollController`
- **Lớp Entities**: `Employee`, `Payroll`

### b. Biểu đồ Sequence
![RunPayroll](https://www.planttext.com/api/plantuml/png/X9F1Jjmm48RlVefvWQht7YeskwlI6oezqAF9fciBxnWvOuJFFN3Wn1kGLbLLf1Kz9weukE8z_0HzXOx3Xi22IYwHnj_y_--Pv6ztirEJTEHNHWXPadMm9uEpnamMAusw9YUvACIXzRYGBWp7xv4gzrcM5SWQ9kDn8V5eFzHKhHuHXIWj4ZV21uyRYUbTnLGk4rDH8MaAC5yT6nkglcqs53SjkJONuhc8yEejJE0D5Acz9lXpaTeV7agLsYR0OMg_uHBCxQ_R1fTYajafiv_Y5JCzUPgwDPZuUvkTPdR6x4Vd0vpwr7udMAJk6enEtPa7LF4hmecELtW7ppFCjdPRQdul5TUeW6niS3ZafFQfLBxFBjjyGI2LkdCWny9CaugDtjONqX3igOrWRlXPyakENl6IVNpe1O-KpUq2-EdD2ZPxnrFGiDJIvZkUbmfmcJEfUCa66Is6sHt4fkJ4gLtZmmPHcRfwCSMnqgczyKFqrniTac7CCxkVunRDtyH2Z8lPjHmEg5_CSylB-pZuttQVJFan16eq46A7pVFFyWy00F__0m00)

### c. Mô tả các lớp phân tích:
- **PayrollInterface**: 
  - Cung cấp giao diện cho người dùng để hiển thị thông tin về trạng thái và kết quả của quá trình chạy bảng lương.
  - Người dùng (như Payroll Administrator) sử dụng lớp này để xem báo cáo, xác nhận thanh toán, và thực hiện các thao tác liên quan đến bảng lương.

- **BankSystemInterface**: 
  - Giao diện kết nối và truyền tải dữ liệu đến hệ thống ngân hàng, phục vụ cho việc xử lý thanh toán qua chuyển khoản trực tiếp.

- **RunPayrollController**: 
  - Lớp điều khiển chính trong ca sử dụng Run Payroll, chịu trách nhiệm tính toán lương, in phiếu lương, gửi giao dịch ngân hàng, v.v.

- **Employee**: 
  - Đại diện cho thông tin cá nhân và thanh toán của một nhân viên trong hệ thống.

- **Payroll**: 
  - Lớp này đại diện cho bảng lương, chứa thông tin tính toán và thanh toán của tất cả nhân viên trong mỗi kỳ bảng lương.

### d. Thuộc tính và phương thức chính của các lớp phân tích:
- **PayrollInterface**:
  - `payrollStatus`: Trạng thái quá trình chạy bảng lương (hoàn thành, lỗi, hoặc đang chờ xử lý).
  - `employeeList`: Danh sách nhân viên đã nhận thanh toán.
  - `displayPayrollStatus()`: Hiển thị trạng thái của bảng lương.
  - `displayEmployeePaymentDetails()`: Hiển thị chi tiết thanh toán của từng nhân viên.

- **BankSystemInterface**:
  - `transactionStatus`: Trạng thái của giao dịch ngân hàng.
  - `sendBankTransaction()`: Gửi giao dịch ngân hàng.
  - `retryBankTransaction()`: Thử lại giao dịch khi hệ thống ngân hàng không sẵn sàng.

- **RunPayrollController**:
  - `payrollDate`: Ngày thực hiện bảng lương.
  - `employeeList`: Danh sách nhân viên cần thanh toán.
  - `calculatePay()`: Tính toán lương cho từng nhân viên từ thông tin chấm công, đơn hàng và thông tin cá nhân.
  - `processPayment()`: Thực hiện thanh toán cho nhân viên (in phiếu lương hoặc chuyển khoản ngân hàng).
  - `checkBankSystemStatus()`: Kiểm tra trạng thái hệ thống ngân hàng và xử lý khi không khả dụng.
  - `deleteEmployee()`: Xóa nhân viên bị đánh dấu xóa sau khi bảng lương được xử lý.

- **Employee**:
  - `employeeId`: Mã số nhân viên.
  - `name`: Tên nhân viên.
  - `salary`: Lương cơ bản của nhân viên (đối với nhân viên lương cố định).
  - `hourlyRate`: Mức lương theo giờ (đối với nhân viên lương theo giờ).
  - `benefits`: Các phúc lợi (bảo hiểm, nghỉ phép, v.v.).
  - `paymentMethod`: Phương thức thanh toán (chuyển khoản ngân hàng, nhận phiếu lương, v.v.).
  - `status`: Trạng thái của nhân viên (đang làm việc, đã nghỉ việc, v.v.).
  - `calculatePay()`: Tính toán lương của nhân viên.
  - `generatePaycheck()`: Tạo phiếu lương cho nhân viên.
  - `sendPayment()`: Gửi thanh toán cho nhân viên qua chuyển khoản ngân hàng.

- **Payroll**:
  - `payrollDate`: Ngày thực hiện bảng lương.
  - `employeePayments`: Danh sách thanh toán của nhân viên.
  - `runPayroll()`: Thực hiện việc chạy bảng lương cho tất cả nhân viên.
  - `generateReports()`: Tạo báo cáo bảng lương.
  - `processPayments()`: Xử lý thanh toán cho nhân viên.

### e. Mối quan hệ giữa các lớp:
- **PayrollInterface** tương tác với **RunPayrollController** để yêu cầu xử lý bảng lương.
- **RunPayrollController** lấy thông tin từ **Employee** và tạo ra đối tượng **Payroll**.
- **RunPayrollController** gửi giao dịch đến **BankSystemInterface** nếu nhân viên chọn phương thức thanh toán qua chuyển khoản.
- **RunPayrollController** tạo phiếu lương cho nhân viên nếu phương thức thanh toán là phiếu lương.
- **PayrollInterface** hiển thị kết quả cho người dùng sau khi bảng lương đã hoàn thành.

### f. Biểu đồ lớp mô tả các lớp phân tích
![RunPayroll](https://www.planttext.com/api/plantuml/png/L8x13S8m34Nldi8BT8SsQG_S44nWMYCX4WSbpY6pzS18h413Wn2d9xt_l-NN-koJKjJi7S0bP5ae5ZnIYS6vWoZ7AysCb73unORaVYv9sVyr3Cn1T1lYAKixONVZEDQ61HQzQS79Frme_9cDNzacrKq00tOTMWJJQ2l77LlSioprwJS0003__mC0)


## 1. Lớp `Employee`

Mô tả thông tin nhân viên, bao gồm mã nhân viên, tên, vai trò và lương cơ bản.

```java
public class Employee {
    private String employeeId;
    private String name;
    private String role;
    private double salary;

    public Employee(String employeeId, String name, String role, double salary) {
        this.employeeId = employeeId;
        this.name = name;
        this.role = role;
        this.salary = salary;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public String getName() {
        return name;
    }

    public String getRole() {
        return role;
    }

    public double getSalary() {
        return salary;
    }
}
```

## 2. Lớp `WorkTimeRecord`

```java
public class WorkTimeRecord {
    private String employeeId;
    private Date date;
    private double hoursWorked;
    private String chargeCode;

    public WorkTimeRecord(String employeeId, Date date, double hoursWorked, String chargeCode) {
        this.employeeId = employeeId;
        this.date = date;
        this.hoursWorked = hoursWorked;
        this.chargeCode = chargeCode;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public Date getDate() {
        return date;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    public String getChargeCode() {
        return chargeCode;
    }
}
```
## 3. Lớp `WorkTimeEntryUI`

```java
public class WorkTimeEntryUI {
    private Scanner scanner;

    public WorkTimeEntryUI() {
        scanner = new Scanner(System.in);
    }
 public WorkTimeRecord getWorkTimeDetails(String employeeId) {
        System.out.println("Nhập ngày (YYYY-MM-DD): ");
        Date date = new Date();  // Giả định người dùng nhập đúng định dạng ngày
        System.out.println("Nhập số giờ làm việc: ");
        double hoursWorked = scanner.nextDouble();
        System.out.println("Nhập mã công việc: ");
        String chargeCode = scanner.next();
        return new WorkTimeRecord(employeeId, date, hoursWorked, chargeCode);
    }
}
```
## 4. Lớp WorkTimeController
Lớp này kiểm soát việc nhập và lưu trữ thông tin thời gian làm việc, đồng thời kiểm tra tính hợp lệ của thông tin.

```java

public class WorkTimeController {
    private List<WorkTimeRecord> workTimeRecords;

    public WorkTimeController() {
        workTimeRecords = new ArrayList<>();
    }

    public void submitWorkTimeRecord(Employee employee, WorkTimeEntryUI ui) {
        WorkTimeRecord workTimeRecord = ui.getWorkTimeDetails(employee.getEmployeeId());

        if (validateWorkTimeRecord(workTimeRecord)) {
            workTimeRecords.add(workTimeRecord);
            System.out.println("Đã gửi thông tin thời gian làm việc thành công cho mã nhân viên: " + employee.getEmployeeId());
        } else {
            System.out.println("Lỗi xác thực thông tin thời gian làm việc. Vui lòng kiểm tra lại dữ liệu đã nhập.");
        }
    }

    private boolean validateWorkTimeRecord(WorkTimeRecord workTimeRecord) {
        return workTimeRecord.getHoursWorked() > 0 && workTimeRecord.getHoursWorked() <= 24;
    }

    public void displayWorkTimeRecords() {
        for (WorkTimeRecord workTimeRecord : workTimeRecords) {
            System.out.println("Mã nhân viên: " + workTimeRecord.getEmployeeId() +
                               ", Ngày: " + workTimeRecord.getDate() +
                               ", Số giờ làm việc: " + workTimeRecord.getHoursWorked() +
                               ", Mã công việc: " + workTimeRecord.getChargeCode());
        }
    }
}
```
## 5. Lớp MaintainWorkTimeApp
Ứng dụng chính để quản lý việc nhập và hiển thị thông tin thời gian làm việc.

```java

public class MaintainWorkTimeApp {
    public static void main(String[] args) {
        Employee employee = new Employee("SW001", "Nguyen An", "Software Engineer", 5000);
        WorkTimeEntryUI ui = new WorkTimeEntryUI();
        WorkTimeController controller = new WorkTimeController();

        controller.submitWorkTimeRecord(employee, ui);
        controller.displayWorkTimeRecords();
    }
}
```
## 6. Lớp SalaryCalculator
Lớp này tính toán lương của nhân viên dựa trên số giờ làm việc và lương cơ bản, có thể áp dụng thêm các yếu tố khác như phụ cấp hay trừ lương.

```java

public class SalaryCalculator {

    public double calculateSalary(Employee employee, List<WorkTimeRecord> workTimeRecords) {
        double totalHoursWorked = 0;

        // Tính tổng số giờ làm việc của nhân viên trong tất cả các ngày
        for (WorkTimeRecord record : workTimeRecords) {
            if (record.getEmployeeId().equals(employee.getEmployeeId())) {
                totalHoursWorked += record.getHoursWorked();
            }
        }

        // Tính lương dựa trên số giờ làm việc và lương cơ bản (giả sử 1 giờ làm là lương cơ bản / 160 giờ)
        double hourlyRate = employee.getSalary() / 160; // Ví dụ 1 tháng có 160 giờ làm việc
        double totalSalary = totalHoursWorked * hourlyRate;

        return totalSalary;
    }

    public double applyBonus(double salary, double bonusPercentage) {
        return salary + (salary * bonusPercentage / 100);
    }

    public double applyDeductions(double salary, double deductions) {
        return salary - deductions;
    }
}
```
