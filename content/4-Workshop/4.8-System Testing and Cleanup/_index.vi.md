---
title: "Kiểm thử bảo mật và rà soát hạ tầng"
date: 2026-10-30
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

#### Tổng quan

Phần cuối cùng tập trung rà soát hạ tầng AWS và tổng hợp các hoạt động kiểm tra bảo mật đã thực hiện trong dự án.

Quá trình kiểm thử tập trung vào khả năng truy cập EC2 riêng tư, trạng thái máy chủ web, hoạt động chuyển tiếp lưu lượng của ALB, khả năng lọc của AWS WAF, cấu hình Security Group và các dịch vụ giám sát, ghi nhật ký.

Mục đích là xác minh các biện pháp bảo mật đã triển khai, xác định những vấn đề cấu hình tiềm ẩn và xem xét mức sử dụng tài nguyên.

### 1. Rà soát hạ tầng AWS

Các tài nguyên chính được kiểm tra trong giai đoạn xác minh cuối cùng bao gồm:

| Thành phần | Tài nguyên / Cấu hình |
|---|---|
| VPC | KLTN-VPC |
| VPC CIDR | 10.0.0.0/16 |
| Private Subnet | 10.0.2.0/24 và 10.0.4.0/24 |
| EC2 Instance | KLTN-Web-Server |
| EC2 Private IP | 10.0.2.35 |
| Phương thức truy cập EC2 | AWS Systems Manager Session Manager |
| Web Server | Nginx |
| Load Balancer | KLTN-ALB |
| Web ACL | KLTN-WebACL |
| Giám sát | CloudWatch, CloudTrail, AWS Config |
| Thông báo | EventBridge và SNS |

Quá trình rà soát xác nhận các thành phần chính đang được sử dụng trong hạ tầng hiện tại. RDS và NAT Gateway không được đưa vào danh sách tài nguyên đang hoạt động trong cấu hình cuối cùng này.

![Thông tin EC2 riêng tư, không có Public IPv4](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-private-ec2.png)

### 2. Kiểm tra EC2 và máy chủ web

EC2 Instance được kiểm tra để xác nhận máy chủ đang hoạt động trong Private Subnet và không được gán địa chỉ IPv4 công khai.

Các bước kiểm tra gồm:

- Xác nhận KLTN-Web-Server đang chạy.

- Kiểm tra các trạng thái kiểm tra Instance.

- Xác minh địa chỉ IP riêng.

- Xác nhận Session Manager thiết lập được kết nối.

- Kiểm tra dịch vụ Nginx đang hoạt động.

Có thể kiểm tra phản hồi của máy chủ web từ terminal EC2 bằng lệnh:

```bash
curl -I http://localhost
```

Phản hồi HTTP thành công xác nhận Nginx đang xử lý yêu cầu nội bộ.

### 3. Kiểm tra Application Load Balancer

Application Load Balancer được kiểm tra để xác nhận khả năng chuyển tiếp yêu cầu web đến EC2 Target.

Các nội dung xác minh gồm:

- Kiểm tra cấu hình Listener của ALB.

- Kiểm tra Target Group liên kết.

- Xác nhận Target đã đăng ký có trạng thái Healthy.

- Gửi yêu cầu HTTP thông thường đến DNS của ALB.

Phản hồi HTTP 200 xác nhận dịch vụ web có thể được truy cập thông qua ALB.

![Kiểm tra yêu cầu web thông thường](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-normal.png)

### 4. Kiểm thử bảo mật AWS WAF

AWS WAF được kiểm tra bằng các mẫu yêu cầu HTTP thông thường và những yêu cầu có dấu hiệu độc hại.

Kết quả quan sát được tổng hợp như sau:

| Trường hợp kiểm thử | Kết quả |
|---|---|
| Yêu cầu HTTP thông thường | HTTP 200 |
| Mẫu SQL Injection trước khi áp dụng WAF | HTTP 200 |
| Mẫu SQL Injection sau khi áp dụng WAF | HTTP 403 |
| Mẫu XSS trước khi áp dụng WAF | HTTP 200 |
| Mẫu XSS sau khi áp dụng WAF | HTTP 403 |
| Yêu cầu dạng Path Traversal | HTTP 400 |

Kết quả cho thấy cấu hình WAF đã chặn các yêu cầu thử nghiệm SQL Injection và XSS, trong khi truy cập web thông thường vẫn hoạt động.

Yêu cầu dạng Path Traversal bị từ chối với HTTP 400. Chỉ dựa vào mã phản hồi này chưa thể xác định chính xác thành phần AWS nào đã từ chối yêu cầu.

![Kiểm thử SQL Injection và XSS sau khi áp dụng WAF](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-sqli-xss.png)

### 5. Rà soát mạng và kiểm soát truy cập

Các cấu hình mạng và kiểm soát truy cập được rà soát nhằm đảm bảo tài nguyên riêng tư không bị phơi bày không cần thiết.

Các nội dung kiểm tra gồm:

- Xác nhận EC2 không có địa chỉ IPv4 công khai.

- Kiểm tra các quy tắc Security Group của EC2.

