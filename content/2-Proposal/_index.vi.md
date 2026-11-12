---
title: "Đề xuất dự án"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS

## 1. Tóm tắt dự án

Dự án **Nghiên cứu và triển khai hệ thống bảo mật hạ tầng trên AWS** nhằm tìm hiểu và triển khai các cơ chế bảo mật cho hạ tầng điện toán đám mây sử dụng nền tảng Amazon Web Services (AWS).

Dự án tập trung vào việc thiết kế và triển khai môi trường mạng AWS an toàn bằng Amazon Virtual Private Cloud (VPC), các public subnet và private subnet, Internet Gateway và NAT Gateway. Các tài nguyên máy chủ và cơ sở dữ liệu được triển khai bằng Amazon EC2 và Amazon RDS. Application Load Balancer (ALB) được sử dụng làm điểm tiếp nhận lưu lượng truy cập đến ứng dụng web.

Để tăng cường bảo mật hạ tầng, dự án áp dụng các cơ chế quản lý danh tính và quyền truy cập IAM, Security Groups, AWS Web Application Firewall (AWS WAF) và các cấu hình kiểm soát truy cập mạng. Hoạt động giám sát và kiểm tra được hỗ trợ bởi Amazon CloudWatch, AWS CloudTrail và AWS Config.

Quá trình triển khai được thực hiện trong môi trường thực hành trên AWS. Dự án tập trung đánh giá khả năng kết nối mạng, quyền truy cập, khả năng lọc yêu cầu web, giám sát tài nguyên và đánh giá mức độ tuân thủ cấu hình. Kết quả hướng tới là một mô hình hạ tầng AWS có nhiều lớp bảo mật cùng các minh chứng kiểm thử cụ thể.

## 2. Phát biểu vấn đề

### Những thách thức hiện tại

Hạ tầng điện toán đám mây cung cấp các tài nguyên linh hoạt về tính toán, lưu trữ và mạng. Tuy nhiên, nếu các tài nguyên được triển khai mà không có cấu hình bảo mật phù hợp, hệ thống có thể đối mặt với nguy cơ truy cập trái phép, lưu lượng mạng không cần thiết và các rủi ro do cấu hình sai.

Một số vấn đề thường gặp bao gồm:

- Công khai các tài nguyên vốn chỉ nên được truy cập thông qua mạng riêng.
- Cấu hình quy tắc lưu lượng vào và ra quá rộng.
- Cấp quyền không cần thiết cho người dùng, nhóm hoặc vai trò dịch vụ.
- Thiếu khả năng theo dõi hoạt động của tài nguyên và hiệu năng hệ thống.
- Khó phát hiện các vấn đề cấu hình và đánh giá mức độ tuân thủ bảo mật.
- Phát sinh chi phí ngoài dự kiến khi các tài nguyên đám mây vẫn hoạt động dù không còn được sử dụng.

Những vấn đề này cho thấy sự cần thiết của một quy trình có hệ thống để thiết kế, triển khai, giám sát và đánh giá bảo mật hạ tầng đám mây.

### Giải pháp đề xuất

Dự án xây dựng kiến trúc bảo mật nhiều lớp trên AWS. Giải pháp bao gồm các thành phần sau:

