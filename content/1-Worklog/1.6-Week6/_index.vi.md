---
title: "Nhật ký thực tập Tuần 6"
date: 2026-09-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:

- Tìm hiểu về Amazon RDS và vai trò của dịch vụ trong việc cung cấp hệ quản trị cơ sở dữ liệu được quản lý trên AWS.
- Tạo và cấu hình cơ sở dữ liệu Amazon RDS bên trong AWS VPC.
- Tìm hiểu cách kiểm soát quyền truy cập cơ sở dữ liệu thông qua Security Group.
- Kiểm tra khả năng kết nối mạng giữa EC2 Instance và cơ sở dữ liệu RDS.
- Tìm hiểu về Application Load Balancer (ALB) và vai trò của dịch vụ trong việc phân phối lưu lượng truy cập.
- Chuẩn bị môi trường cho việc triển khai máy chủ web và cân bằng tải.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu về Amazon RDS và lợi ích của việc sử dụng dịch vụ cơ sở dữ liệu quan hệ được quản lý.<br>- Tìm hiểu các hệ quản trị cơ sở dữ liệu, cấu hình Instance và tùy chọn lưu trữ.<br>- Xem xét các yêu cầu khi triển khai RDS bên trong private subnet.<br>- Tìm hiểu vai trò của DB Subnet Group trong cấu hình mạng cho cơ sở dữ liệu. | 19/09/2026 | 19/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Tạo DB Subnet Group sử dụng các private subnet phù hợp.<br>- Cấu hình RDS Database Instance với hệ quản trị cơ sở dữ liệu và thông số phù hợp.<br>- Cấu hình Security Group cho cơ sở dữ liệu nhằm hạn chế quyền truy cập từ bên ngoài.<br>- Kiểm tra trạng thái hoạt động của RDS sau khi tạo. | 20/09/2026 | 21/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Kiểm tra cấu hình Security Group của EC2 Instance và RDS Database.<br>- Cấu hình Security Group của RDS để cho phép lưu lượng truy cập cơ sở dữ liệu từ Security Group của EC2 thông qua port cần thiết.<br>- Kiểm tra khả năng kết nối mạng giữa EC2 và RDS.<br>- Kiểm tra Database Endpoint và các thông số kết nối. | 22/09/2026 | 23/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Tìm hiểu về Application Load Balancer và vai trò của dịch vụ trong việc phân phối lưu lượng truy cập.<br>- Tìm hiểu về Listener, Target Group và Health Check.<br>- Xem xét các yêu cầu về mạng và Security Group khi kết nối ALB với EC2.<br>- Tổng hợp kết quả kiểm tra kết nối RDS và chuẩn bị cho việc triển khai máy chủ web, cân bằng tải trong tuần tiếp theo. | 24/09/2026 | 25/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Kết quả Tuần 6:

- Nắm được các kiến thức cơ bản về Amazon RDS và vai trò của dịch vụ trong việc cung cấp cơ sở dữ liệu được quản lý.
- Biết cách cấu hình DB Subnet Group sử dụng các private subnet.
- Đã tạo và cấu hình RDS Database Instance bên trong AWS VPC.
- Cấu hình Security Group để kiểm soát quyền truy cập cơ sở dữ liệu và giới hạn kết nối đối với các tài nguyên được phép.
- Kiểm tra thành công khả năng kết nối mạng giữa EC2 Instance và RDS Database thông qua cổng cơ sở dữ liệu cần thiết.
- Hiểu cách sử dụng Database Endpoint và các thông số kết nối khi truy cập RDS.
- Tìm hiểu các kiến thức cơ bản về Application Load Balancer, Listener, Target Group và Health Check.
- Chuẩn bị môi trường cơ sở dữ liệu và mạng cho giai đoạn tiếp theo: triển khai máy chủ web và cấu hình cân bằng tải.