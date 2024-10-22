#Lab1
#1.  Phân tích kiến trúc
  Đề xuất kiến trúc: Kiến trúc phân lớp kết hợp với Microservices cho "Payroll System"
  Giải thích: 
  - Có thể kết hợp với hệ thống cũ.
  - Phân lớp có thể quản lý và bảo trì từng thành phần không ảnh hưởng đến toàn bộ kiến trúc.
  - Kiến trúc Microservices có thể hỗ trợ mở rộng từng chức năng riêng biệt của hệ thống
  Ý nghĩa từng phần:
  - UI Layer: Nơi phát triển giao diện để người dùng tương tác với hệ thống
  - Application Service Layer: Lớp này chứa logic của hệ thống: tính toán lương, ... và API để giao tiếp giữa các dịch vụ khác.
  - Data Access Layer: Lớp này chịu trách nhiệm giao tiếp với cơ sở dữ liệu 
  - Data Layer : Lớp lưu trữ database
  Package: 
![](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTnTcQUGb5-SIfNIMP9Jgf2G69bKNvEZa9mPN59QYuNLq5YSdPYUgg2KgYdWazYPMgHaa8rLosIk6D1GKvcSc99PdwUGd1gKLbcSYfsXIw99OaAZid9gSN5U1GWoqJ3x8nLqDEpKuZ6QLKi5nuvY5uCsu5wCCMGr48LSJcavgM00We0003__mC0)
#2. Cơ chế phân tích
  ##Cơ chế Xác thực và Phân quyền người dùng
    Lý do: Để đảm bảo rằng nhân viên chỉ có thể truy cập và chỉnh sửa thông tin của chính họ và không thể can thiệp vào thông tin của người khác.
  ##Cơ chế Ghi lại và Lưu trữ Ghi chép
    Lý do: Điều này giúp đảm bảo tính minh bạch và trách nhiệm, đồng thời cung cấp dữ liệu cho các báo cáo sau này.
  ##Cơ chế Tính toán Lương
    Lý do: Để đảm bảo rằng nhân viên được trả lương chính xác và kịp thời theo các quy tắc đã định.
  ##Cơ chế Quản lý Dữ liệu Nhân viên
    Lý do: Để duy trì dữ liệu nhân viên luôn cập nhật và chính xác.
  ##Cơ chế Tạo Báo cáo
    Lý do: Để hỗ trợ việc ra quyết định và quản lý thông tin trong doanh nghiệp.
  ##Cơ chế Kết nối với Cơ sở Dữ liệu DB2
    Lý do: Để tận dụng dữ liệu có sẵn mà không cần phải di chuyển hay thay thế hệ thống hiện tại.
  ##Cơ chế Gửi Thanh toán
    Lý do: Để đảm bảo thanh toán được thực hiện đúng cách và đúng hạn, cũng như mang lại sự tiện lợi cho nhân viên.
  ##Cơ chế Bảo mật Dữ liệu
    Lý do: Để bảo vệ thông tin cá nhân của nhân viên và tuân thủ các quy định về bảo vệ dữ liệu.
  ##Cơ chế Quản lý Thông báo
    Lý do: Để giữ cho nhân viên luôn thông báo về các thông tin quan trọng liên quan đến lương và công việc của họ.