- **Hạ tầng mạng:** Amazon VPC cung cấp môi trường mạng riêng biệt với các public subnet và private subnet. Internet Gateway và NAT Gateway hỗ trợ kết nối mạng có kiểm soát.
- **Tài nguyên máy chủ:** Amazon EC2 triển khai máy chủ web và cung cấp môi trường thực hành kiểm thử truy cập, cấu hình bảo mật hạ tầng.
- **Tài nguyên cơ sở dữ liệu:** Amazon RDS cung cấp dịch vụ cơ sở dữ liệu được quản lý, triển khai trong các private subnet. Quyền truy cập được giới hạn đối với các tài nguyên được cho phép.
- **Cân bằng tải:** Application Load Balancer tiếp nhận và phân phối các yêu cầu HTTP đến EC2, đồng thời cung cấp điểm truy cập có kiểm soát cho ứng dụng.
- **Kiểm soát truy cập:** IAM quản lý danh tính và quyền truy cập, trong khi Security Groups kiểm soát lưu lượng giữa ALB, EC2 và RDS.
- **Bảo vệ ứng dụng web:** AWS WAF lọc các yêu cầu truy cập dựa trên những quy tắc được cấu hình trong Web ACL.
- **Giám sát và kiểm tra:** CloudWatch giám sát các chỉ số tài nguyên có sẵn, CloudTrail ghi nhận hoạt động tài khoản và các sự kiện API, AWS Config đánh giá cấu hình tài nguyên theo các quy tắc được lựa chọn.
- **Kiểm thử bảo mật:** Thực hiện kiểm tra kết nối, quyền truy cập và khả năng lọc yêu cầu web để đánh giá các cơ chế bảo mật đã triển khai.

Dự án được thực hiện trong môi trường phòng thí nghiệm nhằm minh họa cách các dịch vụ AWS phối hợp với nhau để bảo vệ hạ tầng đám mây.

### Lợi ích và hiệu quả đầu tư (ROI)

Dự án kỳ vọng mang lại những lợi ích sau:

- Tăng cường phân tách mạng bằng cách tách biệt tài nguyên công khai và tài nguyên riêng tư.
- Hạn chế quyền truy cập vào tài nguyên đám mây thông qua IAM và các quy tắc Security Group.
- Bổ sung lớp bảo vệ ứng dụng web bằng AWS WAF.
- Nâng cao khả năng theo dõi hiệu năng tài nguyên và hoạt động tài khoản thông qua các dịch vụ giám sát, kiểm tra.
- Hỗ trợ đánh giá cấu hình và phát hiện các vấn đề bảo mật tiềm ẩn.
- Cung cấp kinh nghiệm thực hành về mạng đám mây, triển khai hạ tầng và quản lý bảo mật.
- Xây dựng nền tảng có thể mở rộng bằng cách tích hợp thêm các dịch vụ bảo mật khác.

Do đây là dự án nghiên cứu và triển khai thực hành phục vụ học tập, hiệu quả của dự án sẽ được đánh giá thông qua kết quả kỹ thuật, kiểm thử bảo mật, quản lý tài nguyên và chi phí vận hành thay vì giả định một thời gian hoàn vốn tài chính cố định.

## 3. Kiến trúc giải pháp

Hệ thống sử dụng kiến trúc bảo mật hạ tầng AWS nhiều lớp. Amazon VPC cung cấp môi trường mạng chính, được chia thành các public subnet và private subnet tùy theo chức năng tài nguyên và yêu cầu truy cập.

Các public subnet chứa Application Load Balancer và những thành phần mạng cần khả năng kết nối công khai. Private subnet được sử dụng cho các tài nguyên phía sau như EC2 và cơ sở dữ liệu RDS theo thiết kế mạng đã triển khai.

Luồng truy cập chính của hệ thống như sau:

1. Người dùng gửi yêu cầu HTTP đến địa chỉ DNS của Application Load Balancer.
2. ALB chuyển tiếp các yêu cầu được phép đến EC2 đã đăng ký trong Target Group.
3. AWS WAF kiểm tra các yêu cầu web gắn với ALB và áp dụng các quy tắc trong Web ACL đã cấu hình.
4. EC2 vận hành máy chủ web và giao tiếp với cơ sở dữ liệu RDS thông qua cổng cơ sở dữ liệu được cho phép.
5. Security Groups kiểm soát lưu lượng giữa ALB, EC2 và RDS.
6. IAM Role và IAM Policy kiểm soát quyền truy cập vào các dịch vụ và tài nguyên AWS.
7. CloudWatch cung cấp thông tin giám sát, CloudTrail ghi nhận hoạt động tài khoản và AWS Config đánh giá cấu hình tài nguyên.

### Các dịch vụ và công nghệ AWS

