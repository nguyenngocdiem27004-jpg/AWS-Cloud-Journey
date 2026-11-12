---
title: "Thiết kế và triển khai hạ tầng mạng AWS"
date: 2026-10-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

#### Tổng quan về hạ tầng mạng AWS

Amazon Virtual Private Cloud (Amazon VPC) cung cấp một môi trường mạng được cô lập về mặt logic trên AWS. Dịch vụ này cho phép quản trị viên cấu hình dải địa chỉ IP, subnet, bảng định tuyến và kết nối mạng cho các tài nguyên trên nền tảng đám mây.

Trong dự án này, hạ tầng mạng AWS được triển khai tại khu vực Châu Á Thái Bình Dương (Singapore) (`ap-southeast-1`). VPC được chia thành các public subnet và private subnet nhằm phân tách tài nguyên theo chức năng và yêu cầu truy cập.

Các thành phần mạng chính bao gồm Amazon VPC, public subnet, private subnet, Internet Gateway, NAT Gateway và route table. Những thành phần này cung cấp khả năng kết nối mạng đồng thời hỗ trợ kiểm soát truy cập đến các tài nguyên bên trong VPC.

#### Mục tiêu triển khai

- Tạo và cấu hình Amazon VPC với dải địa chỉ IP phù hợp.
- Chia VPC thành các public subnet và private subnet trên các Availability Zone.
- Gắn Internet Gateway để cung cấp kết nối Internet cho public subnet.
- Cấu hình NAT Gateway để cho phép tài nguyên trong private subnet truy cập Internet khi cần thiết.
- Cấu hình route table và liên kết subnet nhằm kiểm soát lưu lượng mạng.
- Chuẩn bị môi trường mạng để triển khai Amazon EC2 và Amazon RDS.

#### Thiết kế địa chỉ IP

Dự án sử dụng dải địa chỉ IP riêng `10.0.0.0/16` cho VPC. Dải địa chỉ này cung cấp đủ không gian địa chỉ để chia thành nhiều public subnet và private subnet.

| Thành phần | Tên tài nguyên | Dải IP / Cấu hình |
|---|---|---|
| Amazon VPC | KLTN-VPC | `10.0.0.0/16` |
| Public Subnet | Được cấu hình trong KLTN-VPC | Kiểm tra CIDR thực tế trên AWS Console |
| Private Subnet 2 | KLTN-Private-Subnet-2 | `10.0.4.0/24` |
| Internet Gateway | Gắn với KLTN-VPC | Cung cấp kết nối Internet cho public subnet |
| NAT Gateway | Được cấu hình trong public subnet | Cho phép private subnet truy cập Internet theo chiều đi ra |
| Private Route Table | KLTN-Private-RT | Định tuyến cho các private subnet được liên kết |

Dải CIDR và Availability Zone của các subnet còn lại cần được kiểm tra trực tiếp trên Amazon VPC Console để bảo đảm tài liệu khớp với hệ thống đã triển khai.

#### Triển khai Amazon VPC

Amazon VPC là một mạng ảo được cô lập về mặt logic, cho phép quản trị viên kiểm soát dải địa chỉ IP, subnet, định tuyến và kết nối mạng.

Dự án sử dụng VPC đã được tạo với tên `KLTN-VPC`.

Các bước kiểm tra cấu hình VPC:

1. Truy cập AWS Management Console.
2. Mở dịch vụ **Amazon VPC**.
3. Chọn **Your VPCs**.
4. Tìm và chọn `KLTN-VPC`.
5. Kiểm tra dải IPv4 CIDR và các thiết lập mạng khác.
6. Xác nhận VPC đang hoạt động và cấu hình phù hợp với thiết kế của dự án.

VPC sử dụng dải địa chỉ IPv4 CIDR `10.0.0.0/16`.

#### Tạo và cấu hình Subnet

Subnet chia VPC thành các phân đoạn mạng nhỏ hơn. Public subnet được sử dụng cho các tài nguyên cần có tuyến kết nối đến Internet Gateway, trong khi private subnet được sử dụng cho các tài nguyên không nên được truy cập trực tiếp từ Internet.

Dự án sử dụng hai public subnet và hai private subnet.

Các bước kiểm tra cấu hình subnet:

