---
title: "Triển khai Amazon EC2 và cấu hình Security Group"
date: 2026-10-30
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

### 1. Tổng quan về Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) cung cấp máy chủ ảo trên AWS Cloud. Dịch vụ cho phép triển khai và quản lý tài nguyên tính toán mà không cần duy trì máy chủ vật lý.

Trong dự án này, EC2 instance có tên KLTN-Web-Server được sử dụng để chạy máy chủ web Nginx. Instance được triển khai trong Private Subnet và nhận lưu lượng truy cập web thông qua Application Load Balancer (ALB).

Instance không được gán địa chỉ IPv4 công khai. Việc quản trị được thực hiện thông qua AWS Systems Manager Session Manager.

#### Mục tiêu triển khai

- Triển khai EC2 trong VPC của dự án.

- Đặt instance trong Private Subnet.

- Gắn IAM Role phục vụ kết nối Systems Manager.

- Sử dụng Session Manager để quản trị an toàn.

- Cài đặt và kiểm tra máy chủ web Nginx.

- Cấu hình Security Group để giới hạn lưu lượng mạng.

### 2. Cấu hình EC2 Instance

| Thành phần | Cấu hình |
|---|---|
| Tên Instance | KLTN-Web-Server |
| Loại Instance | t3.micro |
| VPC | KLTN-VPC |
| Subnet | KLTN-Private-Subnet |
| Private IPv4 | 10.0.2.35 |
| Public IPv4 | Không được gán |
| Web Server | Nginx |
| Phương thức quản trị | AWS Systems Manager Session Manager |
| IAM Role | KLTN-EC2-SSM-Role |

![Cấu hình EC2 instance KLTN-Web-Server](/images/4-Workshop/4.4-EC2%20Security%20Group/ec2-instance.png)

#### Kiểm tra EC2 Instance

Các bước kiểm tra:

1. Mở dịch vụ **Amazon EC2**.
2. Chọn **Instances**.
3. Tìm KLTN-Web-Server.
4. Kiểm tra loại Instance, VPC, Subnet, địa chỉ IP riêng và IP công khai.
5. Xác nhận Instance đang chạy và các trạng thái kiểm tra đã thành công.

Instance được triển khai trong mạng riêng nhằm giảm khả năng bị truy cập trực tiếp từ Internet.

![Thông tin mạng EC2 thể hiện IP riêng và không có Public IPv4](/images/4-Workshop/4.4-EC2%20Security%20Group/ec2-network.png)

### 3. Cấu hình IAM Role cho Systems Manager

AWS Systems Manager Session Manager cho phép quản trị viên truy cập EC2 mà không cần mở cổng SSH inbound hoặc quản lý SSH Key Pair.

Dự án sử dụng IAM Role KLTN-EC2-SSM-Role với AWS-managed policy AmazonSSMManagedInstanceCore.

Các bước kiểm tra:

1. Mở dịch vụ **IAM**.
2. Chọn **Roles**.
3. Tìm KLTN-EC2-SSM-Role.
4. Kiểm tra Trusted Entity và các quyền được gắn.
5. Xác nhận Role được gán cho KLTN-Web-Server.

EC2 sử dụng Role này để giao tiếp với Systems Manager.

### 4. Truy cập Instance bằng Session Manager

Để thiết lập phiên quản trị:

1. Mở **EC2 Console**.
2. Chọn KLTN-Web-Server.
3. Nhấn **Connect**.
4. Chọn **Session Manager**.
5. Bắt đầu phiên kết nối.

Phiên làm việc cung cấp quyền truy cập terminal mà không cần địa chỉ IP công khai hoặc quyền SSH inbound.

### 5. Cấu hình Security Group

Security Group hoạt động như tường lửa ảo cho các tài nguyên AWS, kiểm soát lưu lượng inbound và outbound theo các quy tắc đã thiết lập.

Dự án sử dụng Security Group để giới hạn quyền truy cập đến máy chủ web và các thành phần mạng hỗ trợ.

| Thành phần | Giao thức | Cổng | Mục đích |
|---|---|---|---|
| ALB Security Group | TCP | 80 | Tiếp nhận yêu cầu HTTP |
| EC2 Security Group | TCP | 80 | Cho phép HTTP từ ALB chuyển tiếp đến EC2 |
| VPC Endpoint Security Group | TCP | 443 | Cho phép EC2 giao tiếp HTTPS với Endpoint |

EC2 Security Group được cấu hình để nhận lưu lượng web từ ALB Security Group thay vì cho phép truy cập trực tiếp từ các nguồn Internet không giới hạn.

Không cần mở inbound SSH để quản trị vì dự án sử dụng Session Manager.

![Các quy tắc Security Group của EC2](/images/4-Workshop/4.4-EC2%20Security%20Group/security-group.png)

### 6. Cài đặt và kiểm tra Nginx

Nginx là máy chủ web được cài đặt trên EC2 Instance.

Sau khi kết nối bằng Session Manager, có thể sử dụng các lệnh sau trên Ubuntu:

```bash
sudo apt update
sudo apt install nginx -y
```

Khởi động và thiết lập dịch vụ tự chạy:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Kiểm tra trạng thái:

```bash
sudo systemctl status nginx
```

Kiểm tra phản hồi của máy chủ web tại local:

```bash
curl -I http://localhost
```

Phản hồi HTTP thành công xác nhận Nginx đang hoạt động trên EC2.

### 7. Kết quả kiểm tra

Các cấu hình sau đã được xác minh trong quá trình triển khai:

- KLTN-Web-Server đang hoạt động.

- Instance sử dụng IP riêng 10.0.2.35.

- Không được gán địa chỉ IPv4 công khai.

- Instance có IAM Role KLTN-EC2-SSM-Role.

- Session Manager thiết lập được phiên terminal.

- Nginx đang chạy và phản hồi yêu cầu HTTP nội bộ.

#### Kết quả mong đợi

Dự án có máy chủ EC2 riêng tư chạy Nginx. Session Manager cung cấp phương thức quản trị, trong khi Security Group giới hạn giao tiếp mạng theo các luồng cần thiết.

Cấu hình này giúp giảm mức độ phơi nhiễm trực tiếp của máy chủ và tạo nền tảng cho việc bảo vệ lưu lượng web thông qua Application Load Balancer và AWS WAF.

==================================================
