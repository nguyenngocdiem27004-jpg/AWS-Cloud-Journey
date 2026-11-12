---
title: "Giới thiệu"
date: 2026-10-29
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

#### Giới thiệu về bảo mật hạ tầng AWS

- **Hạ tầng đám mây AWS** cung cấp môi trường để triển khai và quản lý các tài nguyên tính toán, mạng và cơ sở dữ liệu. AWS cung cấp nhiều dịch vụ hỗ trợ tổ chức xây dựng và quản lý môi trường đám mây.

- **Bảo mật mạng** là một phần quan trọng trong việc bảo vệ hạ tầng đám mây. Amazon VPC, Subnet, Route Table, Security Group và Network Access Control List (NACL) giúp tổ chức tài nguyên mạng và kiểm soát quyền truy cập.

- **Quản lý danh tính và quyền truy cập** giúp quản lý quyền đối với các tài nguyên AWS. AWS Identity and Access Management (IAM) hỗ trợ kiểm soát truy cập và triển khai nguyên tắc đặc quyền tối thiểu.

- **Giám sát và quản lý cấu hình** giúp quản trị viên theo dõi thông tin tài nguyên, xem xét hoạt động tài khoản và đánh giá cấu hình hạ tầng. AWS cung cấp các dịch vụ như Amazon CloudWatch, AWS CloudTrail và AWS Config để hỗ trợ những công việc này.

#### Tổng quan Workshop

Workshop này giới thiệu môi trường hạ tầng AWS và các cấu hình bảo mật được triển khai trong dự án **"Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS."**

Môi trường bao gồm các thành phần chính sau:

- **"Hạ tầng mạng AWS"** sử dụng Amazon VPC để tổ chức mạng đám mây với Public Subnet, Private Subnet, Internet Gateway, NAT Gateway và Route Table.

- **"Môi trường máy chủ và cơ sở dữ liệu"** sử dụng Amazon EC2 để triển khai máy chủ web và Amazon RDS để cung cấp cơ sở dữ liệu MySQL được quản lý. Truy cập mạng giữa các tài nguyên được kiểm soát thông qua các cấu hình bảo mật.

- **"Kiểm soát truy cập và bảo mật mạng"** sử dụng IAM Role và Policy để quản lý quyền, trong khi Security Group kiểm soát lưu lượng mạng giữa Application Load Balancer, EC2 và cơ sở dữ liệu RDS.

- **"Truy cập và bảo vệ ứng dụng"** sử dụng Application Load Balancer (ALB) để cung cấp khả năng truy cập đến máy chủ web. AWS WAF được liên kết với ALB nhằm kiểm tra và lọc các yêu cầu truy cập web.

- **"Giám sát và đánh giá cấu hình"** giới thiệu Amazon CloudWatch, AWS CloudTrail và AWS Config để theo dõi thông tin tài nguyên, xem xét hoạt động tài khoản và kiểm tra cấu hình tài nguyên.

Thông qua workshop này, bạn sẽ tìm hiểu kiến trúc môi trường AWS, cách các dịch vụ phối hợp với nhau, đồng thời xem xét những cấu hình bảo mật và các bài kiểm tra thực tế đã thực hiện trong dự án.