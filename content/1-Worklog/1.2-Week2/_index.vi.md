
---
title: "Nhật ký thực tập Tuần 2"
date: 2026-08-17
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Tìm hiểu các yêu cầu trong việc thiết kế và triển khai hệ thống hạ tầng AWS có bảo mật.
- Xác định kiến trúc AWS phù hợp để triển khai và bảo vệ các tài nguyên trên nền tảng đám mây.
- Lập kế hoạch cấu trúc mạng sử dụng Amazon VPC, Public Subnet và Private Subnet.
- Lập kế hoạch địa chỉ IP và phân chia subnet nhằm tổ chức tài nguyên AWS, tránh trùng lặp dải mạng.
- Xác định các thành phần bảo mật cần thiết cho đề tài, bao gồm Security Groups, Network ACLs, IAM và định tuyến mạng.
- Chuẩn bị sơ đồ kiến trúc ban đầu và kế hoạch triển khai cho các tuần tiếp theo.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Phân tích yêu cầu của đề tài bảo mật hạ tầng trên AWS.<br>- Xác định các thành phần chính của hệ thống, bao gồm VPC, Subnet, EC2 Instance, cơ sở dữ liệu và các dịch vụ bảo mật.<br>- Xác định yêu cầu truy cập mạng và bảo vệ tài nguyên AWS.<br>- Phác thảo kiến trúc ban đầu cho hệ thống AWS có bảo mật. | 17/08/2026 | 17/08/2026 | [Tài liệu AWS](https://docs.aws.amazon.com/) |
| 3 | - Tìm hiểu các thành phần mạng trong Amazon VPC.<br>- Phân tích vai trò của Public Subnet, Private Subnet, Route Table, Internet Gateway và NAT Gateway.<br>- Tìm hiểu cách phân đoạn mạng giúp cô lập và bảo vệ tài nguyên đám mây.<br>- Xác định các luồng định tuyến phù hợp cho tài nguyên công khai và tài nguyên nội bộ. | 18/08/2026 | 19/08/2026 | [Tài liệu Amazon VPC](https://docs.aws.amazon.com/vpc/) |
| 4 | - Lập kế hoạch địa chỉ IP cho hệ thống mạng AWS.<br>- Xác định dải CIDR cho VPC và các subnet.<br>- Lên kế hoạch bố trí EC2 Instance và tài nguyên cơ sở dữ liệu trong các subnet phù hợp.<br>- Tìm hiểu Security Groups và Network ACLs để xác định yêu cầu kiểm soát truy cập mạng. | 20/08/2026 | 20/08/2026 | [Tài liệu Amazon VPC](https://docs.aws.amazon.com/vpc/) |
| 5 | - Hoàn thiện sơ đồ kiến trúc hạ tầng AWS ban đầu.<br>- Xác định các dịch vụ bảo mật cần triển khai, bao gồm IAM, AWS WAF, CloudTrail, CloudWatch và AWS Config.<br>- Chuẩn bị kế hoạch cấu hình mạng và các yêu cầu bảo mật cho giai đoạn triển khai.<br>- Rà soát kiến trúc trước khi tạo các tài nguyên AWS trong những tuần tiếp theo. | 21/08/2026 | 21/08/2026 | [Tài liệu bảo mật AWS](https://docs.aws.amazon.com/security/) |

### Kết quả đạt được trong tuần 2:

- Xác định được mục tiêu và các yêu cầu của đề tài bảo mật hạ tầng trên AWS.
- Xây dựng được bản thiết kế kiến trúc ban đầu cho việc triển khai và bảo vệ tài nguyên trên AWS.
- Nắm được vai trò của các thành phần mạng trong AWS:
  - **Amazon VPC:** Cung cấp môi trường mạng ảo riêng biệt cho các tài nguyên AWS.
  - **Public Subnet:** Chứa các tài nguyên cần có đường định tuyến ra Internet thông qua Internet Gateway.
  - **Private Subnet:** Chứa các tài nguyên nội bộ không nên được truy cập trực tiếp từ Internet.
  - **Route Table:** Kiểm soát đường đi của lưu lượng mạng trong VPC.
  - **Internet Gateway:** Cho phép VPC giao tiếp với Internet đối với các tài nguyên đáp ứng điều kiện định tuyến.
  - **NAT Gateway:** Cho phép tài nguyên trong Private Subnet khởi tạo kết nối ra Internet mà không cần cho phép các kết nối không được yêu cầu từ bên ngoài đi vào.
- Xây dựng kế hoạch phân chia địa chỉ IP ban đầu cho VPC và các subnet.
- Hiểu được tầm quan trọng của phân đoạn mạng và kiểm soát quyền truy cập vào tài nguyên AWS.
- Xác định vai trò của Security Groups và Network ACLs trong việc lọc lưu lượng mạng.
- Tìm hiểu các dịch vụ bảo mật và giám sát cần thiết cho đề tài, bao gồm IAM, AWS WAF, CloudTrail, CloudWatch và AWS Config.
- Chuẩn bị sơ đồ kiến trúc và các yêu cầu cấu hình ban đầu để triển khai hệ thống hạ tầng AWS có bảo mật trong những tuần tiếp theo.
