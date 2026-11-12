---
title: "Nhật ký công việc tuần 9"
date: 2026-10-10
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

- Tìm hiểu AWS Web Application Firewall (AWS WAF) và vai trò của dịch vụ trong việc bảo vệ ứng dụng web.
- Kiểm tra cấu hình Web ACL và mối liên kết với Application Load Balancer (ALB).
- Tìm hiểu cách các quy tắc AWS WAF kiểm tra những yêu cầu truy cập gửi đến hệ thống.
- Thực hiện các kiểm thử cơ bản để đánh giá khả năng cho phép hoặc chặn yêu cầu của AWS WAF.
- Kiểm tra thông tin giám sát và chuẩn bị minh chứng cho quá trình kiểm thử bảo mật.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu kiến trúc và nguyên lý hoạt động của AWS WAF.<br>- Tìm hiểu vai trò của Web ACL và các quy tắc trong việc lọc yêu cầu truy cập.<br>- Kiểm tra ALB đã triển khai trong các tuần trước.<br>- Kiểm tra mối liên kết giữa Web ACL và ALB. | 10/10/2026 | 10/10/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |
| 3 | - Truy cập giao diện quản lý AWS WAF và kiểm tra cấu hình Web ACL.<br>- Xem xét các quy tắc đã cấu hình và hành động tương ứng.<br>- Kiểm tra hành động mặc định và thứ tự ưu tiên của các quy tắc.<br>- Kiểm tra trạng thái tích hợp giữa AWS WAF và ALB. | 11/10/2026 | 12/10/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/web-acl.html) |
| 4 | - Thực hiện kiểm thử truy cập cơ bản thông qua DNS của ALB.<br>- Gửi các yêu cầu truy cập thông thường và kiểm tra khả năng được cho phép.<br>- Thực hiện các yêu cầu kiểm thử có chứa mẫu tương tự SQL Injection để đánh giá hoạt động của quy tắc WAF.<br>- Kiểm tra số liệu thống kê các yêu cầu được cho phép và bị chặn trên AWS WAF. | 13/10/2026 | 14/10/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/waf-metrics.html) |
| 5 | - Kiểm tra số liệu thống kê yêu cầu và cấu hình ghi nhật ký có sẵn của AWS WAF.<br>- Xem xét kết quả các bài kiểm thử truy cập.<br>- Tổng hợp vai trò của AWS WAF trong việc bảo vệ điểm truy cập ứng dụng phía sau ALB.<br>- Thu thập ảnh chụp màn hình và minh chứng phục vụ kiểm thử, đánh giá bảo mật. | 15/10/2026 | 16/10/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Kết quả tuần 9:

- Hiểu được vai trò của AWS WAF trong việc bảo vệ ứng dụng web trước các yêu cầu truy cập không mong muốn và có dấu hiệu độc hại.
- Kiểm tra cấu hình Web ACL và xác nhận mối liên kết với Application Load Balancer.
- Hiểu cách các quy tắc AWS WAF kiểm tra yêu cầu truy cập và thực hiện hành động cho phép hoặc chặn.
- Thực hiện các kiểm thử truy cập cơ bản thông qua điểm truy cập ALB.
- Kiểm tra số liệu thống kê các yêu cầu được cho phép và bị chặn để đánh giá hoạt động của WAF.
- Có thêm kinh nghiệm triển khai AWS WAF như một lớp bảo mật bổ sung cho ứng dụng trên AWS.
- Thu thập thông tin giám sát và minh chứng kiểm thử phục vụ quá trình đánh giá bảo mật tổng thể.