---
title: "Nhật ký công việc tuần 10"
date: 2026-10-17
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

- Thực hiện kiểm thử tổng thể hệ thống bảo mật hạ tầng trên AWS.
- Kiểm tra khả năng kết nối mạng giữa các tài nguyên AWS được triển khai trong các subnet công khai và riêng tư.
- Đánh giá hoạt động của EC2, RDS và Application Load Balancer.
- Kiểm thử các cấu hình bảo mật, bao gồm Security Groups, AWS WAF và quyền truy cập IAM.
- Kiểm tra thông tin giám sát, ghi nhật ký và mức độ tuân thủ cấu hình tài nguyên thông qua CloudWatch, CloudTrail và AWS Config.
- Đánh giá chi phí sử dụng dịch vụ AWS và đề xuất các biện pháp tối ưu tài nguyên.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Rà soát kiến trúc tổng thể của hệ thống bảo mật hạ tầng trên AWS.<br>- Kiểm tra trạng thái VPC, các subnet công khai và riêng tư, Internet Gateway, NAT Gateway và Route Tables.<br>- Kiểm tra cấu hình EC2, RDS và ALB.<br>- Xác định các thành phần chính và chức năng bảo mật cần kiểm thử. | 17/10/2026 | 17/10/2026 | [Tài liệu AWS](https://docs.aws.amazon.com/) |
| 3 | - Kiểm tra khả năng kết nối mạng giữa EC2 và cơ sở dữ liệu RDS.<br>- Kiểm tra kết nối cơ sở dữ liệu thông qua các quy tắc bảo mật đã cấu hình và cổng 3306.<br>- Kiểm tra khả năng truy cập máy chủ web thông qua DNS của ALB.<br>- Ghi nhận kết quả kiểm thử và các vấn đề phát sinh. | 18/10/2026 | 19/10/2026 | [Tài liệu Amazon EC2](https://docs.aws.amazon.com/ec2/)<br>[Tài liệu Amazon RDS](https://docs.aws.amazon.com/rds/) |
| 4 | - Kiểm tra các quy tắc Security Group giữa ALB, EC2 và RDS.<br>- Thực hiện các kiểm thử truy cập cơ bản để đánh giá quy tắc AWS WAF.<br>- Kiểm tra các chỉ số giám sát trên CloudWatch và nhật ký hoạt động trên CloudTrail.<br>- Kiểm tra trạng thái ghi nhận của AWS Config và kết quả đánh giá tuân thủ tài nguyên.<br>- Rà soát quyền IAM và áp dụng nguyên tắc đặc quyền tối thiểu khi phù hợp. | 20/10/2026 | 21/10/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/)<br>[Tài liệu AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| 5 | - Kiểm tra tình hình sử dụng và chi phí ước tính của các dịch vụ AWS trong quá trình triển khai.<br>- Xác định các tài nguyên có thể phát sinh chi phí khi không sử dụng, chẳng hạn EC2, EBS, NAT Gateway và RDS.<br>- Đề xuất biện pháp tối ưu chi phí, bao gồm dừng hoặc giải phóng các tài nguyên không cần thiết sau khi đã thu thập đầy đủ minh chứng cho đề tài.<br>- Tổng hợp kết quả triển khai, kiểm thử, đánh giá ưu điểm, hạn chế của hệ thống và đề xuất hướng cải tiến. | 22/10/2026 | 23/10/2026 | [AWS Pricing](https://aws.amazon.com/pricing/) |

### Kết quả tuần 10:

- Rà soát và đánh giá kiến trúc tổng thể của hệ thống bảo mật hạ tầng trên AWS.
- Kiểm tra khả năng kết nối mạng giữa EC2 và RDS thông qua cổng cơ sở dữ liệu đã cấu hình.
- Kiểm tra hoạt động của máy chủ web thông qua Application Load Balancer.
- Rà soát các quy tắc Security Group và đánh giá khả năng lọc yêu cầu truy cập của AWS WAF thông qua các bài kiểm thử cơ bản.
- Kiểm tra các chỉ số CloudWatch, nhật ký hoạt động CloudTrail và thông tin đánh giá tuân thủ của AWS Config.
- Rà soát quyền IAM và hiểu rõ hơn tầm quan trọng của nguyên tắc đặc quyền tối thiểu.
- Xác định các tài nguyên AWS có thể phát sinh chi phí và tìm hiểu những biện pháp tối ưu chi phí cơ bản.
- Tổng hợp kết quả triển khai, kiểm thử và xác định các hướng cải tiến cho hệ thống bảo mật hạ tầng trên AWS.