---
title: "Workshop"
date: 2026-10-27
weight: 5
chapter: false
pre: " <b> 4. </b> "
---

# Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS

#### Tổng quan

Trong workshop này, chúng ta sẽ tìm hiểu quá trình thiết kế và triển khai hạ tầng điện toán đám mây an toàn bằng Amazon Web Services (AWS).

Dự án tập trung xây dựng môi trường mạng AWS với Amazon VPC, public subnet, private subnet, Internet Gateway, NAT Gateway và các bảng định tuyến. Amazon EC2 được triển khai làm máy chủ web, trong khi Amazon RDS cung cấp dịch vụ cơ sở dữ liệu trong môi trường đám mây.

Để tăng cường bảo mật hạ tầng, dự án áp dụng các dịch vụ AWS Identity and Access Management (IAM), Security Groups, Application Load Balancer (ALB) và AWS Web Application Firewall (WAF). Bên cạnh đó, Amazon CloudWatch, AWS CloudTrail và AWS Config được sử dụng để kiểm tra hiệu suất tài nguyên, hoạt động tài khoản và cấu hình các tài nguyên AWS.

Thông qua workshop này, chúng ta sẽ tìm hiểu kiến trúc mạng AWS, triển khai và cấu hình các tài nguyên đám mây, kiểm soát quyền truy cập mạng, xác minh kết nối giữa EC2 và RDS, đồng thời tìm hiểu các chức năng giám sát và bảo mật do AWS cung cấp.

#### Mục tiêu

- **Kiến trúc đám mây AWS:** Tìm hiểu và thiết kế hạ tầng đám mây sử dụng Amazon VPC và các thành phần mạng liên quan.
- **Hạ tầng mạng AWS:** Cấu hình VPC, public subnet, private subnet, Internet Gateway, NAT Gateway và các bảng định tuyến.
- **Triển khai Amazon EC2:** Triển khai máy chủ web và cấu hình truy cập an toàn bằng IAM role và Systems Manager Session Manager.
- **Kết nối cơ sở dữ liệu:** Cấu hình quyền truy cập mạng giữa Amazon EC2 và Amazon RDS thông qua Security Group.
- **Bảo mật hạ tầng:** Áp dụng quyền IAM, Security Group, Application Load Balancer và AWS WAF.
- **Giám sát và ghi nhật ký:** Tìm hiểu Amazon CloudWatch, AWS CloudTrail và AWS Config.
- **Kiểm tra bảo mật:** Xác minh kết nối mạng, kiểm tra các quy tắc kiểm soát truy cập và rà soát cấu hình bảo mật của tài nguyên AWS.

#### Nội dung

1. [Giới thiệu](5.1-Workshop-overview/)
2. [Các yêu cầu chuẩn bị](5.2-Prerequisite/)
3. [Thiết kế và triển khai hạ tầng mạng AWS](5.3-AWS-Network-Infrastructure/)
4. [Triển khai Amazon EC2 và cấu hình Security Group](5.4-EC2-Security-Groups/)
5. [Kết nối giữa Amazon EC2 và Amazon RDS](5.5-Site-to-Site-VPN/)
6. [Cấu hình AWS WAF và lọc lưu lượng truy cập web](5.6-VPN-Routing-Failover/)
7. [Giám sát và ghi nhật ký hạ tầng AWS](5.7-Centralized-Monitoring/)
8. [Kiểm thử bảo mật và rà soát hạ tầng](5.8-System-Testing-Cleanup/)