- **Amazon VPC:** Cung cấp môi trường mạng ảo riêng biệt cho các tài nguyên AWS.
- **Public Subnet và Private Subnet:** Phân tách tài nguyên theo mức độ công khai và yêu cầu truy cập.
- **Internet Gateway:** Cung cấp kết nối Internet cho các tài nguyên được định tuyến qua public subnet.
- **NAT Gateway:** Cho phép tài nguyên trong private subnet chủ động kết nối ra Internet mà không cần cho phép kết nối trực tiếp từ Internet vào.
- **Amazon EC2:** Cung cấp máy chủ ảo để triển khai máy chủ web và thực hiện kiểm thử bảo mật hạ tầng.
- **Amazon RDS:** Cung cấp dịch vụ cơ sở dữ liệu quan hệ được quản lý trong môi trường mạng riêng.
- **Application Load Balancer:** Tiếp nhận và phân phối lưu lượng ứng dụng đến các máy chủ đích đã đăng ký.
- **AWS IAM:** Quản lý người dùng, vai trò, chính sách và quyền truy cập theo nguyên tắc đặc quyền tối thiểu.
- **Security Groups:** Đóng vai trò như tường lửa ảo, kiểm soát lưu lượng vào và ra của các tài nguyên được hỗ trợ.
- **AWS WAF:** Kiểm tra yêu cầu web và áp dụng các quy tắc lọc thông qua Web ACL.
- **Amazon CloudWatch:** Cung cấp khả năng giám sát chỉ số và quản lý log cho các dịch vụ AWS được hỗ trợ.
- **AWS CloudTrail:** Ghi nhận hoạt động tài khoản và các sự kiện gọi API phục vụ kiểm tra.
- **AWS Config:** Ghi nhận cấu hình tài nguyên và đánh giá chúng theo các quy tắc tuân thủ được lựa chọn.

### Thiết kế các thành phần

**Hạ tầng mạng**

Amazon VPC được cấu hình với dải địa chỉ CIDR và chia thành các public subnet, private subnet. Route Table xác định đường đi của lưu lượng giữa các subnet, Internet Gateway và NAT Gateway. Cấu trúc này hỗ trợ phân tách mạng và kiểm soát kết nối.

**Lớp máy chủ và cơ sở dữ liệu**

Amazon EC2 triển khai máy chủ web trong môi trường mạng AWS. Amazon RDS cung cấp dịch vụ cơ sở dữ liệu trong các private subnet. Việc giao tiếp giữa EC2 và RDS được giới hạn thông qua các quy tắc Security Group và cổng cơ sở dữ liệu cần thiết.

**Lớp truy cập ứng dụng**

Application Load Balancer cung cấp điểm tiếp nhận lưu lượng web và chuyển tiếp yêu cầu đến các máy chủ đích có trạng thái hoạt động tốt. AWS WAF được liên kết với ALB để kiểm tra và lọc yêu cầu truy cập dựa trên các quy tắc đã cấu hình.

**Lớp quản lý danh tính và quyền truy cập**

IAM User, IAM Role và IAM Policy xác định danh tính hoặc dịch vụ AWS nào được phép truy cập vào từng tài nguyên cụ thể. Quyền truy cập được thiết kế theo nguyên tắc đặc quyền tối thiểu.

**Lớp giám sát và kiểm tra**

CloudWatch cung cấp khả năng theo dõi các chỉ số tài nguyên và thông tin giám sát có sẵn. CloudTrail ghi nhận hoạt động tài khoản và các lệnh gọi API. AWS Config ghi nhận cấu hình tài nguyên và đánh giá các quy tắc bảo mật được lựa chọn.

**Lớp bảo mật**

Kiến trúc bảo mật kết hợp phân tách mạng, Security Groups, quyền IAM và AWS WAF. Các cơ chế này phối hợp nhằm giảm thiểu việc công khai tài nguyên không cần thiết và giới hạn quyền truy cập đối với lưu lượng, danh tính được cho phép.

## 4. Triển khai kỹ thuật

### Các giai đoạn triển khai

Dự án được chia thành bốn giai đoạn chính.

**Giai đoạn 1: Nghiên cứu và thiết kế kiến trúc**

