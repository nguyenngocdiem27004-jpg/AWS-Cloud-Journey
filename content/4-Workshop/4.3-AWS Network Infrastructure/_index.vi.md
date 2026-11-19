---
title: "Thiết kế và triển khai hạ tầng mạng AWS"
date: 2026-10-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### 1. Tổng quan hạ tầng mạng AWS

Amazon Virtual Private Cloud (Amazon VPC) cung cấp môi trường mạng được cô lập về mặt logic trong AWS. Dịch vụ cho phép quản trị viên xác định dải địa chỉ IP, tạo Subnet, cấu hình Route Table và kiểm soát kết nối mạng.

Trong dự án này, hạ tầng mạng được triển khai tại khu vực Asia Pacific (Singapore) (ap-southeast-1). VPC cung cấp ranh giới mạng cho dự án. Máy chủ EC2 được đặt trong Private Subnet, trong khi Route Table và Internet Gateway xác định các tuyến kết nối khả dụng.

Môi trường sử dụng VPC Endpoint để cung cấp kết nối riêng tư đến các dịch vụ AWS được hỗ trợ. Cách tiếp cận này cho phép EC2 trong Private Subnet giao tiếp với Systems Manager mà không cần NAT Gateway hoặc địa chỉ IP công khai.

#### Mục tiêu triển khai

- Sử dụng Amazon VPC để cô lập mạng của dự án.

- Tổ chức tài nguyên trong VPC và các Private Subnet.

- Cấu hình Route Table và liên kết Subnet.

- Gắn Internet Gateway vào VPC.

- Cấu hình VPC Endpoint để truy cập riêng tư đến các dịch vụ AWS được hỗ trợ.

- Chuẩn bị hạ tầng mạng cho EC2 web server và Application Load Balancer.

#### Thiết kế địa chỉ IP

Dự án sử dụng dải địa chỉ IPv4 10.0.0.0/16 cho VPC.

| Thành phần | Tên tài nguyên | Dải IP / Cấu hình |
|---|---|---|
| VPC | KLTN-VPC | 10.0.0.0/16 |
| Private Subnet 1 | KLTN-Private-Subnet | 10.0.2.0/24 |
| Private Subnet 2 | KLTN-Private-Subnet-2 | 10.0.4.0/24 |
| Private Route Table | KLTN-Private-RT | Liên kết với các Private Subnet |
| Public Route Table | KLTN-Public-RT | Sử dụng cho định tuyến mạng công khai |
| Internet Gateway | Gắn với KLTN-VPC | Cung cấp kết nối Internet cho tài nguyên có định tuyến phù hợp |
| VPC Endpoint | SSM và SSMMessages | Kết nối riêng tư đến Systems Manager |

### 2. Kiểm tra cấu hình Amazon VPC

Dự án sử dụng VPC đã được tạo với tên KLTN-VPC.

Các bước kiểm tra:

1. Truy cập AWS Management Console.
2. Mở dịch vụ **VPC**.
3. Chọn **Your VPCs**.
4. Tìm và chọn KLTN-VPC.
5. Kiểm tra dải IPv4 CIDR.
6. Xác nhận trạng thái VPC là khả dụng.

VPC được cấu hình với dải IPv4 10.0.0.0/16.

![Cấu hình KLTN-VPC và dải IPv4 CIDR](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/vpc-details.png)

### 3. Kiểm tra Subnet

Subnet chia VPC thành các phân đoạn mạng nhỏ hơn, giúp phân tách tài nguyên theo chức năng và yêu cầu truy cập.

Các bước kiểm tra:

1. Trong VPC Console, chọn **Subnets**.
2. Lọc danh sách theo VPC KLTN-VPC.
3. Kiểm tra tên, IPv4 CIDR và Availability Zone của từng Subnet.
4. Kiểm tra Route Table được liên kết với từng Subnet.
5. Xác nhận các Private Subnet sử dụng bảng định tuyến riêng tương ứng.

Hai Private Subnet được sử dụng trong dự án gồm:

- KLTN-Private-Subnet: 10.0.2.0/24

- KLTN-Private-Subnet-2: 10.0.4.0/24

![Hai Private Subnet trong KLTN-VPC](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/subnets.png)

### 4. Internet Gateway và Route Table

Internet Gateway được gắn với VPC để hỗ trợ kết nối Internet cho những tài nguyên có cấu hình định tuyến và quy tắc bảo mật cho phép.

Dự án có Public Route Table tên KLTN-Public-RT và Private Route Table tên KLTN-Private-RT.

Các bước kiểm tra:

1. Mở **Route tables** trong VPC Console.
2. Chọn KLTN-Public-RT để xem các tuyến đường và Subnet liên kết.
3. Chọn KLTN-Private-RT.
4. Mở tab **Routes** để xem cấu hình định tuyến.
5. Mở **Subnet associations** để xác nhận các Private Subnet được liên kết.

Private Route Table được sử dụng để tách biệt định tuyến của mạng riêng với mạng công khai. NAT Gateway không thuộc môi trường đang triển khai hiện tại.

![Liên kết Subnet trong các Route Table](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/route-tables.png)

### 5. Cấu hình VPC Endpoint

VPC Endpoint cho phép tài nguyên bên trong VPC kết nối đến các dịch vụ AWS được hỗ trợ mà không cần truyền lưu lượng qua tuyến Internet công khai.

Dự án sử dụng các VPC Endpoint liên quan đến Systems Manager để hỗ trợ quản trị EC2 thông qua kết nối riêng tư.

Các Endpoint đã cấu hình gồm:

- KLTN-SSM-Endpoint

- KLTN-SSMMessages-Endpoint

Các bước kiểm tra:

1. Mở VPC Console.
2. Chọn **Endpoints**.
3. Tìm các Endpoint liên quan đến Systems Manager.
4. Kiểm tra tên dịch vụ, VPC liên kết, cấu hình Subnet và Security Group của Endpoint.
5. Xác nhận trạng thái Endpoint là **Available**.

Security Group của Endpoint cho phép lưu lượng HTTPS trên TCP port 443 từ Security Group của EC2.

### 6. Kiểm tra cấu hình mạng

Sau khi rà soát môi trường mạng, cần xác nhận:

- KLTN-VPC sử dụng dải 10.0.0.0/16.

- Hai Private Subnet tồn tại với các dải CIDR tương ứng.

- Public Route Table và Private Route Table khả dụng.

- Internet Gateway được gắn với đúng VPC.

- SSM và SSMMessages VPC Endpoint có trạng thái Available.

- EC2 trong Private Subnet có thể sử dụng các Endpoint đã cấu hình để kết nối Systems Manager.

#### Kết quả mong đợi

VPC cung cấp môi trường mạng riêng biệt cho dự án. Hai Private Subnet, Route Table, Internet Gateway và VPC Endpoint giúp tổ chức kết nối và giảm mức độ phơi nhiễm trực tiếp của EC2.

Phần tiếp theo tập trung vào triển khai EC2 web server và cấu hình Security Group để kiểm soát truy cập mạng.

==================================================
