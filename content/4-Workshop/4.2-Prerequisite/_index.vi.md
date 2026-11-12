---
title: "Các yêu cầu chuẩn bị"
date: 2026-10-29
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

#### Tổng quan về môi trường triển khai

Để triển khai hệ thống bảo mật hạ tầng trên AWS, cần chuẩn bị tài khoản AWS, máy tính phục vụ quản trị, kết nối Internet và thiết kế mạng cơ bản.

Dự án sử dụng Amazon Web Services (AWS) để xây dựng và quản lý hạ tầng đám mây. Môi trường triển khai được đặt tại khu vực Singapore (`ap-southeast-1`), nơi các tài nguyên mạng, máy chủ, cơ sở dữ liệu và bảo mật được cấu hình.

Hạ tầng bao gồm Amazon VPC với các Public Subnet và Private Subnet, Internet Gateway, NAT Gateway, Route Table, máy chủ web EC2, cơ sở dữ liệu MySQL trên RDS và Application Load Balancer. Các dịch vụ AWS khác được sử dụng để quản lý quyền truy cập, bảo vệ lưu lượng web và kiểm tra hoạt động của hạ tầng.

#### Các thành phần cần thiết

- **Tài khoản Amazon Web Services (AWS):** Dùng để truy cập AWS Management Console và tạo hoặc quản lý các tài nguyên trên đám mây.

- **AWS Management Console:** Được sử dụng để cấu hình và quản lý các dịch vụ như Amazon VPC, EC2, RDS, IAM, Elastic Load Balancing và AWS WAF.

- **IAM User và quyền truy cập:** Được sử dụng để truy cập các dịch vụ AWS và thực hiện những thao tác cần thiết cho dự án. Tài khoản cần có quyền phù hợp với các tài nguyên được cấu hình.

- **Amazon VPC:** Được sử dụng để xây dựng môi trường mạng đám mây, bao gồm Public Subnet, Private Subnet, Internet Gateway, NAT Gateway và Route Table.

- **Amazon EC2:** Được sử dụng để triển khai máy chủ web và cung cấp môi trường tính toán phục vụ kiểm tra truy cập mạng.

- **Amazon RDS:** Được sử dụng để triển khai và quản lý cơ sở dữ liệu MySQL trong môi trường AWS.

- **Application Load Balancer (ALB) và AWS WAF:** Được sử dụng để cung cấp khả năng truy cập đến máy chủ web và áp dụng các quy tắc bảo vệ lưu lượng truy cập web.

- **Máy tính quản trị:** Được sử dụng để truy cập AWS Management Console, cấu hình tài nguyên, kết nối đến EC2 và thực hiện kiểm tra thông qua trình duyệt web hoặc cửa sổ dòng lệnh.

#### Các yêu cầu trước khi triển khai

Trước khi bắt đầu workshop, cần đảm bảo các yêu cầu sau:

1. Đã tạo tài khoản AWS và có thể truy cập AWS Management Console.
2. Có IAM User hoặc danh tính được cấp quyền phù hợp để cấu hình các dịch vụ AWS cần thiết.
3. Có máy tính với trình duyệt web hiện đại và kết nối Internet ổn định.
4. Đã chọn AWS Region là Asia Pacific (Singapore) (`ap-southeast-1`).
5. Đã chuẩn bị kế hoạch địa chỉ IP cho VPC và các Public Subnet, Private Subnet. Các dải địa chỉ CIDR được lựa chọn không được trùng lặp.
6. Nên có kiến thức cơ bản về điện toán đám mây, địa chỉ IP, chia subnet và kiểm soát truy cập mạng.
7. Cần kiểm tra giá dịch vụ AWS và mức sử dụng tài nguyên trước khi triển khai để tránh phát sinh chi phí không cần thiết.

#### Kết quả mong đợi

Sau khi hoàn thành bước chuẩn bị, chúng ta sẽ có tài khoản AWS có thể truy cập, khu vực triển khai phù hợp, quyền truy cập cần thiết và kế hoạch địa chỉ IP ban đầu.

Những bước chuẩn bị này tạo nền tảng cho việc xây dựng mạng VPC, triển khai EC2 và RDS, cấu hình kiểm soát truy cập, bảo vệ lưu lượng web và đánh giá bảo mật hạ tầng trong các phần tiếp theo.