- Tìm hiểu hạ tầng điện toán đám mây AWS và mô hình trách nhiệm chia sẻ.
- Nghiên cứu VPC, chia subnet, định tuyến và các cơ chế bảo mật mạng trên AWS.
- Xác định yêu cầu bảo mật đối với máy chủ, cơ sở dữ liệu và truy cập ứng dụng.
- Thiết kế kiến trúc mạng, kế hoạch địa chỉ CIDR và vị trí triển khai tài nguyên.
- Lựa chọn các dịch vụ AWS phù hợp để kiểm soát truy cập, giám sát và kiểm tra.

**Giai đoạn 2: Triển khai mạng và tài nguyên AWS**

- Tạo Amazon VPC với dải địa chỉ CIDR phù hợp.
- Tạo public subnet và private subnet trên các Availability Zone.
- Cấu hình Internet Gateway, NAT Gateway và Route Table.
- Triển khai EC2 và cấu hình phương thức truy cập quản trị an toàn.
- Tạo cơ sở dữ liệu RDS và cấu hình DB Subnet Group.
- Cấu hình Security Groups để kiểm soát giao tiếp giữa các tài nguyên.
- Triển khai Application Load Balancer và kiểm tra trạng thái của Target Group.

**Giai đoạn 3: Cấu hình bảo mật và giám sát**

- Cấu hình IAM Role và IAM Policy phù hợp với quyền truy cập của tài nguyên.
- Rà soát các quy tắc Security Group và hạn chế lưu lượng không cần thiết.
- Tạo AWS WAF Web ACL và liên kết với Application Load Balancer.
- Cấu hình và kiểm tra các bản ghi hoạt động của CloudTrail.
- Sử dụng CloudWatch để theo dõi các chỉ số tài nguyên và thông tin giám sát có sẵn.
- Kiểm tra trạng thái ghi nhận của AWS Config và các quy tắc đánh giá tuân thủ được lựa chọn.

**Giai đoạn 4: Kiểm thử, đánh giá và hoàn thiện tài liệu**

- Kiểm tra kết nối mạng giữa EC2 và cơ sở dữ liệu RDS.
- Kiểm tra khả năng truy cập máy chủ web thông qua DNS của ALB.
- Kiểm thử lưu lượng được phép và bị hạn chế theo các quy tắc Security Group.
- Thực hiện các yêu cầu web có kiểm soát để đánh giá hoạt động của AWS WAF.
- Kiểm tra chỉ số CloudWatch, bản ghi CloudTrail và kết quả AWS Config.
- Đánh giá mức sử dụng tài nguyên và xác định các cơ hội tối ưu chi phí.
- Hoàn thiện sơ đồ kiến trúc, mô tả cấu hình, ảnh chụp màn hình và báo cáo kiểm thử.

### Yêu cầu kỹ thuật

**Hạ tầng mạng**

- Sử dụng Amazon VPC để tạo môi trường mạng riêng biệt.
- Phân chia mạng thành các public subnet và private subnet.
- Cấu hình Route Table, Internet Gateway và NAT Gateway theo thiết kế mạng.
- Thiết lập định tuyến và liên kết subnet phù hợp.
- Hạn chế lưu lượng không cần thiết giữa các thành phần mạng.

**Hạ tầng máy chủ và cơ sở dữ liệu**

- Triển khai EC2 với Amazon Machine Image phù hợp.
- Cấu hình phương thức truy cập quản trị an toàn, ưu tiên sử dụng AWS Systems Manager Session Manager khi phù hợp.
- Triển khai cơ sở dữ liệu RDS trong các private subnet.
- Cấu hình Security Group của cơ sở dữ liệu chỉ cho phép kết nối từ các tài nguyên được ủy quyền.
- Kiểm tra khả năng kết nối thông qua cổng cơ sở dữ liệu cần thiết, không mặc định rằng ứng dụng đã thực hiện truy vấn dữ liệu thành công.

**Ứng dụng và bảo vệ web**

