---
title: "Nhật ký thực tập Tuần 5"
date: 2026-09-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

- Kiểm tra và hoàn thiện kiến trúc mạng AWS VPC đã triển khai trong các tuần trước.
- Tìm hiểu vai trò của public subnet và private subnet trong việc phân tách các tài nguyên hạ tầng AWS.
- Tìm hiểu về NAT Gateway và vai trò của dịch vụ trong việc cung cấp kết nối Internet chiều ra cho các tài nguyên trong private subnet.
- Cấu hình Route Table để kiểm soát lưu lượng giữa public subnet, private subnet và mạng bên ngoài.
- Kiểm tra lại các quy tắc Security Group nhằm kiểm soát kết nối giữa EC2 Instance và các tài nguyên AWS khác.
- Kiểm tra khả năng kết nối mạng và chuẩn bị hạ tầng cho việc triển khai các dịch vụ bảo mật tiếp theo.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Kiểm tra lại kiến trúc VPC và cấu hình subnet hiện có.<br>- Tìm hiểu sự khác nhau giữa public subnet và private subnet.<br>- Ôn tập vai trò của Internet Gateway và NAT Gateway trong kiến trúc mạng AWS.<br>- Xác định yêu cầu lưu lượng mạng đối với các tài nguyên được triển khai trong từng subnet. | 12/09/2026 | 12/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Tạo và cấu hình NAT Gateway trong public subnet.<br>- Cấp phát địa chỉ Elastic IP cho NAT Gateway.<br>- Kiểm tra cấu hình Route Table của private subnet.<br>- Thêm tuyến mặc định `0.0.0.0/0` trỏ đến NAT Gateway khi cần thiết. | 13/09/2026 | 14/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Kiểm tra các Route Table được liên kết với public subnet và private subnet.<br>- Xác minh hướng định tuyến lưu lượng thông qua Internet Gateway và NAT Gateway.<br>- Kiểm tra các quy tắc Security Group của EC2 Instance và những tài nguyên liên quan.<br>- Tìm hiểu cách Security Group kiểm soát kết nối giữa các thành phần khác nhau trong hạ tầng. | 15/09/2026 | 16/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Kiểm tra cấu hình VPC, subnet, NAT Gateway và Route Table.<br>- Xác minh khả năng kết nối mạng cần thiết của EC2 Instance.<br>- Kiểm tra việc phân tách mạng giữa các tài nguyên public và private.<br>- Tổng hợp kết quả triển khai mạng và chuẩn bị cho giai đoạn tiếp theo của đề tài bảo mật hạ tầng. | 17/09/2026 | 18/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Kết quả Tuần 5:

- Đã kiểm tra lại kiến trúc AWS VPC và cấu hình mạng được triển khai trong các tuần trước.
- Hiểu được vai trò của public subnet và private subnet trong việc phân tách các tài nguyên hạ tầng.
- Tìm hiểu về NAT Gateway và chức năng cho phép tài nguyên trong private subnet truy cập Internet chiều ra mà không cần cho phép kết nối trực tiếp từ Internet vào.
- Đã cấu hình NAT Gateway và liên kết địa chỉ Elastic IP với dịch vụ.
- Cấu hình Route Table của private subnet với tuyến định tuyến phù hợp trỏ đến NAT Gateway.
- Kiểm tra Route Table của public subnet và private subnet, xác minh các cấu hình định tuyến.
- Kiểm tra các quy tắc Security Group nhằm kiểm soát lưu lượng mạng giữa EC2 và những tài nguyên AWS khác.
- Nâng cao hiểu biết về phân tách mạng và kiểm soát lưu lượng bên trong AWS VPC.
- Hoàn thiện cấu hình mạng cơ bản, tạo nền tảng cho các giai đoạn tiếp theo của việc triển khai và bảo mật hạ tầng AWS.