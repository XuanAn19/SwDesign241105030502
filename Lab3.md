![Diagram](https://planttext.com/api/plantuml/png/n5DBRi8m4Dtx52Cs1QdX0CX22EWYYqfLMNKv94DmSUp8dWXGsvDrqIFr2dM8Gp-4TRsmRCzxC-_Do9_l7pFFwBWkDJmu-qmPtwF1Waeol4J6DNfQrMj_z4oby3jbAdHOWWj8D8KcU14GrXopNU5iRVA5rTP9wJiILCuUZjCfF97MTY_UXBY1XJNih8Q5Hkz5rknT_HZIv43AhBq4Tbi6e3p9YzZXg4sN6YQtmOo4wawGNlgPdxDiYBDj13GsXrLxJfSmwOIaor54rrMEtDLSCNBj-mctu4_HyBPYfqmHzPqxs40Fnz-6BniEVUtx9-btXXKh-ZEam9MIcb2G5aDjzf_lWVv86bbPuxUgyk9on4bkzoQPzazh0eEJM_A09ezUF8GT1wAN8L_7u-jzxUVO9FcsTHtIsXCpCdduBU8B003__mC0)
   - Giari thích thành phần biểu đồ trên
          + Mục đích: Quản lý dữ liệu và trạng thái của các dự án.
          + Thành phần:
             + ProjectController: Lớp điều khiển, thực thi phương thức manageProject() để quản lý dự án.
             + IProjectManagementDB: Interface kết nối đến cơ sở dữ liệu dự án, cung cấp các phương thức như:
                  + fetchProjectData(): Lấy thông tin dự án.
                  + updateProjectStatus(): Cập nhật trạng thái dự án.
             + ProjectManagementDatabase: Lớp thực thi (proxy) để thao tác với cơ sở dữ liệu thực.
             + ProjectID và Status: Các thực thể biểu diễn thông tin dự án và trạng thái của dự án.
          + Quy trình:
             + ProjectController gọi IProjectManagementDB để lấy hoặc cập nhật dữ liệu dự án.
             + Interface này tương tác với ProjectManagementDatabase để thực hiện công việc.
# 2. Analysis class to design element map
     Dưới đây là ánh xạ các lớp phân tích từ sơ đồ trên sang các phần tử thiết kế của hệ thống:
  ![image](https://github.com/user-attachments/assets/7244fa5f-2876-4a63-a838-1cfd56d520f6)
#3. Analysis class to design element map
### Mappings
- **LoginForm** -> `LoginForm`
- **MaintainTimecardForm** -> `MainEmployeeForm`
- **TimecardController** -> `TimecardController`
- **PayrollController** -> `PayrollController`
- **PayCheck** -> `PayCheck`
- **BankService** -> `BankService`
- **SystemClockInterface** -> `SystemClockInterface`
- **PayrollController** -> `PayrollControllerImpl`
- **Employee** -> `EmployeeEntity`
- **Timecard** -> `TimecardEntity`
- **Payroll** -> `PayrollProcessor`
- **BankTransaction** -> `BankTransactionProcessor`
- **PaymentUI** -> `PaymentUIComponent`
- **PrintService** -> `PrintServiceProcessor`
#4. Design element to owning package map

| Design Element         | "Owning" Package                          |
|-------------------------|-------------------------------------------|
| LoginForm              | Middleware::Security::GUI Framework       |
| MainEmployeeForm       | Applications::Employee Activities         |
| TimecardForm           | Applications::Employee Activities         |
| MainApplicationForm    | Middleware::Security::GUI Framework       |
| TimecardController     | Applications::Payroll                     |
