---
title: "Giám sát và ghi nhật ký hạ tầng AWS"
date: 2026-10-30
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

#### Tổng quan

Phần này giới thiệu các dịch vụ giám sát và ghi nhật ký được sử dụng để theo dõi hạ tầng AWS triển khai trong dự án.

AWS cung cấp nhiều dịch vụ hỗ trợ quản trị viên giám sát hiệu suất tài nguyên, ghi lại các hoạt động trên tài khoản và kiểm tra cấu hình tài nguyên.

Các dịch vụ chính được đề cập trong dự án bao gồm:

- **Amazon CloudWatch:** Giám sát các chỉ số và thông tin hoạt động của tài nguyên AWS.
- **AWS CloudTrail:** Ghi lại các hoạt động trên tài khoản và các sự kiện API.
- **AWS Config:** Ghi nhận cấu hình tài nguyên và đánh giá chúng dựa trên các quy tắc cấu hình.

Các dịch vụ này cung cấp thông tin giúp quản trị viên kiểm tra hoạt động hạ tầng và phát hiện những vấn đề tiềm ẩn về cấu hình hoặc vận hành.

#### 1. Chuẩn bị môi trường giám sát

Trước khi kiểm tra các dịch vụ giám sát, cần xác nhận những tài nguyên AWS sau đã sẵn sàng:

- EC2 instance có tên `KLTN-Web-Server`.
- Application Load Balancer có tên `KLTN-ALB`.
- RDS MySQL instance có tên `kltn-db`.
- Quyền truy cập AWS Management Console.
- Các quyền IAM phù hợp để xem thông tin giám sát và ghi nhật ký.

Các dịch vụ giám sát được kiểm tra trong AWS Region `ap-southeast-1` (Singapore), nơi triển khai hạ tầng của dự án.

#### 2. Giám sát chỉ số EC2 bằng Amazon CloudWatch

Amazon CloudWatch thu thập và hiển thị các chỉ số từ tài nguyên AWS.

Để kiểm tra thông tin giám sát EC2:

1. Mở AWS Management Console.
2. Truy cập **CloudWatch**.
3. Chọn **Metrics**.
4. Mở nhóm chỉ số EC2.
5. Xem các chỉ số có sẵn của EC2 instance.

Một số chỉ số EC2 phổ biến bao gồm:

- `CPUUtilization`: Mức sử dụng CPU.
- `NetworkIn`: Lưu lượng mạng đi vào.
- `NetworkOut`: Lưu lượng mạng đi ra.
- `NetworkPacketsIn`: Số lượng gói tin đi vào.
- `NetworkPacketsOut`: Số lượng gói tin đi ra.

Các chỉ số này giúp quản trị viên theo dõi hiệu suất và hoạt động mạng của EC2 instance.

#### 3. Kiểm tra sự kiện AWS CloudTrail

AWS CloudTrail ghi lại các hoạt động trên tài khoản và sự kiện API được thực hiện trong tài khoản AWS.

Để kiểm tra thông tin CloudTrail:

1. Mở AWS Management Console.
2. Truy cập **CloudTrail**.
3. Chọn **Event history**.
4. Xem các sự kiện quản lý gần đây.
5. Khi cần thiết, lọc sự kiện theo tên sự kiện, tài nguyên hoặc danh tính người dùng.

CloudTrail giúp quản trị viên xác định các thao tác được thực hiện trên tài nguyên AWS, bao gồm tạo tài nguyên, thay đổi cấu hình và các hoạt động liên quan đến truy cập.

#### 4. Kiểm tra cấu hình tài nguyên bằng AWS Config

AWS Config hỗ trợ theo dõi cấu hình tài nguyên và đánh giá chúng dựa trên các quy tắc đã thiết lập.

Trong dự án này, chức năng ghi nhận của AWS Config đã được bật để thu thập thông tin về các tài nguyên AWS.

Để kiểm tra thông tin cấu hình:

1. Mở AWS Management Console.
2. Truy cập **AWS Config**.
3. Kiểm tra danh sách tài nguyên.
4. Khi cần thiết, mở lịch sử cấu hình của một tài nguyên.
5. Xem trạng thái tuân thủ của các quy tắc đã cấu hình.

AWS Config cung cấp thông tin về những thay đổi trong cấu hình tài nguyên và hỗ trợ phát hiện các tài nguyên có thể chưa đáp ứng những quy tắc đã xác định.

**Lưu ý:** Kết quả tuân thủ phụ thuộc vào các quy tắc được cấu hình trong AWS Config. Chỉ nên kết luận tài nguyên tuân thủ khi kết quả đánh giá tương ứng xác nhận điều đó.

#### 5. Tổng hợp kết quả giám sát và ghi nhật ký

Sau khi kiểm tra các dịch vụ, quản trị viên có thể sử dụng thông tin thu thập được để đánh giá tình trạng hoạt động của môi trường AWS.

Bảng sau tổng hợp vai trò của từng dịch vụ:

| Dịch vụ AWS | Mục đích chính |
|---|---|
| Amazon CloudWatch | Giám sát các chỉ số tài nguyên |
| AWS CloudTrail | Ghi lại hoạt động tài khoản và sự kiện API |
| AWS Config | Theo dõi cấu hình tài nguyên và đánh giá mức độ tuân thủ |

Các dịch vụ này bổ trợ cho nhau bằng cách cung cấp những loại thông tin vận hành và bảo mật khác nhau.

#### Kết luận

Trong phần này, Amazon CloudWatch, AWS CloudTrail và AWS Config đã được tìm hiểu và kiểm tra như những dịch vụ giám sát, ghi nhật ký cho hạ tầng AWS.

CloudWatch cung cấp các chỉ số hiệu suất tài nguyên, CloudTrail ghi lại hoạt động trên tài khoản và AWS Config theo dõi cấu hình tài nguyên cũng như đánh giá mức độ tuân thủ.

Kết hợp với nhau, các dịch vụ này hỗ trợ giám sát hạ tầng, kiểm tra cấu hình và quản lý bảo mật trong môi trường AWS.