---
title: "Cân bằng tải và bảo vệ ứng dụng web"
date: 2026-10-30
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

#### Tổng quan

Application Load Balancer (ALB) và AWS Web Application Firewall (WAF) cung cấp các lớp bảo vệ quan trọng cho ứng dụng web được triển khai trên AWS.

Trong dự án này, Application Load Balancer đóng vai trò là điểm tiếp nhận lưu lượng HTTP đến máy chủ web Nginx trên EC2 riêng tư. AWS WAF được liên kết với ALB để kiểm tra các yêu cầu truy cập và lọc những lưu lượng web có dấu hiệu độc hại.

### 1. Application Load Balancer

Dự án sử dụng Application Load Balancer có tên KLTN-ALB.

ALB tiếp nhận các yêu cầu HTTP và chuyển tiếp lưu lượng phù hợp đến Target Group đã cấu hình.

Các bước kiểm tra cấu hình ALB:

1. Mở dịch vụ **EC2**.
2. Chọn **Load Balancers**.
3. Tìm KLTN-ALB.
4. Kiểm tra Scheme, Listener, Availability Zone và Security Group liên kết.
5. Mở Target Group tương ứng.
6. Kiểm tra EC2 Target đã đăng ký và trạng thái Health.

ALB cung cấp điểm truy cập tập trung đến máy chủ web thay vì yêu cầu người dùng kết nối trực tiếp với EC2 riêng tư.

![Cấu hình và trạng thái KLTN-ALB](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/alb-details.png)

![Target Group và trạng thái EC2 Target](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/target-group.png)

### 2. Cấu hình AWS WAF

AWS WAF được sử dụng để kiểm tra các yêu cầu HTTP và áp dụng quy tắc lọc lưu lượng web.

Dự án sử dụng Web ACL có tên KLTN-WebACL, được liên kết với KLTN-ALB.

Các bước kiểm tra Web ACL:

1. Mở dịch vụ **AWS WAF & Shield**.
2. Chọn **Web ACLs**.
3. Tìm KLTN-WebACL.
4. Kiểm tra tài nguyên AWS được liên kết.
5. Xem các Rule và Rule Group đã cấu hình.
6. Kiểm tra các chỉ số lưu lượng hiện có.

AWS Managed Rules hỗ trợ phát hiện và ngăn chặn các mẫu tấn công web phổ biến, bao gồm SQL Injection và Cross-Site Scripting.

![KLTN-WebACL được liên kết với Application Load Balancer](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-web-acl.png)

![Cấu hình AWS WAF Managed Rules](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-rules.png)

### 3. Kiểm tra lưu lượng web

Dự án thực hiện các yêu cầu HTTP cơ bản để quan sát phản hồi của ứng dụng trước và sau khi áp dụng WAF.

Các trường hợp kiểm tra gồm:

- Yêu cầu HTTP thông thường để xác minh dịch vụ web vẫn truy cập được.

- Mẫu SQL Injection trong tham số yêu cầu.

- Mẫu Cross-Site Scripting (XSS) trong tham số yêu cầu.

- Yêu cầu có dạng Path Traversal.

Ví dụ lệnh kiểm tra:

```bash
curl -i "http://<ALB-DNS>/"
```

Kiểm tra mẫu SQL Injection:

```bash
curl -i "http://<ALB-DNS>/?id=1%20OR%201=1"
```

Kiểm tra mẫu XSS:

```bash
curl -i "http://<ALB-DNS>/?input=<script>alert(1)</script>"
```

Thay <ALB-DNS> bằng DNS thực tế của Application Load Balancer.

![Yêu cầu HTTP thông thường trả về HTTP 200](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-normal-request.png)

### 4. Kết quả kiểm thử

Trong quá trình triển khai, yêu cầu web thông thường đã được máy chủ xử lý thành công.

Các bài kiểm tra bảo mật ghi nhận kết quả:

| Bài kiểm tra | Kết quả quan sát |
|---|---|
| Yêu cầu HTTP thông thường | HTTP 200 |
| Kiểm tra SQL Injection trước khi bật WAF | HTTP 200 |
| Kiểm tra SQL Injection sau khi bật WAF | HTTP 403 |
| Kiểm tra XSS trước khi bật WAF | HTTP 200 |
| Kiểm tra XSS sau khi bật WAF | HTTP 403 |
| Yêu cầu dạng Path Traversal | HTTP 400 |

Phản hồi HTTP 403 trong các bài kiểm tra SQL Injection và XSS cho thấy yêu cầu đã bị chặn bởi lớp bảo vệ web được cấu hình.

Phản hồi HTTP 400 đối với yêu cầu dạng Path Traversal cho thấy yêu cầu bị từ chối. Không nên khẳng định AWS WAF là thành phần trực tiếp chặn yêu cầu này nếu chưa có WAF log hoặc metric xác nhận hành động của Rule tương ứng.

![Yêu cầu kiểm thử SQL Injection và XSS trả về HTTP 403](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-sqli-xss.png)

![AWS WAF Sampled Requests ghi nhận yêu cầu SQL Injection bị chặn](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-sampled-block.png)

### 5. Lợi ích bảo mật

Cấu hình ALB và WAF mang lại các lợi ích:

- Cung cấp điểm tiếp nhận tập trung cho lưu lượng web.

- Phân tách Load Balancer có khả năng tiếp nhận truy cập bên ngoài với EC2 riêng tư.

- Kiểm tra các yêu cầu HTTP đi vào hệ thống.

- Lọc các yêu cầu khớp với quy tắc tấn công web đã cấu hình.

- Giảm khả năng truy cập trực tiếp đến máy chủ ứng dụng.

### 6. Kết luận

Phần này trình bày cách Application Load Balancer và AWS WAF phối hợp để cung cấp khả năng truy cập và bảo vệ lưu lượng web.

Các bài kiểm tra thực tế cho thấy yêu cầu thử nghiệm SQL Injection và XSS nhận phản hồi HTTP 403 sau khi áp dụng WAF, trong khi truy cập web thông thường vẫn trả về HTTP 200.

==================================================
