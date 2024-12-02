# Lab5 : Payroll System Subsystem Design
## 1. Distribute Subsystem Behavior to Subsystem Elements
Hệ thống được chia thành 4 hệ thống con chính:
**a) Timecard Subsystem**
- Chức năng chính: Quản lý giờ làm việc và trạng thái thẻ chấm công.
- Thành phần chính:
  - `TimecardController`: Xử lý logic nghiệp vụ liên quan đến thẻ chấm công.
  - `TimecardForm`: Giao diện nhập liệu giờ làm việc và trạng thái thẻ.
  - `ProjectManagementDatabase`: Lấy danh sách mã dự án.
- Mô tả chi tiết:
  - Quản lý thông tin giờ làm việc của nhân viên.
  - Lấy danh sách mã dự án từ cơ sở dữ liệu.
  - Cập nhật trạng thái thẻ chấm công.
    
**b) Payroll Processing Subsystem**
- Chức năng chính: Tính toán và thực hiện thanh toán lương.
- Thành phần chính:
  - `PayrollController`: Quản lý logic nghiệp vụ liên quan đến tính toán lương.
  - `BankSystemProxy`: Kết nối với ngân hàng để chuyển khoản lương.
  - `PrinterServiceProxy`: In phiếu lương.
  - `PayrollDatabase`: Lưu trữ thông tin lương.
- Mô tả chi tiết: 
  - Xử lý tính toán lương cho từng nhân viên dựa trên giờ làm việc và trạng thái.
  - Thực hiện thanh toán qua ngân hàng hoặc in phiếu lương.
  - Lưu thông tin lương vào cơ sở dữ liệu.
**c) Employee Management Subsystem**
- Chức năng chính: Quản lý thông tin nhân viên và trạng thái (đang làm việc, bị xóa, nghỉ việc).
- Thành phần chính:
  - `Employee`: Thực thể lưu trữ thông tin nhân viên.
  - `EmployeeDatabase`: Cơ sở dữ liệu nhân viên.
- Mô tả chi tiết:
  - Lưu trữ thông tin nhân viên.
  - Cập nhật trạng thái nhân viên (đang làm việc hoặc bị xóa).
  - Cung cấp thông tin cho các hệ thống con khác.
**d) Scheduler Subsystem**
- Chức năng chính: Kích hoạt quy trình tính lương theo lịch.
- Thành phần chính:
  - `SystemClock`: Kích hoạt quy trình Run Payroll theo thời gian định trước.
- Mô tả chi tiết:
  - Kích hoạt quy trình tính lương tự động vào thời gian được định trước.

## 2. Describe Subsystem Dependencies
Mối quan hệ phụ thuộc giữa các hệ thống con:
- Timecard Subsystem phụ thuộc vào Employee Management Subsystem để lấy thông tin nhân viên.
- Payroll Processing Subsystem phụ thuộc vào:
  - Employee Management Subsystem để lấy danh sách nhân viên.
  - Timecard Subsystem để lấy thông tin giờ làm việc.
- Scheduler Subsystem không phụ thuộc vào các hệ thống con khác nhưng kích hoạt Payroll Processing Subsystem.
## 3. Checkpoints
- **Phân chia hợp lý**: Mỗi hệ thống con có trách nhiệm riêng biệt, với các thành phần được phân bổ rõ ràng.
- **Phụ thuộc rõ ràng**: Mối quan hệ giữa các hệ thống con được thể hiện rõ qua sơ đồ và các phụ thuộc cụ thể.
- **Tính mở rộng**: Các hệ thống con có thể mở rộng hoặc thay đổi mà không ảnh hưởng đến toàn bộ hệ thống.

