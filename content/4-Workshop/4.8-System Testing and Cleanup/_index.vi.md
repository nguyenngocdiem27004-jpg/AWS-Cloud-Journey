---
title: "Kiểm thử bảo mật và rà soát hạ tầng"
date: 2026-10-30
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

#### Tổng quan

Trong phần cuối này, chúng ta tiến hành rà soát và xác minh hạ tầng AWS đã triển khai trong dự án.

Quá trình kiểm thử tập trung vào khả năng kết nối giữa các tài nguyên AWS, trạng thái hoạt động của máy chủ web EC2, khả năng truy cập cơ sở dữ liệu, chức năng lọc lưu lượng của AWS WAF và các dịch vụ giám sát, ghi nhật ký.

Mục tiêu chính là xác minh các tài nguyên đã triển khai hoạt động theo thiết kế, kiểm tra cấu hình bảo mật và xác định những tài nguyên có thể phát sinh chi phí không cần thiết.

#### 1. Rà soát hạ tầng AWS

Trước khi tiến hành kiểm thử, cần xem lại kiến trúc tổng thể và xác nhận các tài nguyên chính đã sẵn sàng.

Hạ tầng bao gồm:

- **Amazon VPC:** `KLTN-VPC`, sử dụng CIDR `10.0.0.0/16`.
- **Subnet:** Hai public subnet và hai private subnet.
- **Internet Gateway và NAT Gateway:** Cung cấp kết nối Internet theo thiết kế mạng.
- **Amazon EC2:** `KLTN-Web-Server`, triển khai máy chủ web Nginx.
- **Amazon RDS:** `kltn-db`, cung cấp dịch vụ cơ sở dữ liệu MySQL.
- **Application Load Balancer:** `KLTN-ALB`, tiếp nhận lưu lượng truy cập web.
- **AWS WAF:** `KLTN-WebACL`, được liên kết với Application Load Balancer.
- **Giám sát và ghi nhật ký:** Amazon CloudWatch, AWS CloudTrail và AWS Config.

#### 2. Kiểm tra máy chủ web EC2

Trước tiên, kiểm tra trạng thái hoạt động của EC2 instance.

1. Mở AWS Management Console.
2. Truy cập **EC2**.
3. Chọn **Instances**.
4. Tìm `KLTN-Web-Server`.
5. Xác nhận instance đang ở trạng thái **Running**.
6. Kiểm tra các trạng thái kiểm tra của instance đã thành công.

Để kiểm tra dịch vụ Nginx, kết nối đến EC2 bằng AWS Systems Manager Session Manager và thực hiện lệnh:

```bash
sudo systemctl status nginx
```

Dịch vụ cần ở trạng thái đang hoạt động.

Ngoài ra, có thể truy cập máy chủ web thông qua DNS name của Application Load Balancer để xác minh các yêu cầu HTTP được chuyển tiếp thành công.

#### 3. Kiểm tra Application Load Balancer

Application Load Balancer phân phối lưu lượng truy cập web đến các target đã đăng ký.

Để kiểm tra hoạt động:

1. Mở EC2 Console.
2. Chọn **Load Balancers**.
3. Mở `KLTN-ALB`.
4. Kiểm tra trạng thái và DNS name.
5. Mở phần **Target Groups**.
6. Kiểm tra trạng thái sức khỏe của EC2 target đã đăng ký.

Trong quá trình triển khai, target group hiển thị một target healthy và không có target unhealthy.

Khi truy cập DNS name của ALB, trang chào mặc định của Nginx cũng được hiển thị, xác nhận máy chủ web có thể truy cập thông qua load balancer.

#### 4. Kiểm tra kết nối giữa EC2 và RDS

Bài kiểm tra tiếp theo xác minh khả năng kết nối mạng giữa EC2 instance và cơ sở dữ liệu RDS MySQL.

Security Group của RDS được cấu hình cho phép lưu lượng MySQL qua cổng TCP `3306` từ Security Group của EC2.

