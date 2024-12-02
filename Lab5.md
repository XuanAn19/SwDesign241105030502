# Lab 5: Payroll System Subsystem Design

## 1. Distribute Subsystem Behavior to Subsystem Elements

Hệ thống được chia thành 4 hệ thống con chính:

---

### a) Timecard Subsystem
#### **Chức năng chính:**
- Quản lý giờ làm việc và trạng thái thẻ chấm công.

#### **Thành phần chính:**
1. **`TimecardController`**:
   - Quản lý logic nghiệp vụ liên quan đến thẻ chấm công, bao gồm: 
     - Chấm công khi vào và ra.
     - Tính tổng số giờ làm việc.
2. **`Timecard`**:
   - Thực thể lưu trữ thông tin giờ làm việc, gồm:
     - ID nhân viên, ngày giờ vào/ra, tổng giờ làm việc.
3. **`ProjectManagementDatabase`**:
   - Lưu trữ thông tin danh sách dự án liên quan.

#### **Mô tả chi tiết:**
- Nhân viên sử dụng hệ thống để chấm công vào và ra.
- Thông tin giờ làm việc được tính toán tự động và lưu trữ trong cơ sở dữ liệu.
- Hệ thống hỗ trợ nhân viên gửi yêu cầu nghỉ phép, đồng thời cập nhật trạng thái thẻ chấm công khi cần.

---

### b) Payroll Processing Subsystem
#### **Chức năng chính:**
- Tính toán và thực hiện thanh toán lương.

#### **Thành phần chính:**
1. **`PayrollController`**:
   - Quản lý logic nghiệp vụ tính toán lương dựa trên thông tin giờ làm việc và các yếu tố khác.
2. **`Paycheck`**:
   - Thực thể chứa thông tin phiếu lương:
     - ID phiếu lương, ID nhân viên, số tiền, ngày phát hành.
3. **`BankSystemProxy`**:
   - Kết nối với hệ thống ngân hàng để thực hiện thanh toán.
4. **`PayrollDatabase`**:
   - Lưu trữ thông tin chi tiết về lương, hỗ trợ cho báo cáo và tra cứu.

#### **Mô tả chi tiết:**
- PayrollController lấy dữ liệu từ Timecard Subsystem và Employee Management Subsystem để tính toán lương.
- Lương được gửi qua ngân hàng hoặc in phiếu lương tùy thuộc vào cấu hình.
- Dữ liệu phiếu lương được lưu trữ trong PayrollDatabase để hỗ trợ cho các báo cáo tài chính.

---

### c) Employee Management Subsystem
#### **Chức năng chính:**
- Quản lý thông tin nhân viên và trạng thái làm việc.

#### **Thành phần chính:**
1. **`Employee`**:
   - Thực thể lưu trữ thông tin nhân viên, gồm:
     - ID, tên, thông tin ngân hàng, mức lương cơ bản.
2. **`EmployeeDatabase`**:
   - Lưu trữ thông tin nhân viên, hỗ trợ việc cập nhật và tra cứu.

#### **Mô tả chi tiết:**
- Thông tin nhân viên được cập nhật theo thời gian.
- Cung cấp thông tin nhân viên cho các hệ thống con khác, bao gồm:
  - Timecard Subsystem: để xác định ID nhân viên.
  - Payroll Processing Subsystem: để lấy dữ liệu lương cơ bản.

---

### d) Scheduler Subsystem
#### **Chức năng chính:**
- Kích hoạt quy trình tính lương theo lịch.

#### **Thành phần chính:**
1. **`SystemClock`**:
   - Định thời gian và tự động kích hoạt quy trình "Run Payroll".

#### **Mô tả chi tiết:**
- Scheduler Subsystem hoạt động độc lập, đảm bảo Payroll Processing Subsystem được kích hoạt tự động theo lịch định trước.
- Đảm bảo tính chính xác và nhất quán trong quy trình tính lương.

---

## 2. Describe Subsystem Dependencies

| **Hệ Thống Con**               | **Phụ Thuộc Vào**                                                        |
|---------------------------------|---------------------------------------------------------------------------|
| **Timecard Subsystem**          | Employee Management Subsystem để lấy thông tin nhân viên.                |
| **Payroll Processing Subsystem**| - Employee Management Subsystem để lấy danh sách nhân viên và mức lương. |
|                                 | - Timecard Subsystem để lấy thông tin giờ làm việc của nhân viên.         |
| **Scheduler Subsystem**         | Không phụ thuộc, nhưng kích hoạt Payroll Processing Subsystem.           |

---

## 3. Checkpoints

1. **Phân chia hợp lý**: 
   - Các hệ thống con được thiết kế rõ ràng với chức năng độc lập, đảm bảo tính đơn nhiệm (Single Responsibility).
2. **Phụ thuộc rõ ràng**: 
   - Mối quan hệ giữa các hệ thống con được xác định cụ thể, tránh các phụ thuộc không cần thiết.
3. **Tính mở rộng**:
   - Có thể dễ dàng thêm mới hoặc thay đổi chức năng mà không ảnh hưởng lớn đến toàn bộ hệ thống.

---
