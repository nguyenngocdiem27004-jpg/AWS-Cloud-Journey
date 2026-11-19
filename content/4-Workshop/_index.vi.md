---
title: "Workshop"
date: 2026-10-27
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

# Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS

### 1. Tổng quan

Trong workshop này, chúng ta sẽ tìm hiểu quá trình thiết kế và triển khai hạ tầng điện toán đám mây an toàn bằng Amazon Web Services (AWS).

Dự án tập trung xây dựng hạ tầng mạng AWS dựa trên Amazon VPC, hai Private Subnet, các bảng định tuyến, Internet Gateway và VPC Endpoint. Một EC2 instance chạy máy chủ web Nginx trong mạng riêng, trong khi Application Load Balancer cung cấp điểm truy cập web.

Để tăng cường bảo mật hạ tầng, dự án áp dụng các dịch vụ AWS Identity and Access Management (IAM), Security Groups, Application Load Balancer (ALB) và AWS Web Application Firewall (WAF). Bên cạnh đó, Amazon CloudWatch, AWS CloudTrail và AWS Config được sử dụng để kiểm tra hiệu suất tài nguyên, hoạt động tài khoản và cấu hình các tài nguyên AWS.

Thông qua workshop này, chúng ta sẽ tìm hiểu kiến trúc mạng AWS đã triển khai, phương thức quản trị EC2 an toàn, bảo vệ lưu lượng web, giám sát, ghi nhật ký, kiểm thử bảo mật và rà soát mức sử dụng tài nguyên.

### 2. Mục tiêu

- **Kiến trúc đám mây AWS:** Tìm hiểu và thiết kế hạ tầng đám mây sử dụng Amazon VPC và các thành phần mạng liên quan.

- **Hạ tầng mạng AWS:** Rà soát VPC, các Private Subnet, Route Table, Internet Gateway và VPC Endpoint dành cho Systems Manager.

- **Triển khai Amazon EC2:** Triển khai máy chủ web và cấu hình truy cập an toàn bằng IAM role và Systems Manager Session Manager.

- **Bảo mật hạ tầng:** Áp dụng quyền IAM, Security Group, Application Load Balancer và AWS WAF.

- **Giám sát và ghi nhật ký:** Tìm hiểu Amazon CloudWatch, AWS CloudTrail và AWS Config.

- **Kiểm tra bảo mật:** Xác minh kết nối mạng, kiểm tra các quy tắc kiểm soát truy cập và rà soát cấu hình bảo mật của tài nguyên AWS.

### 3. Nội dung

1. [Giới thiệu](4.1-Workshop-overview/)
2. [Các yêu cầu chuẩn bị](4.2-Prerequisite/)
3. [Thiết kế và triển khai hạ tầng mạng AWS](4.3-AWS%20Network%20Infrastructure/)
4. [Triển khai Amazon EC2 và cấu hình Security Group](4.4-EC2%20Security%20Group/)
5. [Cân bằng tải và bảo vệ ứng dụng web](4.6-Load%20Balancing%20and%20Web%20Application%20Protection/)
6. [Giám sát và ghi nhật ký hạ tầng AWS](4.7-Centralized%20Monitoring%20and%20Logging/)
7. [Kiểm thử bảo mật và rà soát hạ tầng](4.8-System%20Testing%20and%20Cleanup/)

