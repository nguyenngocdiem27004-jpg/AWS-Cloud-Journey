---
title: "IAM và quản lý truy cập an toàn"
date: 2026-10-30
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

#### Tổng quan

Identity and Access Management (IAM) là thành phần quan trọng trong bảo mật hạ tầng AWS. Dịch vụ cho phép quản trị viên xác định danh tính nào được phép truy cập tài nguyên AWS và những thao tác nào được thực hiện.

Trong dự án này, IAM Role và AWS Systems Manager Session Manager được sử dụng để cung cấp phương thức quản trị an toàn cho EC2 nằm trong mạng riêng.

Mục tiêu chính là quản lý quyền truy cập mà không cần công khai địa chỉ IP của Instance hoặc mở cổng SSH inbound.

### 1. IAM Role dành cho EC2

EC2 Instance KLTN-Web-Server sử dụng IAM Role KLTN-EC2-SSM-Role.

Role này cho phép Instance giao tiếp với AWS Systems Manager và hỗ trợ chức năng Session Manager.

Role sử dụng AWS-managed policy:

- AmazonSSMManagedInstanceCore

Policy này cung cấp các quyền cần thiết để EC2 đăng ký và giao tiếp với Systems Manager.

![IAM Role được gắn policy AmazonSSMManagedInstanceCore](/images/4-Workshop/4.5-IAM%20and%20Secure%20Access%20Management/iam-role-policy.png)

### 2. Kiểm tra IAM Role

Các bước kiểm tra:

1. Truy cập AWS Management Console.
2. Mở dịch vụ **IAM**.
3. Chọn **Roles**.
4. Tìm KLTN-EC2-SSM-Role.
5. Kiểm tra các Policy được gắn.
6. Xác nhận có AmazonSSMManagedInstanceCore.
7. Kiểm tra Role được liên kết với EC2 Instance.

IAM Role cho phép Instance sử dụng quyền tạm thời mà không cần lưu trữ Access Key dài hạn trên máy chủ.

### 3. Truy cập an toàn bằng Session Manager

AWS Systems Manager Session Manager cung cấp khả năng truy cập EC2 thông qua trình duyệt hoặc giao diện dòng lệnh.

Khác với phương thức SSH truyền thống, Session Manager không yêu cầu mở quy tắc SSH inbound hoặc gán địa chỉ IP công khai.

Dự án sử dụng các thành phần:

- EC2 Instance: KLTN-Web-Server

- IAM Role: KLTN-EC2-SSM-Role

- Quyền Systems Manager: AmazonSSMManagedInstanceCore

- VPC Endpoint: KLTN-SSM-Endpoint và KLTN-SSMMessages-Endpoint

VPC Endpoint cho phép Instance trong mạng riêng giao tiếp với Systems Manager thông qua kết nối mạng riêng tư.

### 4. Thiết lập kết nối Session Manager

Để truy cập EC2:

1. Mở **EC2 Console**.
2. Chọn KLTN-Web-Server.
3. Nhấn **Connect**.
4. Mở tab **Session Manager**.
5. Nhấn **Connect** để bắt đầu phiên làm việc.

Sau khi kết nối thành công, quản trị viên có thể sử dụng terminal để thực hiện các thao tác quản trị.

Phiên làm việc có thể được sử dụng để kiểm tra dịch vụ hệ thống, cấu hình mạng và quản lý máy chủ web Nginx.

![Phiên terminal Session Manager kết nối thành công](/images/4-Workshop/4.5-IAM%20and%20Secure%20Access%20Management/ssm-session.png)

### 5. Lợi ích bảo mật

Cấu hình IAM và Session Manager mang lại các lợi ích:

- **Không cần mở SSH inbound:** EC2 không cần mở cổng SSH để quản trị.

- **Không cần Public IP:** EC2 riêng tư có thể được quản lý mà không cần phơi bày trực tiếp ra Internet.

- **Quyền truy cập tạm thời:** IAM Role cung cấp thông tin xác thực tạm thời thay vì lưu Access Key dài hạn trên Instance.

- **Quản lý truy cập tập trung:** IAM và Systems Manager hỗ trợ quản lý và kiểm soát quyền quản trị.

- **Kết nối dịch vụ riêng tư:** VPC Endpoint cho phép giao tiếp với các dịch vụ Systems Manager được hỗ trợ thông qua VPC.

#### Kết quả kiểm tra

Quá trình triển khai đã xác minh:

- IAM Role KLTN-EC2-SSM-Role được gán cho EC2.

- Policy AmazonSSMManagedInstanceCore được gắn vào Role.

- SSM Agent đang hoạt động trên Instance.

- Session Manager thiết lập được kết nối đến EC2 trong mạng riêng.

- Instance có thể được quản trị mà không cần Public IPv4 hoặc SSH inbound.

### 6. Kết luận

Phần này trình bày cách sử dụng IAM Role và AWS Systems Manager Session Manager để quản trị EC2 riêng tư một cách an toàn.

Việc kết hợp IAM, Session Manager và VPC Endpoint giúp giảm nhu cầu truy cập mạng trực tiếp và tránh phơi bày các dịch vụ quản trị ra Internet công khai.

==================================================