Có thể kiểm tra kết nối từ EC2 bằng lệnh:

```bash
nc -zv <RDS-endpoint> 3306
```

Trong quá trình triển khai, kết quả kiểm tra hiển thị:

```text
Connected to 10.0.2.198:3306
```

Điều này xác nhận EC2 có thể thiết lập kết nối TCP đến cơ sở dữ liệu RDS thông qua cổng 3306.

**Lưu ý:** Bài kiểm tra này chỉ xác minh khả năng kết nối mạng. Việc truy vấn dữ liệu ở cấp ứng dụng và xử lý dữ liệu từ cơ sở dữ liệu chưa được thực hiện.

#### 5. Kiểm tra chức năng lọc lưu lượng AWS WAF

AWS WAF được liên kết với `KLTN-ALB` để kiểm tra các yêu cầu web gửi đến hệ thống.

Để kiểm tra cấu hình và thống kê lưu lượng:

1. Mở **AWS WAF & Shield**.
2. Chọn **Web ACLs**.
3. Mở `KLTN-WebACL`.
4. Xác nhận `KLTN-ALB` đã được liên kết với Web ACL.
5. Kiểm tra thống kê các yêu cầu truy cập.

Trong quá trình triển khai, dashboard của Web ACL hiển thị kết quả:

| Hành động đối với yêu cầu | Số lượng |
|---|---:|
| Allowed (Cho phép) | 5 |
| Blocked (Chặn) | 25 |
| Tổng cộng | 30 |

Kết quả cho thấy AWS WAF đã xử lý các yêu cầu truy cập và áp dụng những quy tắc lọc lưu lượng đã cấu hình.

#### 6. Kiểm tra các dịch vụ giám sát và ghi nhật ký

Các dịch vụ giám sát và ghi nhật ký cung cấp thông tin về hiệu suất tài nguyên, hoạt động tài khoản và cấu hình hạ tầng.

**Amazon CloudWatch**

Kiểm tra các chỉ số EC2 có sẵn, chẳng hạn:

- `CPUUtilization`
- `NetworkIn`
- `NetworkOut`

Những chỉ số này hỗ trợ theo dõi trạng thái hoạt động và mức sử dụng tài nguyên của EC2 instance.

**AWS CloudTrail**

Kiểm tra cấu hình CloudTrail và lịch sử sự kiện có sẵn để xác định những hoạt động tài khoản và sự kiện quản lý đã được ghi nhận.

**AWS Config**

Kiểm tra danh sách tài nguyên và trạng thái ghi nhận cấu hình.

Trong quá trình triển khai, chức năng ghi nhận của AWS Config đã được bật và danh sách tài nguyên hiển thị 24 tài nguyên.

Trạng thái tuân thủ của từng quy tắc cần được kiểm tra riêng. Không nên mặc định tất cả tài nguyên đều tuân thủ khi chưa xem kết quả đánh giá.

#### 7. Rà soát tài nguyên và chi phí AWS

Trước khi hoàn thành dự án, cần kiểm tra các tài nguyên AWS có thể phát sinh chi phí.

Mở AWS Management Console và rà soát các dịch vụ sau:

- **EC2:** Kiểm tra các instance đang chạy và ổ đĩa được gắn.
- **Elastic IP addresses:** Kiểm tra các địa chỉ IP đã cấp phát và trạng thái liên kết.
- **EBS Volumes:** Rà soát những volume không còn cần thiết.
- **Snapshots:** Kiểm tra các snapshot đang được lưu trữ.
- **NAT Gateway:** Kiểm tra trạng thái và chi phí liên quan.
- **Application Load Balancer:** Xem xét tài nguyên còn cần sử dụng hay không.
- **Amazon RDS:** Kiểm tra instance cơ sở dữ liệu và cấu hình lưu trữ.
- **AWS WAF:** Kiểm tra Web ACL và mức sử dụng liên quan.
- **CloudWatch:** Rà soát các tài nguyên giám sát có thể phát sinh thêm chi phí.

