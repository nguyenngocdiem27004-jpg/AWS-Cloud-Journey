---
title: "Nhật ký thực tập Tuần 7"
date: 2026-09-26
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

- Tìm hiểu quy trình triển khai máy chủ web trên Amazon EC2.
- Cài đặt và cấu hình Nginx trên máy chủ Ubuntu Server.
- Cấu hình Security Group để kiểm soát lưu lượng HTTP giữa Application Load Balancer và EC2 Instance.
- Cấu hình Application Load Balancer để chuyển tiếp các yêu cầu HTTP đến máy chủ web.
- Kiểm tra khả năng truy cập website thông qua DNS name của Application Load Balancer.
- Chuẩn bị môi trường máy chủ web cho việc triển khai các dịch vụ bảo mật và giám sát trong những tuần tiếp theo.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Kiểm tra trạng thái EC2 Instance và cấu hình mạng đã triển khai trong các tuần trước.<br>- Kiểm tra hệ điều hành, địa chỉ IP private và cấu hình Security Group của máy chủ.<br>- Tìm hiểu về Nginx và vai trò của máy chủ web trong hạ tầng AWS.<br>- Chuẩn bị môi trường EC2 để cài đặt dịch vụ web. | 26/09/2026 | 26/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Cập nhật danh sách các gói phần mềm trên Ubuntu Server.<br>- Cài đặt Nginx trên EC2 Instance.<br>- Kiểm tra trạng thái dịch vụ Nginx và cấu hình để dịch vụ tự động khởi động cùng hệ thống.<br>- Kiểm tra dịch vụ web đang lắng nghe trên cổng cần thiết. | 27/09/2026 | 28/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Kiểm tra và cấu hình các quy tắc Security Group cho máy chủ web.<br>- Cho phép lưu lượng HTTP qua TCP port 80 từ Security Group của Application Load Balancer.<br>- Kiểm tra các quy tắc giao tiếp giữa ALB và EC2 Instance.<br>- Cấu hình Listener và Target Group của ALB để chuyển tiếp yêu cầu HTTP đến EC2 Instance.<br>- Kiểm tra trạng thái hoạt động của Target Group. | 29/09/2026 | 30/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Truy cập máy chủ web thông qua DNS name của Application Load Balancer.<br>- Kiểm tra trạng thái dịch vụ Nginx và xử lý lỗi truy cập nếu có.<br>- Xác minh cấu hình Listener, Target Group, Health Check và Security Group của ALB.<br>- Ghi nhận kết quả kiểm tra truy cập website và chuẩn bị triển khai các dịch vụ bảo mật, giám sát trong Tuần 8. | 01/10/2026 | 02/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Kết quả Tuần 7:

- Nắm được quy trình triển khai máy chủ web trên Amazon EC2.
- Đã cài đặt Nginx trên máy chủ Ubuntu Server.
- Kiểm tra trạng thái dịch vụ Nginx và xác nhận dịch vụ web đang hoạt động.
- Cấu hình Security Group để cho phép lưu lượng HTTP từ Application Load Balancer đến EC2 Instance.
- Tìm hiểu cách cấu hình Listener và Target Group của ALB để phân phối các yêu cầu HTTP.
- Kiểm tra trạng thái hoạt động của Target Group và xác nhận EC2 Instance ở trạng thái Healthy.
- Truy cập thành công trang mặc định Welcome to nginx thông qua DNS name của Application Load Balancer.
- Hoàn thành môi trường máy chủ web, tạo nền tảng cho việc triển khai các dịch vụ bảo mật và giám sát trong những tuần tiếp theo.