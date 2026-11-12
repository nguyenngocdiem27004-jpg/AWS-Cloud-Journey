---
title: "Triển khai Amazon EC2 và cấu hình Security Group"
date: 2026-10-30
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

#### Tổng quan về Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) là dịch vụ AWS cung cấp máy chủ ảo trên nền tảng đám mây. Dịch vụ này cho phép người dùng triển khai ứng dụng và dịch vụ mà không cần duy trì máy chủ vật lý.

Trong dự án này, một EC2 instance có tên `KLTN-Web-Server` được triển khai để chạy máy chủ web Nginx. Instance thuộc kiến trúc mạng riêng và nhận lưu lượng truy cập web thông qua Application Load Balancer (ALB).

Instance cũng được cấu hình IAM role để hỗ trợ quản trị an toàn thông qua AWS Systems Manager Session Manager.

#### Mục tiêu triển khai

- Triển khai EC2 instance phục vụ máy chủ web của dự án.
- Đặt instance trong subnet phù hợp thuộc `KLTN-VPC`.
- Cấu hình IAM role để hỗ trợ truy cập thông qua Systems Manager.
- Sử dụng Session Manager để truy cập và quản trị instance mà không cần SSH trực tiếp.
- Cài đặt và kiểm tra hoạt động của máy chủ web Nginx.
- Cấu hình Security Group để kiểm soát lưu lượng giữa ALB, EC2 và RDS.

#### Thông số EC2 Instance

| Thành phần | Cấu hình |
|---|---|
| Instance Name | `KLTN-Web-Server` |
| Hệ điều hành | Ubuntu Server |
| VPC | `KLTN-VPC` |
| Subnet | Private subnet |
| Web Server | Nginx |
| Phương thức quản trị | AWS Systems Manager Session Manager |
| IAM Role | IAM role dành cho EC2 để truy cập Systems Manager |

#### Triển khai EC2 Instance

Thực hiện theo các bước sau:

1. Truy cập **AWS Management Console**.
2. Mở dịch vụ **Amazon EC2**.
3. Chọn **Instances**, sau đó nhấn **Launch instances**.
4. Nhập tên instance là `KLTN-Web-Server`.
5. Chọn Amazon Machine Image (AMI) phù hợp với Ubuntu Server.
6. Chọn loại instance phù hợp với yêu cầu dự án và ngân sách.
7. Trong phần **Network settings**, chọn VPC `KLTN-VPC`.
8. Chọn private subnet phù hợp.
9. Cấu hình Security Group cho các kết nối mạng cần thiết.
10. Gắn IAM role cho phép quản trị instance thông qua AWS Systems Manager.
11. Cấu hình dung lượng lưu trữ theo yêu cầu của dự án.
12. Kiểm tra lại cấu hình và nhấn **Launch instance**.

Sau khi khởi chạy, kiểm tra trạng thái của instance phải là **Running** và các kiểm tra trạng thái đã hoàn tất thành công.

#### Cấu hình IAM Role cho Systems Manager

AWS Systems Manager Session Manager cung cấp phương thức truy cập EC2 instance mà không cần mở cổng SSH inbound hoặc quản lý SSH key pair.

Để sử dụng Session Manager, EC2 instance cần được gắn IAM role với các quyền cần thiết cho Systems Manager.

Quy trình cấu hình bao gồm:

1. Mở dịch vụ **IAM** trong AWS Management Console.
2. Tạo hoặc chọn IAM role dành cho EC2.
3. Gắn quyền cần thiết cho Systems Manager, chẳng hạn policy `AmazonSSMManagedInstanceCore`.
4. Quay lại giao diện EC2.
5. Chọn instance `KLTN-Web-Server`.
6. Gắn IAM role cho instance nếu chưa được cấu hình.
7. Kiểm tra khả năng kết nối của instance với Systems Manager.

Sau khi hoàn tất cấu hình, chọn EC2 instance và sử dụng **Connect** → **Session Manager** để mở phiên làm việc trên terminal.