- Triển khai máy chủ web trên EC2.
- Cấu hình Application Load Balancer và Target Group.
- Kiểm tra trạng thái hoạt động của target và khả năng truy cập ứng dụng qua DNS của ALB.
- Liên kết AWS WAF với ALB và cấu hình các quy tắc Web ACL phù hợp.
- Kiểm thử các yêu cầu thông thường và các yêu cầu có dấu hiệu đáng ngờ trong môi trường có kiểm soát để đánh giá khả năng lọc.

**Giám sát và kiểm tra**

- Sử dụng CloudWatch để theo dõi các chỉ số và thông tin giám sát tài nguyên được hỗ trợ.
- Sử dụng CloudTrail để kiểm tra hoạt động tài khoản và các sự kiện API.
- Sử dụng AWS Config để ghi nhận cấu hình tài nguyên và đánh giá các quy tắc được lựa chọn.
- Kiểm tra các log và kết quả giám sát có sẵn để phục vụ phân tích bảo mật.

**Quản lý bảo mật**

- Áp dụng quyền IAM theo nguyên tắc đặc quyền tối thiểu.
- Cấu hình Security Groups chỉ cho phép lưu lượng cần thiết.
- Đặt tài nguyên cơ sở dữ liệu trong private subnet.
- Tránh công khai không cần thiết các giao diện quản trị và giám sát.
- Thường xuyên rà soát cấu hình bảo mật và ghi nhận kết quả kiểm thử.

## 5. Tiến độ triển khai và các mốc công việc

Dự án được thực hiện theo các mốc công việc trong giai đoạn thực tập và triển khai từ tháng 8 đến tháng 12 năm 2026.

- **Giai đoạn 1 – Nghiên cứu và thiết kế:** Tìm hiểu các dịch vụ AWS, nguyên tắc bảo mật hạ tầng, kiến trúc mạng và kế hoạch địa chỉ IP.
- **Giai đoạn 2 – Triển khai mạng:** Tạo VPC, public subnet, private subnet, Internet Gateway, NAT Gateway và Route Table.
- **Giai đoạn 3 – Triển khai máy chủ và cơ sở dữ liệu:** Triển khai EC2, RDS, cấu hình Security Groups và kiểm tra kết nối cơ sở dữ liệu.
- **Giai đoạn 4 – Triển khai truy cập ứng dụng:** Cấu hình máy chủ web, Application Load Balancer, Target Group và kiểm tra truy cập ứng dụng.
- **Giai đoạn 5 – Bảo mật và giám sát:** Cấu hình IAM, AWS WAF, CloudTrail, CloudWatch và AWS Config.
- **Giai đoạn 6 – Kiểm thử và hoàn thiện:** Thực hiện kiểm tra kết nối, kiểm thử bảo mật, rà soát kết quả giám sát, đánh giá chi phí và hoàn thiện tài liệu dự án.

Trong tương lai, dự án có thể được mở rộng thông qua việc tích hợp thêm các dịch vụ bảo mật, tự động hóa quản lý cấu hình, nâng cao khả năng giám sát và thực hiện các bài kiểm thử bảo mật chuyên sâu hơn.

## 6. Dự toán kinh phí

Chi phí của dự án phụ thuộc vào các tài nguyên AWS được sử dụng, cấu hình dịch vụ, thời gian hoạt động, dung lượng lưu trữ, lưu lượng truyền dữ liệu và các tính năng được lựa chọn.

