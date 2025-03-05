+++
title = "Workshop: Triển Khai Website Blog Fullstack Trên AWS EC2 Với DocumentDB & CloudFront & S3"
date = 2025
weight = 1
chapter = false
+++

# Workshop: Triển Khai Website Blog Fullstack Trên AWS EC2 Với DocumentDB & CloudFront & S3

### Tổng quan

Trong workshop này, bạn sẽ học cách triển khai một Website Blog FullStack trên AWS, sử dụng EC2, sử dụng DocumentDB làm cơ sở dữ liệu IAM và CloudFront để tối ưu hiệu suất và tối ưu chi phí

![Workshop Architecture](/images/workshop_architecture.png)

### Mục tiêu:

- Hiểu cách tạo và cấu hình EC2, DocumentDB, CloudFront và IAM trên AWS.

- Biết cách triển khai ứng dụng full stack MERN Web Blog trên EC2.

- Kết nối và sử dụng DocumentDB từ EC2 và hiểu cách chuyển dữ liệu từ MongoDB lên DocumentDB.

- Hiểu cách cấu hình CloudFront để giảm tải EC2 và tối ưu hiệu suất.

- Quản lý quyền truy cập giữa các dịch vụ bằng AWS IAM.

### Yêu cầu:

- Tài khoản AWS với quyền truy cập IAM.

- Một máy tính với SSH client (như Terminal hoặc PuTTY).

### Nội dung

1. [Giới thiệu](1-Introduction/)
2. [Hạn chế quyền truy cập với IAM Service](2-restrict-access/)
3. [Khởi tạo VPC](3-create-vpc-instance/)
4. [Khởi tạo EC2 Instance](4-create-ec2-instance/)
5. [Khởi tạo S3](5-create-s3-bucket/)
6. [Khởi tạo DocumentDB](6-create-documentdb/)
7. [Triển khai ứng dụng lên EC2](7-deploy-the-application-to-ec2/)
8. [Khởi tạo CloudFront](8-create-cloudfront/)
9. [Dọn dẹp tài nguyên](9-clean-up/)
