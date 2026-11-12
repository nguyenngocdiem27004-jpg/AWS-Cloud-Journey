---
title: "Cấu hình AWS WAF và lọc lưu lượng truy cập web"
date: 2026-10-30
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

#### Tổng quan

Phần này trình bày quá trình cấu hình AWS Web Application Firewall (AWS WAF) nhằm tăng cường bảo vệ hạ tầng ứng dụng web được triển khai trên AWS.

AWS WAF được liên kết với Application Load Balancer (ALB) để kiểm tra các yêu cầu HTTP gửi đến và áp dụng các quy tắc lọc lưu lượng đã cấu hình.

Trong dự án này, Web ACL có tên `KLTN-WebACL` được liên kết với `KLTN-ALB`. Mục tiêu là kiểm soát lưu lượng truy cập web và minh họa cách AWS WAF cho phép hoặc chặn các yêu cầu dựa trên những quy tắc được thiết lập.

#### 1. Chuẩn bị môi trường WAF

Trước khi cấu hình AWS WAF, cần xác nhận các tài nguyên sau đã sẵn sàng:

- Application Load Balancer có tên `KLTN-ALB`.
- AWS WAF Web ACL có tên `KLTN-WebACL`.
- Máy chủ web đang hoạt động phía sau Application Load Balancer.
- Quyền truy cập AWS Management Console.

Application Load Balancer đóng vai trò là điểm tiếp nhận lưu lượng truy cập web, trong khi AWS WAF kiểm tra các yêu cầu trước khi chúng được chuyển đến máy chủ web.

#### 2. Tạo và cấu hình Web ACL

Để cấu hình AWS WAF:

1. Mở AWS Management Console.
2. Truy cập **AWS WAF & Shield**.
3. Chọn **Web ACLs**.
4. Mở Web ACL có tên `KLTN-WebACL`.
5. Kiểm tra các quy tắc đã cấu hình và hành động mặc định.
6. Kiểm tra tài nguyên AWS được liên kết.

Web ACL chứa các quy tắc xác định liệu những yêu cầu truy cập đến có được cho phép hay bị chặn.

#### 3. Liên kết AWS WAF với Application Load Balancer

AWS WAF được liên kết với Application Load Balancer để kiểm tra các yêu cầu HTTP gửi đến hệ thống.

Thực hiện kiểm tra liên kết như sau:

1. Mở AWS WAF Console.
2. Chọn `KLTN-WebACL`.
3. Kiểm tra danh sách tài nguyên AWS được liên kết.
4. Xác nhận `KLTN-ALB` xuất hiện trong danh sách.

Cấu hình này cho phép AWS WAF kiểm tra các yêu cầu web trước khi chúng được chuyển tiếp đến máy chủ EC2.

#### 4. Kiểm tra kết quả lọc lưu lượng truy cập

Sau khi liên kết Web ACL với Application Load Balancer, tiến hành kiểm tra thống kê yêu cầu trong AWS WAF Console.

Dashboard cung cấp thông tin về số lượng yêu cầu được cho phép hoặc bị chặn bởi các quy tắc đã cấu hình.

Trong quá trình triển khai, dashboard của Web ACL hiển thị kết quả như sau:

| Hành động đối với yêu cầu | Số lượng |
|---|---:|
| Allowed (Cho phép) | 5 |
| Blocked (Chặn) | 25 |
| Tổng cộng | 30 |

Kết quả này cho thấy AWS WAF đã xử lý các yêu cầu truy cập và áp dụng những quy tắc lọc lưu lượng.

#### 5. Xác minh cấu hình WAF

Để xác minh cấu hình:

1. Mở AWS WAF Console.
2. Chọn `KLTN-WebACL`.
3. Kiểm tra tài nguyên được liên kết và xác nhận `KLTN-ALB` đã được gắn.
4. Xem lại thống kê các yêu cầu truy cập.
5. So sánh số lượng yêu cầu được cho phép và bị chặn.

Ngoài ra, có thể truy cập ALB thông qua DNS name để xác minh máy chủ web có thể truy cập được.

**Lưu ý:** Thống kê yêu cầu cho thấy AWS WAF đã xử lý và lọc lưu lượng truy cập. Không nên xem đây là bằng chứng đã kiểm thử thành công tất cả các loại tấn công nếu chưa có kết quả kiểm thử tương ứng.

#### Kết luận

Trong phần này, AWS WAF đã được cấu hình và liên kết với Application Load Balancer để kiểm tra lưu lượng truy cập web.

Thống kê ghi nhận 30 yêu cầu đã được xử lý, trong đó có 5 yêu cầu được cho phép và 25 yêu cầu bị chặn. Kết quả này minh họa cách AWS WAF cung cấp thêm một lớp bảo vệ cho hạ tầng web được triển khai trên AWS.