1. Trong Amazon VPC Console, chọn **Subnets**.
2. Lọc danh sách subnet theo VPC `KLTN-VPC`.
3. Kiểm tra tên, dải IPv4 CIDR và Availability Zone của cả bốn subnet.
4. Xác nhận public subnet và private subnet sử dụng các dải mạng riêng biệt.
5. Kiểm tra route table được liên kết với từng subnet.
6. Đối với public subnet cần tự động cấp địa chỉ IPv4 công khai, kiểm tra tùy chọn **Enable auto-assign public IPv4 address**.

Một private subnet được sử dụng trong dự án có tên `KLTN-Private-Subnet-2`, với dải CIDR `10.0.4.0/24`.

#### Tạo và gắn Internet Gateway

Internet Gateway cho phép các tài nguyên trong VPC giao tiếp với Internet khi đã có cấu hình định tuyến và bảo mật phù hợp.

Các bước kiểm tra cấu hình Internet Gateway:

1. Trong Amazon VPC Console, chọn **Internet gateways**.
2. Tìm Internet Gateway được gắn với `KLTN-VPC`.
3. Chọn Internet Gateway và kiểm tra thông tin chi tiết.
4. Xác nhận trạng thái cho biết Internet Gateway đã được gắn với đúng VPC.

Internet Gateway được sử dụng trong public route table để tạo tuyến kết nối ra Internet.

#### Cấu hình NAT Gateway

NAT Gateway cho phép các tài nguyên trong private subnet chủ động khởi tạo kết nối ra Internet mà không cho phép các kết nối không được yêu cầu từ Internet đi vào.

Các bước kiểm tra cấu hình NAT Gateway:

1. Trong Amazon VPC Console, chọn **NAT gateways**.
2. Tìm NAT Gateway được cấu hình cho dự án.
3. Kiểm tra trạng thái là **Available**.
4. Xác nhận NAT Gateway được triển khai trong một public subnet.
5. Kiểm tra private route table để xác nhận tuyến mặc định trỏ đến NAT Gateway.

NAT Gateway cung cấp khả năng truy cập Internet theo chiều đi ra cho các tài nguyên trong private subnet khi cần thiết.

#### Cấu hình Route Table

Route table xác định hướng chuyển tiếp của lưu lượng mạng. Public subnet và private subnet sử dụng các bảng định tuyến với cấu hình khác nhau.

Đối với public route table:

1. Trong Amazon VPC Console, chọn **Route tables**.
2. Chọn route table được liên kết với các public subnet.
3. Mở tab **Routes**.
4. Kiểm tra tuyến `0.0.0.0/0` trỏ đến Internet Gateway.
5. Mở **Subnet associations** và kiểm tra các public subnet được liên kết.

Đối với private route table:

1. Chọn `KLTN-Private-RT`.
2. Mở tab **Routes**.
3. Kiểm tra tuyến `0.0.0.0/0` trỏ đến NAT Gateway nếu private subnet cần truy cập Internet.
4. Mở **Subnet associations**.
5. Kiểm tra các private subnet được liên kết với route table này.

Cấu hình route table giúp phân tách lưu lượng mạng public và private, đồng thời đáp ứng yêu cầu truy cập của hệ thống.

#### Kiểm tra cấu hình triển khai

Sau khi kiểm tra cấu hình mạng, cần xác nhận các nội dung sau:

- VPC `KLTN-VPC` sử dụng dải CIDR `10.0.0.0/16`.
- VPC có hai public subnet và hai private subnet.
- Internet Gateway đã được gắn với đúng VPC.
- Public route table có tuyến mặc định trỏ đến Internet Gateway.
- NAT Gateway đang ở trạng thái khả dụng và được đặt trong public subnet.
- Private route table sử dụng NAT Gateway làm tuyến mặc định khi cần truy cập Internet theo chiều đi ra.
- Các subnet được liên kết với route table phù hợp với thiết kế mạng.

#### Kết quả mong đợi

Sau khi hoàn thành phần này, hạ tầng mạng AWS cung cấp nền tảng để triển khai và kết nối các tài nguyên trên môi trường đám mây. Public subnet và private subnet giúp phân tách tài nguyên theo yêu cầu truy cập, trong khi Internet Gateway, NAT Gateway và route table kiểm soát khả năng kết nối mạng.

Phần tiếp theo tập trung vào Amazon EC2 và Security Groups, được sử dụng để triển khai máy chủ web và kiểm soát quyền truy cập mạng đến EC2 instance.