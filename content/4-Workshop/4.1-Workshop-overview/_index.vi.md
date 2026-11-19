---
title: "Giới thiệu"
date: 2026-10-29
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

### 1. Giới thiệu về bảo mật hạ tầng AWS

Bảo mật hạ tầng AWS bao gồm việc bảo vệ tài nguyên đám mây, kiểm soát quyền truy cập mạng, quản lý quyền hạn và giám sát các hoạt động trong môi trường AWS.

Các khía cạnh bảo mật chính được đề cập trong dự án bao gồm:

- **Bảo mật mạng:** Amazon Virtual Private Cloud (VPC), Subnet, Route Table, Internet Gateway, Security Group và VPC Endpoint giúp tổ chức tài nguyên mạng và kiểm soát hoạt động giao tiếp giữa các thành phần.

- **Quản lý danh tính và quyền truy cập:** AWS Identity and Access Management (IAM) cung cấp các cơ chế quản lý quyền. IAM Role và Policy được sử dụng để cấp những quyền cần thiết theo nguyên tắc đặc quyền tối thiểu.

- **Quản trị EC2 an toàn:** AWS Systems Manager (SSM) Session Manager cho phép truy cập và quản lý EC2 instance mà không cần địa chỉ IP công khai hoặc kết nối SSH trực tiếp.

- **Bảo vệ ứng dụng web:** Application Load Balancer (ALB) phân phối lưu lượng truy cập đến máy chủ ứng dụng, trong khi AWS Web Application Firewall (WAF) kiểm tra và lọc các yêu cầu web dựa trên những quy tắc đã cấu hình.

- **Giám sát và kiểm toán:** Amazon CloudWatch, AWS CloudTrail và AWS Config hỗ trợ giám sát hoạt động của tài nguyên, ghi nhận sự kiện trong tài khoản và theo dõi cấu hình tài nguyên.

### 2. Tổng quan Workshop

Workshop này giới thiệu hạ tầng AWS và các cấu hình bảo mật được triển khai trong dự án **"Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS."**

Môi trường được triển khai tại khu vực Asia Pacific (Singapore) (ap-southeast-1) và bao gồm các thành phần chính sau:

![Sơ đồ kiến trúc hạ tầng AWS](/images/4-Workshop/4.1-Introduction/diagram.png)

- **Hạ tầng mạng AWS:** Amazon VPC cung cấp môi trường mạng được cô lập với các phân đoạn mạng công khai và riêng tư, bảng định tuyến và Internet Gateway. VPC Endpoint cung cấp kết nối riêng tư đến các dịch vụ AWS được hỗ trợ mà không cần sử dụng NAT Gateway.

- **Môi trường máy chủ:** Một EC2 instance có tên KLTN-Web-Server được triển khai trong Private Subnet. Instance chạy Nginx làm máy chủ web và không được gán địa chỉ IPv4 công khai.

- **Kiểm soát truy cập và quản trị an toàn:** IAM Role cung cấp các quyền cần thiết để EC2 giao tiếp với AWS Systems Manager. Session Manager được sử dụng để truy cập instance mà không cần mở quyền truy cập SSH từ bên ngoài.

- **Truy cập và bảo vệ ứng dụng:** Application Load Balancer (ALB) cung cấp điểm truy cập web đến máy chủ EC2. AWS WAF được liên kết với ALB để kiểm tra các yêu cầu truy cập và hỗ trợ ngăn chặn lưu lượng web có dấu hiệu độc hại.

- **Giám sát, ghi nhật ký và cảnh báo:** Amazon CloudWatch được sử dụng để xem xét các chỉ số và thông tin giám sát tài nguyên. AWS CloudTrail ghi nhận hoạt động trong tài khoản, trong khi AWS Config theo dõi cấu hình tài nguyên và đánh giá chúng dựa trên các quy tắc đã thiết lập. Amazon EventBridge và Amazon SNS hỗ trợ gửi thông báo đối với một số sự kiện liên quan đến bảo mật.

Thông qua workshop này, bạn sẽ tìm hiểu kiến trúc AWS đã triển khai, cách các dịch vụ phối hợp với nhau, đồng thời xem xét các cấu hình bảo mật và hoạt động kiểm tra thực tế được thực hiện trong dự án.

### 3. Mục tiêu Workshop

Sau khi hoàn thành workshop, bạn có thể:

- Hiểu các thành phần chính của hạ tầng mạng AWS.

- Tổ chức tài nguyên đám mây bằng Amazon VPC, Subnet và Route Table.

- Triển khai máy chủ web EC2 trong Private Subnet.

- Áp dụng IAM Role và Security Group để kiểm soát quyền truy cập.

- Sử dụng Systems Manager Session Manager để quản trị EC2 an toàn.

- Cấu hình Application Load Balancer và AWS WAF để bảo vệ lưu lượng truy cập web.

- Theo dõi hoạt động và cấu hình hạ tầng bằng CloudWatch, CloudTrail và AWS Config.

- Hiểu cách EventBridge và SNS hỗ trợ gửi cảnh báo về các sự kiện bảo mật.

- Thực hiện kiểm tra bảo mật cơ bản và đánh giá mức sử dụng tài nguyên hạ tầng.

==================================================
