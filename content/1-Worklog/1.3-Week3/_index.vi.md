---
title: "Nhật ký thực tập Tuần 3"
date: 2026-08-24
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

- Triển khai hạ tầng mạng cơ bản trên AWS dựa trên kiến trúc và kế hoạch phân bổ địa chỉ IP đã xây dựng trong Tuần 2.
- Tạo và cấu hình Amazon VPC với dải địa chỉ CIDR phù hợp cho đề tài bảo mật hạ tầng trên AWS.
- Tạo các public subnet và private subnet, tìm hiểu cách phân bổ tài nguyên mạng bên trong VPC.
- Cấu hình Internet Gateway và Route Table để kiểm soát hướng lưu lượng mạng.
- Kiểm tra cấu hình mạng nhằm chuẩn bị cho việc triển khai Amazon EC2 và các thành phần bảo mật trong những tuần tiếp theo.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Truy cập AWS Management Console và mở dịch vụ Amazon VPC.<br>- Tạo VPC cho đề tài bảo mật hạ tầng trên AWS.<br>- Cấu hình dải địa chỉ IPv4 CIDR theo kế hoạch đã xây dựng.<br>- Kiểm tra thông tin và trạng thái VPC sau khi tạo. | 24/08/2026 | 24/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Tạo public subnet và private subnet bên trong VPC theo kế hoạch phân bổ địa chỉ IP.<br>- Xác định dải CIDR và Availability Zone cho từng subnet.<br>- Tìm hiểu sự khác nhau giữa public subnet và private subnet.<br>- Cấu hình tự động gán địa chỉ IPv4 công khai cho public subnet khi cần thiết. | 25/08/2026 | 26/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Tạo Internet Gateway và gắn vào VPC.<br>- Tạo và cấu hình Route Table cho public subnet.<br>- Thêm tuyến mặc định `0.0.0.0/0` trỏ đến Internet Gateway.<br>- Liên kết Route Table với subnet tương ứng và kiểm tra các tuyến định tuyến đã cấu hình. | 27/08/2026 | 27/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Kiểm tra lại cấu hình VPC, subnet, Internet Gateway và Route Table.<br>- Kiểm tra dải CIDR, trạng thái liên kết subnet và các tuyến định tuyến.<br>- Đối chiếu cấu hình thực tế với sơ đồ kiến trúc và kế hoạch phân bổ địa chỉ IP.<br>- Tổng hợp kết quả triển khai để chuẩn bị cho Tuần 4. | 28/08/2026 | 28/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Kết quả Tuần 3:

- Đã tạo và cấu hình Amazon VPC cho đề tài bảo mật hạ tầng trên AWS.
- Cấu hình dải địa chỉ IPv4 CIDR của VPC theo kế hoạch thiết kế mạng.
- Tạo public subnet và private subnet nhằm tổ chức tài nguyên mạng và phân tách các thành phần hạ tầng.
- Hiểu được public subnet và private subnet được phân biệt dựa trên cấu hình định tuyến chứ không chỉ dựa vào tên gọi.
- Tạo Internet Gateway và gắn vào VPC để cung cấp khả năng kết nối Internet cho các tài nguyên phù hợp.
- Tạo và cấu hình Route Table với các tuyến định tuyến cần thiết:
  - Tuyến local cho phép các tài nguyên trong VPC giao tiếp với nhau theo cấu hình mạng.
  - Tuyến mặc định `0.0.0.0/0` trỏ đến Internet Gateway để định tuyến lưu lượng đi Internet từ public subnet.
- Liên kết Route Table với các subnet tương ứng và kiểm tra các tuyến định tuyến đã cấu hình.
- Đối chiếu cấu hình mạng AWS thực tế với sơ đồ kiến trúc và kế hoạch phân bổ địa chỉ IP đã xây dựng trong Tuần 2.
- Hoàn thành hạ tầng mạng VPC cơ bản, tạo nền tảng cho việc triển khai Amazon EC2 và các biện pháp bảo mật trong những tuần tiếp theo.