Có thể kiểm tra chi phí ước tính thông qua **Billing and Cost Management**.

**Lưu ý quan trọng:** Dừng EC2 instance không đồng nghĩa với việc tất cả chi phí liên quan đều dừng. NAT Gateway, load balancer, RDS, ổ đĩa lưu trữ và các tài nguyên vẫn được giữ lại có thể tiếp tục phát sinh chi phí.

#### 8. Lưu bằng chứng và rà soát các tài nguyên cần dọn dẹp

Trước khi dừng hoặc xóa bất kỳ tài nguyên AWS nào, cần lưu lại ảnh chụp màn hình và kết quả kiểm thử phục vụ báo cáo cũng như video demo.

Các bằng chứng nên lưu bao gồm:

1. Cấu hình VPC và subnet.
2. Trạng thái EC2 instance và kết quả kiểm tra instance.
3. Quy tắc inbound của Security Group EC2.
4. Quy tắc inbound TCP 3306 của Security Group RDS.
5. Kết quả kiểm tra kết nối EC2 đến RDS.
6. Application Load Balancer và trạng thái healthy của target.
7. Trang Nginx truy cập thông qua DNS name của ALB.
8. Liên kết AWS WAF và thống kê yêu cầu.
9. Các chỉ số EC2 trên CloudWatch.
10. Lịch sử sự kiện CloudTrail.
11. Trạng thái ghi nhận và danh sách tài nguyên AWS Config.

Sau khi lưu đầy đủ bằng chứng, tiến hành xác định những tài nguyên không còn cần thiết.

Chỉ dừng hoặc xóa tài nguyên sau khi đã kiểm tra các thành phần phụ thuộc và xác nhận chúng không còn cần cho báo cáo hoặc buổi trình diễn dự án.

Không xóa các thành phần mạng dùng chung hoặc tài nguyên vẫn đang được những dịch vụ khác sử dụng.

#### 9. Đánh giá tổng thể hạ tầng

Dựa trên quá trình triển khai và kiểm tra, có thể tổng hợp các kết quả chính như sau:

| Thành phần | Kết quả xác minh |
|---|---|
| VPC và hạ tầng mạng | Đã triển khai |
| EC2 instance | Running; các kiểm tra trạng thái thành công |
| Máy chủ web Nginx | Truy cập được thông qua ALB |
| Application Load Balancer | Active; có một target healthy |
| Kết nối EC2 đến RDS | Kết nối TCP cổng 3306 thành công |
| AWS WAF | Đã liên kết với ALB; ghi nhận 30 yêu cầu |
| CloudTrail | Đã tạo |
| AWS Config | Đã bật recording; hiển thị 24 tài nguyên |
| CloudWatch | Đã sử dụng để kiểm tra các chỉ số tài nguyên |

Các kết quả này thể hiện khả năng hoạt động của những thành phần hạ tầng AWS chính và các biện pháp bảo mật đã áp dụng trong dự án.

#### Kết luận

Trong phần cuối này, chúng ta đã rà soát và xác minh hạ tầng AWS được triển khai trong dự án.

Các bài kiểm tra xác nhận máy chủ web EC2 có thể truy cập thông qua Application Load Balancer, EC2 có thể thiết lập kết nối TCP đến cơ sở dữ liệu RDS MySQL và AWS WAF đã xử lý các yêu cầu truy cập web.

Bên cạnh đó, CloudWatch, CloudTrail và AWS Config cũng được kiểm tra để tìm hiểu cách AWS hỗ trợ giám sát, ghi nhận hoạt động và theo dõi cấu hình tài nguyên.

Kết quả dự án thể hiện quá trình triển khai hạ tầng mạng AWS và áp dụng các biện pháp bảo mật nhằm bảo vệ tài nguyên trong môi trường điện toán đám mây.