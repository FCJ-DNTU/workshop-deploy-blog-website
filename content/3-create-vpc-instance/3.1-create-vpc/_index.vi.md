---
title: "Khởi tạo VPC Instance"
date: 2025
weight: 1
chapter: false
pre: "<b>3.1. </b>"
---

#### Khái niệm về VPC

Trong bài Workshop này, *Amazon Virtual Private Cloud (VPC)* được sử dụng để tạo một mạng riêng ảo (private network), cho phép tổ chức và quản lý các tài nguyên trong một không gian mạng riêng biệt trên AWS.

VPC giúp bạn kiểm soát hoàn toàn môi trường mạng của mình, từ cấu hình địa chỉ IP, bảng định tuyến (route table), cổng internet (Internet Gateway) cho đến các mạng con (subnet).

#### Các trường hợp sử dụng chính của VPC trong Workshop

Trong Workshop này, chúng ta sẽ khởi tạo VPC Instance bao gồm:

- 2 Availability Zones (AZs) để đảm bảo tính sẵn sàng cao.

- 2 Public Subnets (dành cho EC2 chạy ứng dụng).

- 2 Private Subnets (dành cho Amazon DocumentDB).

- Internet Gateway (IGW) để EC2 có thể giao tiếp với Internet.

- Security Group để quản lý quyền truy cập an toàn.

![use-case-vpc](/images/3-create-vpc-instance/3.1-create-vpc/use-case-vpc.png)

#### Chi phí cho VPC

Sẽ không phát sinh chi phí khi sử dụng VPC. Tuy nhiên, sẽ có phí dịch vụ cho những **dịch vụ của VPC**, ví dụ NAT Gateways, IP Address Manager, traffic mirroring, Reachability Analyzer, và Network Access Analyzer.

#### Khởi tạo VPC Instance

Ở section này chúng ta sẽ khởi tạo **VPC Instance**, bao gồm 2 **AZ**, 2 Public Subnets, 2 Private Subnets

#### 1. Tạo VPC Instance 
- Truy cập [Your VPCs](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#vpcs:), Create VPC
- Tại **VPC Settings**, chọn option **VPC and more**

![create-vpc](/images/3-create-vpc-instance/3.1-create-vpc/create-vpc.png)
- Đặt tên **name tag** và để mặc định các field khác, chọn **Create VPC**
![create-vpc-done](/images/3-create-vpc-instance/3.1-create-vpc/create-vpc-done.png)
- Kết quả tạo VPC Instance thành công
![review-result](/images/3-create-vpc-instance/3.1-create-vpc/review-result.png)

#### 2. Tiếp theo chúng ta sẽ gán Public IP4 cho các public subnet
- Truy cập [Subnets](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#subnets:)
- Chọn **Subnet ID** của public subnet e.g. **deploy-fullstack-blog-workshop-subnet-public1-ap-southeast-1a**
![subnets](/images/3-create-vpc-instance/3.1-create-vpc/subnets.png)
- Chọn dropdown **Actions**, **Edit subnet settings**
![edit-subnet](/images/3-create-vpc-instance/3.1-create-vpc/edit-subnet.png)
- Tích vào **Enable auto-assign public IPv4 address**, Save
![enable-ipv4](/images/3-create-vpc-instance/3.1-create-vpc/enable-ipv4.png)
- Hoàn thành gán Public IPv4 cho một public subnet **deploy-fullstack-blog-workshop-subnet-public1-ap-southeast-1a**
![complete](/images/3-create-vpc-instance/3.1-create-vpc/complete.png)

