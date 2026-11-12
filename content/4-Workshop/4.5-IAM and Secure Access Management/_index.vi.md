---
title: "Kết nối giữa Amazon EC2 và Amazon RDS"
date: 2026-10-30
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

#### Tổng quan

Phần này trình bày quá trình kết nối mạng giữa máy chủ Amazon EC2 và cơ sở dữ liệu Amazon RDS MySQL trong môi trường AWS.

EC2 instance `KLTN-Web-Server` được sử dụng làm máy chủ web, trong khi RDS instance `kltn-db` cung cấp dịch vụ cơ sở dữ liệu. Việc giao tiếp giữa hai tài nguyên này được kiểm soát thông qua các Security Group tương ứng.

Mục tiêu là cho phép EC2 truy cập cơ sở dữ liệu RDS thông qua cổng MySQL (TCP 3306), đồng thời giới hạn quyền truy cập cơ sở dữ liệu đối với các tài nguyên được phép.

#### 1. Chuẩn bị môi trường

Trước khi kiểm tra kết nối, cần xác nhận các tài nguyên sau đã sẵn sàng:

- VPC hiện có với tên `KLTN-VPC`.
- EC2 instance có tên `KLTN-Web-Server`.
- RDS MySQL instance có tên `kltn-db`.
- Security Group được gán cho EC2 và RDS.
- Các tuyến mạng cho phép hai tài nguyên giao tiếp với nhau.

EC2 instance và cơ sở dữ liệu RDS được triển khai trong AWS VPC. RDS sử dụng DB subnet group bao gồm các private subnet.

#### 2. Cấu hình Security Group

Security Group kiểm soát lưu lượng mạng đi vào và đi ra khỏi các tài nguyên AWS. Để cho phép EC2 kết nối đến RDS, cần cấu hình quy tắc inbound của Security Group gắn với RDS.

**Security Group của EC2**

Security Group của EC2 cho phép lưu lượng HTTP đi vào từ Security Group của Application Load Balancer.

**Security Group của RDS**

Cấu hình quy tắc inbound như sau:

| Loại | Giao thức | Cổng | Nguồn |
|---|---|---|---|
| MySQL/Aurora | TCP | 3306 | Security Group của EC2 |

Sử dụng Security Group của EC2 làm nguồn giúp giới hạn quyền truy cập cơ sở dữ liệu đối với EC2 được cấp phép, thay vì cho phép kết nối từ mọi địa chỉ IP.

#### 3. Kiểm tra kết nối đến cơ sở dữ liệu

Sau khi cấu hình Security Group, sử dụng EC2 instance để kiểm tra khả năng kết nối đến cơ sở dữ liệu RDS.

Bài kiểm tra xác định liệu EC2 có thể truy cập địa chỉ cơ sở dữ liệu thông qua cổng TCP 3306 hay không.

Lệnh kiểm tra ví dụ:

```bash
nc -zv <RDS-endpoint> 3306
```

Thay `<RDS-endpoint>` bằng endpoint hoặc địa chỉ cơ sở dữ liệu thực tế có thể truy cập.

Kết nối thành công cho thấy tuyến mạng và các quy tắc Security Group cho phép lưu lượng đi qua cổng MySQL.

#### 4. Kết quả kiểm tra

Trong quá trình triển khai, kết nối từ EC2 đến cơ sở dữ liệu RDS MySQL đã được kiểm tra thành công.

Kết quả kiểm tra hiển thị thông báo:

```text
Connected to 10.0.2.198:3306
```

Điều này xác nhận EC2 có thể thiết lập kết nối TCP đến cơ sở dữ liệu RDS thông qua cổng 3306.

**Lưu ý:** Bài kiểm tra này chỉ xác nhận khả năng kết nối mạng. Việc đọc, truy vấn hoặc xử lý dữ liệu ứng dụng từ cơ sở dữ liệu chưa được thực hiện trong bước này.

#### Kết luận

Trong phần này, quyền truy cập mạng giữa Amazon EC2 và Amazon RDS đã được cấu hình và kiểm tra thông qua Security Group.

Kết nối TCP thành công qua cổng 3306 xác nhận EC2 có thể truy cập cơ sở dữ liệu MySQL thông qua tuyến mạng đã cấu hình. Việc giới hạn quy tắc inbound của RDS theo Security Group của EC2 cũng góp phần giảm nguy cơ truy cập cơ sở dữ liệu trái phép.