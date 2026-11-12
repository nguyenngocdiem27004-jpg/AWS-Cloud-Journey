---
title: "Nhật ký thực tập Tuần 4"
date: 2026-09-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

- Tìm hiểu về Amazon EC2 và vai trò của dịch vụ trong việc triển khai máy chủ ảo cho đề tài bảo mật hạ tầng trên AWS.
- Tìm hiểu các loại EC2 Instance, Amazon Machine Image (AMI) và lưu trữ Amazon EBS.
- Khởi tạo và cấu hình EC2 Instance bên trong VPC đã tạo ở Tuần 3.
- Cấu hình Security Group để kiểm soát lưu lượng mạng vào và ra, bảo vệ EC2 Instance.
- Tìm hiểu cách truy cập và quản lý EC2 Instance thông qua AWS Systems Manager Session Manager.
- Tìm hiểu các thao tác quản lý EC2 cơ bản nhằm kiểm soát chi phí sử dụng AWS.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu về Amazon EC2, các loại Instance, AMI và lưu trữ EBS.<br>- Tìm hiểu cách lựa chọn loại Instance và hệ điều hành phù hợp với đề tài.<br>- Tìm hiểu các tùy chọn cấu hình cơ bản khi khởi tạo EC2 Instance. | 05/09/2026 | 05/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Khởi tạo EC2 Instance trong VPC đã tạo ở Tuần 3.<br>- Lựa chọn AMI, loại Instance, subnet và dung lượng lưu trữ.<br>- Cấu hình các thiết lập mạng và gán Security Group phù hợp cho Instance.<br>- Kiểm tra trạng thái hoạt động và địa chỉ IP được cấp cho Instance. | 06/09/2026 | 07/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Tạo và cấu hình Security Group cho EC2 Instance.<br>- Kiểm tra các quy tắc Inbound và chỉ cho phép những lưu lượng cần thiết.<br>- Cấu hình quyền truy cập HTTP qua TCP port 80 khi cần thiết cho máy chủ web.<br>- Kiểm tra các quy tắc Outbound và áp dụng nguyên tắc đặc quyền tối thiểu.<br>- Tìm hiểu cách Security Group bảo vệ các tài nguyên trên AWS. | 08/09/2026 | 08/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Tìm hiểu cách cấu hình IAM Role cho EC2 để sử dụng AWS Systems Manager.<br>- Kết nối đến EC2 Instance thông qua Systems Manager Session Manager.<br>- Kiểm tra hệ điều hành, cấu hình mạng và các tài nguyên hệ thống cơ bản.<br>- Kiểm tra trạng thái Instance và cấu hình truy cập.<br>- Tìm hiểu cách dừng và khởi động lại EC2 Instance để quản lý chi phí AWS. | 09/09/2026 | 09/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Kết quả Tuần 4:

- Nắm được các kiến thức cơ bản về Amazon EC2, các loại Instance, AMI và lưu trữ EBS.
- Biết cách lựa chọn cấu hình EC2 phù hợp với đề tài bảo mật hạ tầng trên AWS.
- Đã khởi tạo EC2 Instance bên trong VPC và biết cách kiểm tra trạng thái hoạt động cũng như địa chỉ IP.
- Đã tạo và cấu hình Security Group để kiểm soát lưu lượng mạng vào và ra.
- Hiểu cách hạn chế quyền truy cập mạng bằng cách chỉ cho phép những lưu lượng cần thiết thông qua các quy tắc Security Group.
- Tìm hiểu cách cấu hình IAM Role và sử dụng AWS Systems Manager Session Manager để truy cập EC2 Instance mà không cần phụ thuộc vào kết nối SSH trực tiếp.
- Thực hiện kiểm tra cơ bản về hệ điều hành và cấu hình mạng trên EC2 Instance.
- Nắm được các thao tác quản lý EC2 cơ bản, bao gồm dừng và khởi động Instance nhằm kiểm soát chi phí AWS.
- Hoàn thành môi trường máy chủ, tạo nền tảng cho các bước tiếp theo như triển khai máy chủ web và bổ sung các biện pháp bảo mật hạ tầng.