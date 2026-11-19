---
title: "Giám sát và ghi nhật ký hạ tầng AWS"
date: 2026-10-30
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

#### Tổng quan

Giám sát, ghi nhật ký và theo dõi cấu hình là những yếu tố quan trọng để duy trì tính bảo mật và độ tin cậy của hạ tầng AWS.

Dự án sử dụng Amazon CloudWatch, AWS CloudTrail, AWS Config, Amazon EventBridge và Amazon SNS để theo dõi hoạt động tài nguyên, ghi nhận sự kiện tài khoản, đánh giá cấu hình và gửi thông báo về một số thay đổi liên quan đến bảo mật.

### 1. Amazon CloudWatch

Amazon CloudWatch thu thập và hiển thị dữ liệu giám sát của các tài nguyên AWS.

Trong dự án, CloudWatch được sử dụng để xem xét các chỉ số EC2 và theo dõi thông tin giám sát liên quan đến quá trình xử lý sự kiện bảo mật.

Các bước kiểm tra CloudWatch:

1. Mở dịch vụ **CloudWatch**.
2. Chọn **Metrics**.
3. Xem các chỉ số EC2 hiện có.
4. Chọn các chỉ số của Instance cần theo dõi.
5. Xem biểu đồ CPU Utilization và các chỉ số khả dụng khác.

CloudWatch giúp quản trị viên theo dõi hiệu suất tài nguyên và nhận biết những thay đổi bất thường trong các chỉ số được giám sát.

![Chỉ số CPU Utilization của EC2 trên CloudWatch](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/cloudwatch-metrics.png)

### 2. AWS CloudTrail

AWS CloudTrail ghi lại các hoạt động được thực hiện trong tài khoản AWS, bao gồm các Management Event phát sinh thông qua AWS Management Console, CLI và API.

Dự án sử dụng Trail đa khu vực có tên kltn-trail. Trail chuyển nhật ký đến S3 Bucket và sử dụng mã hóa AWS KMS.

Các bước kiểm tra CloudTrail:

1. Mở dịch vụ **CloudTrail**.
2. Chọn **Trails**.
3. Tìm kltn-trail.
4. Kiểm tra cấu hình Multi-Region.
5. Kiểm tra S3 Destination và cấu hình mã hóa.
6. Mở **Event history** để xem các Management Event đã ghi nhận.

CloudTrail cung cấp dữ liệu kiểm toán giúp quản trị viên điều tra những thay đổi đối với tài nguyên và cấu hình tài khoản AWS.

![Cấu hình kltn-trail trong AWS CloudTrail](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/cloudtrail-trail.png)

### 3. AWS Config

AWS Config ghi nhận cấu hình tài nguyên và đánh giá tài nguyên dựa trên các Configuration Rule.

Dự án bật AWS Config Recorder và sử dụng các quy tắc để kiểm tra một số yêu cầu bảo mật đã lựa chọn.

Các Rule được cấu hình gồm:

- cloudtrail-enabled

- ec2-instance-no-public-ip

- restricted-ssh

- vpc-default-security-group-closed

Các bước kiểm tra AWS Config:

1. Mở dịch vụ **AWS Config**.
2. Kiểm tra trạng thái Recorder.
3. Mở **Resources** để xem danh sách tài nguyên đã ghi nhận.
4. Chọn **Rules**.
5. Kiểm tra kết quả đánh giá của từng Rule.
6. Xem trạng thái Compliant, Noncompliant hoặc Not evaluated.

Cần xem xét kết quả đánh giá của từng Rule riêng biệt. Rule chưa có kết quả đánh giá không được mô tả là Compliant.

![Các quy tắc bảo mật và trạng thái đánh giá trong AWS Config](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/aws-config-rules.png)

### 4. Amazon EventBridge và thông báo SNS

Amazon EventBridge có thể phát hiện các sự kiện AWS được lựa chọn và chuyển chúng đến Target đã cấu hình.

Dự án sử dụng EventBridge Rule có tên KLTN-SG-Change-Alert để phát hiện các thay đổi Ingress hoặc Egress của Security Group EC2.

Rule được kết nối với quy trình gửi thông báo thông qua Amazon SNS.

SNS Topic có tên KLTN-Security-Alert và Email Subscription đã được xác nhận.

Các bước kiểm tra cấu hình thông báo:

1. Mở **Amazon EventBridge**.
2. Chọn **Rules**.
3. Tìm KLTN-SG-Change-Alert.
4. Kiểm tra Event Pattern và Target.
5. Mở **Amazon SNS**.
6. Chọn KLTN-Security-Alert.
7. Kiểm tra Topic và trạng thái xác nhận Email Subscription.

Các chỉ số CloudWatch cũng có thể được sử dụng để xem hoạt động của EventBridge Rule, bao gồm Matched Events và Invocations.

![EventBridge Rule theo dõi thay đổi Security Group đang bật](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/eventbridge-rule.png)

### 5. Lợi ích của hệ thống giám sát

Các dịch vụ giám sát và ghi nhật ký mang lại những lợi ích:

- CloudWatch hỗ trợ theo dõi hiệu suất tài nguyên và các chỉ số giám sát.

- CloudTrail ghi nhận hoạt động tài khoản phục vụ kiểm toán và điều tra.

- AWS Config theo dõi cấu hình tài nguyên và đánh giá các quy tắc bảo mật được lựa chọn.

- EventBridge phát hiện những sự kiện bảo mật đã cấu hình.

- SNS gửi thông báo đến địa chỉ email đã đăng ký.

Sự kết hợp của các dịch vụ này giúp tăng khả năng quan sát hoạt động hạ tầng và hỗ trợ quản trị viên kiểm tra các thay đổi liên quan đến bảo mật.

### 6. Kết luận

Phần này trình bày cách sử dụng các dịch vụ giám sát, ghi nhật ký và thông báo của AWS.

CloudWatch, CloudTrail và AWS Config hỗ trợ giám sát tài nguyên, ghi nhận hoạt động và đánh giá cấu hình. EventBridge và SNS mở rộng khả năng này bằng cách hỗ trợ gửi thông báo khi phát hiện các thay đổi Security Group đã được cấu hình.

==================================================