#### Cấu hình Security Group

Security Group hoạt động như một tường lửa ảo, kiểm soát lưu lượng truy cập vào và ra khỏi các tài nguyên AWS. Thành phần này giúp giới hạn quyền truy cập chỉ đối với những kết nối mà hệ thống thực sự cần.

Trong dự án này, Security Group được cấu hình để kiểm soát giao tiếp giữa Application Load Balancer, EC2 web server và RDS database.

Các quy tắc truy cập chính được thiết kế như sau:

| Tài nguyên | Giao thức | Cổng | Nguồn / Đích | Mục đích |
|---|---|---|---|---|
| ALB Security Group | TCP | 80 | Người dùng truy cập, theo cấu hình của ALB | Tiếp nhận yêu cầu truy cập web |
| EC2 Security Group | TCP | 80 | ALB Security Group | Cho phép ALB chuyển tiếp lưu lượng HTTP đến Nginx |
| RDS Security Group | TCP | 3306 | EC2 Security Group | Cho phép EC2 kết nối đến MySQL |

EC2 Security Group không cần quy tắc SSH inbound công khai khi sử dụng Session Manager để quản trị. Các cổng giám sát như `3000`, `9090` và `9100` không được đưa vào cấu hình vì dự án không triển khai Grafana, Prometheus và Node Exporter.

**Các lưu ý về bảo mật:**

- Chỉ cho phép lưu lượng HTTP đến EC2 từ ALB Security Group.
- Chỉ cho phép kết nối MySQL đến RDS từ EC2 Security Group.
- Tránh mở trực tiếp các cổng quản trị ra Internet.
- Áp dụng nguyên tắc đặc quyền tối thiểu khi xác định quy tắc inbound và outbound.
- Security Group có tính chất stateful, vì vậy lưu lượng phản hồi của kết nối được cho phép sẽ tự động được chấp nhận.

#### Cài đặt và kiểm tra Nginx

Nginx được sử dụng làm máy chủ web chạy trên EC2 instance.

Sau khi kết nối đến instance thông qua Session Manager, quản trị viên có thể cài đặt Nginx trên Ubuntu bằng các lệnh sau:

```bash
sudo apt update
sudo apt install nginx -y
```

Khởi động Nginx và cấu hình dịch vụ tự động chạy khi hệ thống khởi động:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Kiểm tra trạng thái dịch vụ:

```bash
sudo systemctl status nginx
```

Nếu Nginx hoạt động bình thường, máy chủ web có thể phản hồi các yêu cầu HTTP được Application Load Balancer chuyển tiếp đến.

#### Kiểm tra cấu hình EC2 và Security Group

Sau khi hoàn tất cấu hình, kiểm tra các nội dung sau:

- EC2 instance `KLTN-Web-Server` có trạng thái **Running**.
- Các kiểm tra trạng thái của instance đã hoàn tất thành công.
- Instance được gắn IAM role cần thiết cho Systems Manager.
- Session Manager có thể tạo phiên kết nối đến instance.
- Dịch vụ Nginx đang hoạt động.
- EC2 Security Group cho phép lưu lượng HTTP từ ALB Security Group.
- RDS Security Group cho phép lưu lượng MySQL trên cổng `3306` từ EC2 Security Group.

Có thể kiểm tra riêng kết nối mạng giữa EC2 và RDS để xác nhận cổng cơ sở dữ liệu cần thiết có thể truy cập được.

#### Kết quả mong đợi

Sau khi hoàn thành phần này, dự án có một EC2 instance chạy Nginx làm máy chủ web. Việc quản trị instance được thực hiện thông qua AWS Systems Manager Session Manager, trong khi Security Group giới hạn giao tiếp giữa ALB, EC2 và RDS.

Các cấu hình này tạo nền tảng cho việc triển khai và bảo vệ dịch vụ web bên trong hạ tầng AWS.