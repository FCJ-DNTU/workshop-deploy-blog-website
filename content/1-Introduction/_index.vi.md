+++
title = "Giới thiệu"
date = 2020-05-14T00:38:32+07:00
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

Trong workshop này, bạn sẽ học cách triển khai một Website Blog FullStack trên **AWS**, sử dụng **EC2**, sử dụng **DocumentDB** làm cơ sở dữ liệu **IAM** và **CloudFront** để tối ưu hiệu suất và tối ưu chi phí

![Workshop Architecture](/images/workshop_architecture.png)

### Mục tiêu:

- Hiểu cách tạo và cấu hình **EC2, DocumentDB, CloudFront và IAM trên AWS**.

- Triển khai Website Blog Fullstack trên EC2.

- Kết nối và sử dụng DocumentDB từ EC2

- Hiểu cách cấu hình CloudFront

### Yêu cầu:

- Tài khoản AWS với quyền truy cập IAM.

- Một máy tính với SSH client (như Terminal hoặc PuTTY).

### Luồng hoạt động:

**1. Client truy cập trang web**
- Người dùng truy cập trang blog thông qua trình duyệt.
- Dữ liệu tĩnh của frontend ReactJS được lưu trữ trên Amazon S3 và phân phối thông qua AWS CloudFront để tăng tốc độ tải trang.
- Xử lý yêu cầu từ Client

**2. CloudFront tiếp nhận request**
- CloudFront chuyển tiếp các yêu cầu API của client đến Internet Gateway, cho phép kết nối với máy chủ backend.
- Máy chủ Backend xử lý logic

**3. EC2 xử lý request**
- EC2 lấy dữ liệu từ Amazon DocumentDB (MongoDB) để phục vụ các API như lấy danh sách bài viết, người dùng, bình luận,...
Lưu trữ và quản lý dữ liệu

**4. Truy vấn dữ liệu từ Amazon DocumentDB**
- Cơ sở dữ liệu MongoDB được triển khai trên Amazon DocumentDB với hệ thống replica giữa Availability Zone 1 và Availability Zone 2 để đảm bảo tính khả dụng và độ bền dữ liệu.
- Phân quyền và bảo mật

**5. Trả kết quả về client**
- DocumentDB trả dữ liệu cho EC2.
- EC2 xử lý xong và trả kết quả về CloudFront.
- CloudFront có thể cache response để phục vụ nhanh hơn trong lần sau.
- Cuối cùng, response được gửi đến client.

**6. Quản lý quyền truy cập bằng IAM**
- IAM kiểm soát quyền truy cập cho user hoặc dịch vụ.
- IAM User thuộc một IAM Group và tuân theo các chính sách (Policies) để giới hạn quyền truy cập vào tài nguyên AWS như EC2, DocumentDB.