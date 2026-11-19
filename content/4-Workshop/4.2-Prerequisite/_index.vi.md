---
title: "Điều kiện tiên quyết"
date: 2026-10-29
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

### 1. Tổng quan môi trường triển khai

Trước khi triển khai môi trường bảo mật hạ tầng AWS, cần chuẩn bị một số yêu cầu cơ bản như tài khoản AWS, máy tính quản trị, kế hoạch mạng và quyền truy cập phù hợp.

Dự án được triển khai tại khu vực Asia Pacific (Singapore) (ap-southeast-1). Môi trường sử dụng Amazon VPC, EC2, Application Load Balancer, AWS WAF, IAM, AWS Systems Manager cùng các dịch vụ giám sát và ghi nhật ký.

![AWS Management Console tại khu vực Singapore](/images/4-Workshop/4.2-Prerequisites/aws-region.png)

### 2. Các thành phần cần thiết

- **Tài khoản AWS:** Dùng để truy cập AWS Management Console và triển khai các tài nguyên đám mây.

- **AWS Management Console:** Giao diện quản lý và cấu hình các dịch vụ AWS.

- **Danh tính IAM được cấp quyền:** IAM User hoặc Role cần có đủ quyền để tạo và quản lý các tài nguyên được sử dụng trong dự án.

- **Amazon VPC:** Cung cấp môi trường mạng riêng biệt cho hạ tầng đám mây.

- **Amazon EC2:** Chạy máy chủ web Nginx bên trong Private Subnet.

- **VPC Endpoint:** Cung cấp kết nối riêng tư giữa VPC và các dịch vụ AWS được hỗ trợ, bao gồm Systems Manager.

- **Application Load Balancer và AWS WAF:** Hỗ trợ phân phối và bảo vệ lưu lượng truy cập web.

- **Các dịch vụ giám sát và ghi nhật ký:** CloudWatch, CloudTrail, AWS Config, EventBridge và SNS hỗ trợ giám sát, kiểm toán, đánh giá cấu hình và gửi thông báo.

- **Máy tính quản trị:** Cần có trình duyệt web hiện đại và terminal để truy cập AWS Console cũng như thực hiện các bước kiểm tra.

### 3. Yêu cầu trước khi triển khai

Trước khi bắt đầu workshop, cần đảm bảo:

1. Có tài khoản AWS và truy cập được AWS Management Console.
2. Tài khoản có đủ quyền để cấu hình các dịch vụ AWS cần thiết.
3. Có kết nối Internet ổn định và trình duyệt web hiện đại.
4. Đã chọn khu vực Asia Pacific (Singapore) (ap-southeast-1).
5. Đã lên kế hoạch CIDR cho VPC và các Subnet, đảm bảo các dải địa chỉ không bị trùng lặp.
6. Nên có kiến thức cơ bản về địa chỉ IP, chia mạng con, định tuyến và bảo mật mạng.
7. Cần xem xét giá dịch vụ AWS và mức sử dụng tài nguyên để tránh phát sinh chi phí không cần thiết.

### 4. Kết quả mong đợi

Sau giai đoạn chuẩn bị, tài khoản AWS, khu vực triển khai, quyền truy cập và kế hoạch địa chỉ mạng đã sẵn sàng.

Đây là cơ sở để xây dựng môi trường VPC, triển khai EC2 trong mạng riêng, cấu hình truy cập an toàn, bảo vệ lưu lượng web và giám sát hoạt động của hạ tầng.


