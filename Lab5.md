# Lab 5: Payroll System Subsystem Design

## 1. Distribute Subsystem Behavior to Subsystem Elements

Hệ thống được chia thành 2 hệ thống con chính dựa trên 2 ca sử dụng từ Lab 4:

---

### a) Timecard Subsystem
#### **Chức năng chính:**
- Quản lý thông tin giờ làm việc và trạng thái thẻ chấm công.

#### **Thành phần chính:**
1. **`TimecardController`**:
   - Xử lý logic nghiệp vụ liên quan đến:
     - Chấm công khi vào/ra.
     - Tính tổng số giờ làm việc.
     - Cập nhật trạng thái thẻ chấm công.
2. **`Timecard`**:
   - Thực thể lưu trữ thông tin giờ làm việc, gồm:
     - ID nhân viên.
     - Ngày giờ vào/ra.
     - Tổng số giờ làm việc.
     - Yêu cầu nghỉ phép và trạng thái.
3. **`TimecardDatabase`**:
   - Cơ sở dữ liệu lưu trữ thông tin thẻ chấm công.

#### **Mô tả chi tiết:**
- **Khi bắt đầu ca làm việc:** Nhân viên chấm công, hệ thống ghi nhận thời gian vào.
- **Khi kết thúc ca làm việc:** Nhân viên chấm công ra, hệ thống tính toán tổng giờ làm việc và lưu vào cơ sở dữ liệu.
- **Yêu cầu nghỉ phép:** Nhân viên gửi yêu cầu, trạng thái nghỉ phép được quản lý bởi người quản trị hệ thống.

---

### b) Payroll Processing Subsystem
#### **Chức năng chính:**
- Tính toán và thực hiện thanh toán lương.

#### **Thành phần chính:**
1. **`PayrollController`**:
   - Xử lý nghiệp vụ liên quan đến:
     - Tính toán lương dựa trên giờ làm việc và các yếu tố khác (OT, nghỉ phép, v.v.).
     - Tạo phiếu lương (Paycheck).
     - Giao tiếp với hệ thống ngân hàng để thực hiện thanh toán.
2. **`Paycheck`**:
   - Thực thể lưu trữ thông tin phiếu lương:
     - ID phiếu lương.
     - ID nhân viên.
     - Số tiền.
     - Ngày phát hành.
3. **`BankSystemProxy`**:
   - Kết nối với hệ thống ngân hàng để gửi tiền lương vào tài khoản nhân viên.
4. **`PayrollDatabase`**:
   - Cơ sở dữ liệu lưu trữ thông tin chi tiết về phiếu lương.

#### **Mô tả chi tiết:**
- **Khi kích hoạt quy trình trả lương:** PayrollController lấy thông tin giờ làm việc từ Timecard Subsystem và thông tin nhân viên từ Employee Database.
- Hệ thống tính toán lương và tạo phiếu lương cho từng nhân viên.
- Tiền lương được gửi qua hệ thống ngân hàng, thông tin phiếu lương được lưu trữ trong PayrollDatabase.

---

## 2. Describe Subsystem Dependencies

| **Hệ Thống Con**               | **Phụ Thuộc Vào**                                                        |
|---------------------------------|---------------------------------------------------------------------------|
| **Timecard Subsystem**          | Employee Management Database để lấy thông tin nhân viên.                 |
| **Payroll Processing Subsystem**| - Timecard Subsystem để lấy thông tin giờ làm việc.                       |
|                                 | - Employee Management Database để lấy thông tin nhân viên và mức lương.  |

---

## 3. Checkpoints

1. **Phân chia hợp lý**: 
   - Hệ thống được chia thành 2 subsystem chính dựa trên ca sử dụng.
   - Các chức năng được phân bổ rõ ràng và logic.
2. **Phụ thuộc rõ ràng**: 
   - Timecard Subsystem và Payroll Processing Subsystem có mối quan hệ phụ thuộc rõ ràng với các cơ sở dữ liệu.
3. **Tính mở rộng**:
   - Hệ thống con có thể dễ dàng mở rộng để bổ sung các chức năng mới (như quản lý OT hoặc tích hợp hệ thống báo cáo tài chính).

---