- Xác nhận quyền quản trị được cung cấp thông qua Session Manager.

- Kiểm tra IAM Role được gán cho EC2.

- Kiểm tra trạng thái các Systems Manager VPC Endpoint.

- Rà soát cấu hình Public Route Table và Private Route Table.

Các bước kiểm tra này giúp xác minh quyền truy cập máy chủ riêng tư được kiểm soát thông qua cấu hình mạng và danh tính phù hợp.

### 6. Rà soát giám sát và cấu hình

Các dịch vụ giám sát và kiểm toán được rà soát để xác nhận hoạt động và cấu hình hạ tầng có thể được kiểm tra.

**Amazon CloudWatch**

Kiểm tra các chỉ số EC2 hiện có và chỉ số hoạt động của EventBridge, bao gồm Matched Events và Invocations.

**AWS CloudTrail**

Kiểm tra cấu hình kltn-trail và Event History để xem các hoạt động tài khoản đã được ghi nhận.

**AWS Config**

Kiểm tra trạng thái Recorder, danh sách tài nguyên và kết quả đánh giá của các quy tắc bảo mật đã cấu hình.

Các Rule được sử dụng gồm:

- cloudtrail-enabled

- ec2-instance-no-public-ip

- restricted-ssh

- vpc-default-security-group-closed

Trạng thái tuân thủ phải được xác định dựa trên kết quả đánh giá thực tế hiển thị trong AWS Config.

**EventBridge và SNS**

Kiểm tra Rule KLTN-SG-Change-Alert và SNS Topic KLTN-Security-Alert để xác minh cấu hình thông báo về thay đổi Security Group.

### 7. Rà soát tài nguyên và chi phí AWS

Các tài nguyên AWS cần được kiểm tra trước và sau quá trình thử nghiệm để tránh phát sinh chi phí không cần thiết.

Các dịch vụ và tài nguyên cần xem xét gồm:

- **EC2:** Kiểm tra Instance đang chạy và loại Instance.

- **EBS:** Kiểm tra Volume đang gắn và dung lượng lưu trữ không còn sử dụng.

- **Elastic Load Balancing:** Kiểm tra Application Load Balancer và mức sử dụng.

- **VPC Endpoint:** Kiểm tra các Endpoint đã cấu hình và chi phí liên quan.

- **AWS WAF:** Kiểm tra Web ACL và chi phí sử dụng.

- **CloudWatch:** Kiểm tra Metrics, Logs và các tài nguyên giám sát bổ sung.

- **CloudTrail và AWS Config:** Kiểm tra cấu hình ghi nhận và lưu trữ dữ liệu.

- **SNS:** Kiểm tra Topic thông báo và Subscription.

Billing and Cost Management có thể được sử dụng để xem chi phí theo dịch vụ và mức chi tiêu ước tính.

Những tài nguyên không còn cần thiết cho quá trình kiểm thử nên được dừng hoặc xóa khi phù hợp. Các tài nguyên ghi nhật ký và kiểm toán cần được lưu giữ theo yêu cầu tài liệu của dự án.

### 8. Tổng hợp kết quả kiểm tra

| Hạng mục xác minh | Kết quả quan sát |
|---|---|
| VPC KLTN-VPC | Đã cấu hình |
| Private Subnet | Đã cấu hình hai Subnet |
| EC2 KLTN-Web-Server | Đang hoạt động |
| Public IPv4 của EC2 | Không được gán |
| Session Manager | Kết nối thành công |
| Nginx | Đang hoạt động |
| Application Load Balancer | Đã triển khai; đã kiểm tra trạng thái Target |
| AWS WAF | Đã liên kết với ALB |
| Kiểm tra SQL Injection sau WAF | HTTP 403 |
| Kiểm tra XSS sau WAF | HTTP 403 |
| CloudTrail | Đã cấu hình Trail |
| AWS Config | Đã bật ghi nhận |
| EventBridge | Đã bật Rule theo dõi thay đổi Security Group |
| SNS | Đã xác nhận Email Subscription |

### 9. Kết luận

Quá trình xác minh cuối cùng cho thấy các thành phần hạ tầng AWS chính và những biện pháp bảo mật được triển khai trong dự án đã hoạt động theo mục tiêu thiết kế.

Máy chủ EC2 hoạt động trong Private Subnet và có thể được quản trị thông qua Systems Manager Session Manager mà không cần địa chỉ IP công khai hoặc quyền SSH inbound.

Application Load Balancer cung cấp khả năng truy cập máy chủ web, trong khi AWS WAF chặn các yêu cầu thử nghiệm SQL Injection và XSS. CloudWatch, CloudTrail, AWS Config, EventBridge và SNS cung cấp thêm khả năng giám sát, kiểm toán, rà soát cấu hình và gửi thông báo.

Dự án qua đó minh họa cách kết hợp các dịch vụ mạng, quản lý danh tính, bảo vệ ứng dụng web và giám sát của AWS nhằm cải thiện bảo mật hạ tầng, đồng thời kiểm soát việc sử dụng tài nguyên.