Có thể sử dụng [AWS Pricing Calculator](https://calculator.aws/) để ước tính chi phí dựa trên cấu hình hạ tầng dự kiến.

### Các thành phần chi phí

- **Amazon EC2:** Chi phí phụ thuộc vào loại instance, hệ điều hành và thời gian hoạt động.
- **Amazon EBS:** Chi phí lưu trữ phụ thuộc vào loại volume, dung lượng được cấp phát và mức sử dụng.
- **Amazon RDS:** Chi phí phụ thuộc vào loại instance cơ sở dữ liệu, dung lượng lưu trữ, cấu hình sao lưu và thời gian hoạt động.
- **NAT Gateway:** Có thể phát sinh phí theo thời gian hoạt động và lượng dữ liệu được xử lý.
- **Application Load Balancer:** Chi phí phụ thuộc vào thời gian hoạt động và các đơn vị dung lượng được tính phí.
- **AWS WAF:** Chi phí có thể phụ thuộc vào số lượng Web ACL, quy tắc và yêu cầu web được xử lý.
- **Amazon CloudWatch:** Có thể phát sinh chi phí đối với metric, log, alarm và các tính năng vượt mức sử dụng miễn phí áp dụng.
- **AWS CloudTrail và AWS Config:** Chi phí phụ thuộc vào các tính năng ghi nhận sự kiện, cấu hình, phân phối dữ liệu và đánh giá được lựa chọn.
- **Truyền dữ liệu:** Có thể phát sinh chi phí tùy thuộc vào loại và lượng dữ liệu truyền tải.

### Các biện pháp tối ưu chi phí

- Chỉ khởi chạy EC2 khi cần cấu hình, kiểm thử hoặc trình diễn.
- Rà soát việc sử dụng RDS và dừng hoặc xóa tài nguyên khi phù hợp và được phép.
- Giải phóng Elastic IP không sử dụng và loại bỏ các tài nguyên mạng không cần thiết sau khi kiểm tra các thành phần phụ thuộc.
- Theo dõi việc sử dụng NAT Gateway và ALB vì các tài nguyên này có thể phát sinh chi phí trong thời gian hoạt động.
- Lựa chọn cấu hình tài nguyên phù hợp với khối lượng công việc thực tế.
- Theo dõi AWS Billing và thiết lập cảnh báo ngân sách.
- Thu thập đầy đủ ảnh chụp màn hình, log và minh chứng dự án trước khi dừng hoặc xóa tài nguyên.
- Kiểm tra các thành phần phụ thuộc trước khi giải phóng tài nguyên để tránh làm gián đoạn hệ thống.

Việc đánh giá chi phí cuối cùng cần dựa trên dữ liệu thanh toán thực tế và AWS Pricing Calculator. Không nên mặc định chi phí bằng không chỉ vì tài nguyên nằm trong phạm vi ưu đãi miễn phí hoặc được cấp credit khuyến mãi.

## 7. Đánh giá rủi ro

### Ma trận rủi ro

- **Truy cập trái phép:** Mức độ ảnh hưởng cao nếu quyền IAM hoặc quy tắc truy cập mạng được cấu hình quá rộng.
- **Sai cấu hình mạng:** Mức độ ảnh hưởng cao nếu liên kết subnet, Route Table hoặc tuyến đến Gateway không chính xác.
- **Lộ cơ sở dữ liệu:** Mức độ ảnh hưởng cao nếu RDS có thể được truy cập từ các mạng không được ủy quyền.
- **Tấn công ứng dụng web:** Mức độ ảnh hưởng trung bình đến cao nếu các yêu cầu truy cập không được kiểm tra và lọc phù hợp.
- **Thiếu thông tin giám sát:** Mức độ ảnh hưởng trung bình nếu hoạt động tài nguyên hoặc sự kiện bảo mật không được ghi nhận đầy đủ.
- **Phát sinh chi phí AWS ngoài dự kiến:** Mức độ ảnh hưởng trung bình đến cao nếu các tài nguyên tính phí vẫn hoạt động lâu hơn cần thiết.
- **Không tuân thủ cấu hình:** Mức độ ảnh hưởng trung bình nếu tài nguyên AWS không đáp ứng các quy tắc bảo mật đã lựa chọn.

### Các biện pháp giảm thiểu rủi ro

- **Kiểm soát truy cập:** Áp dụng IAM Policy theo nguyên tắc đặc quyền tối thiểu và thường xuyên rà soát quyền.
- **Bảo mật mạng:** Phân tách tài nguyên công khai và riêng tư, giới hạn quy tắc Security Group và kiểm tra cấu hình Route Table.
- **Bảo mật cơ sở dữ liệu:** Đặt RDS trong private subnet và chỉ cho phép kết nối cơ sở dữ liệu từ các tài nguyên được ủy quyền.
- **Bảo vệ ứng dụng web:** Liên kết AWS WAF với ALB và kiểm thử các quy tắc lọc đã cấu hình.
- **Giám sát và kiểm tra:** Kiểm tra metric CloudWatch, bản ghi CloudTrail và kết quả tuân thủ của AWS Config.
- **Quản lý chi phí:** Theo dõi thanh toán, thiết lập cảnh báo ngân sách và dừng hoặc giải phóng các tài nguyên không cần thiết sau khi thu thập đủ minh chứng.
- **Quản lý cấu hình:** Ghi chép cấu hình hạ tầng và rà soát các thay đổi để hạn chế lỗi cấu hình.

### Kế hoạch dự phòng

Nếu ứng dụng web không thể truy cập, cần kiểm tra trạng thái EC2, dịch vụ web, ALB Listener, tình trạng hoạt động của Target Group và các quy tắc Security Group.

Nếu EC2 không thể kết nối đến RDS, cần kiểm tra trạng thái cơ sở dữ liệu, định tuyến subnet, quy tắc nguồn của Security Group, cổng cơ sở dữ liệu và cấu hình kết nối.

Nếu các yêu cầu truy cập không hợp lệ vẫn được cho phép hoặc yêu cầu hợp lệ bị chặn, cần xem xét các quy tắc Web ACL của AWS WAF, thứ tự ưu tiên và số liệu yêu cầu. Chỉ điều chỉnh cấu hình sau khi xác định được nguyên nhân.

Nếu không có thông tin giám sát, cần kiểm tra cấu hình dịch vụ, quyền truy cập tài nguyên, trạng thái ghi nhận và khả năng cung cấp metric hoặc log liên quan.

Trước khi dừng hoặc xóa bất kỳ tài nguyên nào trong quá trình dọn dẹp, cần lưu lại ảnh chụp màn hình và minh chứng kiểm thử cần thiết cho báo cáo, cũng như phần trình diễn dự án.

## 8. Kết quả dự kiến

### Kết quả kỹ thuật

- Xây dựng môi trường hạ tầng AWS có phân tách mạng công khai và mạng riêng.
- Triển khai EC2 và RDS với cơ chế kiểm soát truy cập mạng.
- Cấu hình Application Load Balancer để cung cấp khả năng truy cập ứng dụng web.
- Áp dụng IAM Role và IAM Policy theo nguyên tắc đặc quyền tối thiểu.
- Sử dụng Security Groups để kiểm soát lưu lượng giữa các thành phần hạ tầng.
- Tích hợp AWS WAF với ALB để kiểm tra và lọc các yêu cầu truy cập web.
- Sử dụng CloudWatch, CloudTrail và AWS Config để hỗ trợ giám sát, kiểm tra và đánh giá cấu hình.
- Thực hiện các bài kiểm tra kết nối, kiểm thử bảo mật và ghi nhận kết quả.

### Giá trị lâu dài

Dự án cung cấp nền tảng thực hành để tìm hiểu về bảo mật hạ tầng AWS, mạng đám mây, kiểm soát truy cập và giám sát hệ thống.

Kiến trúc có thể được mở rộng bằng cách tích hợp thêm các dịch vụ bảo mật, tự động hóa triển khai, phân tích log tập trung, thiết lập cảnh báo nâng cao và thực hiện các bài kiểm thử bảo mật toàn diện hơn.

Thông qua dự án, người thực hiện có thể vận dụng kiến thức mạng máy tính vào môi trường điện toán đám mây AWS, đồng thời tích lũy kinh nghiệm thực tế về triển khai hạ tầng, quản lý tài nguyên, cấu hình bảo mật và viết tài liệu kỹ thuật.

Kết quả cuối cùng được đánh giá dựa trên khả năng kết nối mạng, tính sẵn sàng của dịch vụ, hiệu quả kiểm soát truy cập, khả năng lọc yêu cầu web, thông tin giám sát, kết quả đánh giá cấu hình và chi phí sử dụng tài nguyên.