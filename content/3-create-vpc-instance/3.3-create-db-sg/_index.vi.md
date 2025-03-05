---
title: "Tạo Database Subnet Group"
date: 2025
weight: 3
chapter: false
pre: "<b>3.3 </b>"
---

#### DB Subnet Group là gì?

**DB Subnet Group** trong Amazon DocumentDB là một tập hợp các subnets trong VPC, được sử dụng để xác định các subnets mà cluster DocumentDB có thể triển khai. Mỗi DB Subnet Group phải chứa **tối thiểu hai subnets thuộc các Availability Zones (AZs) khác nhau** để đảm bảo tính sẵn sàng cao và khả năng dự phòng.


### Vì sao cần tạo DB Subnet Group?
- **Chọn đúng mạng trong VPC:** DB Subnet Group giúp xác định VPC và subnet nào Amazon DocumentDB có thể sử dụng, giúp kiểm soát mạng và tăng cường bảo mật.

- **Giữ hệ thống luôn hoạt động:** Cơ sở dữ liệu cần ít nhất 2 subnet ở 2 khu vực khác nhau (AZs). Nếu một khu vực bị lỗi, hệ thống vẫn hoạt động nhờ subnet còn lại.

- **Tự động chuyển đổi khi gặp sự cố:** Nếu máy chủ chính (primary instance) bị lỗi, Amazon DocumentDB sẽ chuyển đổi sang máy chủ dự phòng (replica instance) trong subnet khác để đảm bảo không bị gián đoạn. Sau đó, một máy chủ mới sẽ được tạo để duy trì số lượng cần thiết.

#### Tạo DB Subnet Group trên AWS

Để tạo DB Subnet Group trên AWS, làm theo các bước sau:

1. Truy cập vào **AWS Management Console**.

2. Tìm và chọn dịch vụ **Amazon DocumentDB**.

3. Trong menu điều hướng, chọn [Subnet
   groups](hhttps://ap-southeast-1.console.aws.amazon.com/docdb/home?region=ap-southeast-1#subnetGroups).
   ![documentdb-interface.png](/images/3-create-vpc-instance/3.3-create-db-sg/3.3.1.png)

4. Trong **Subnet groups**, chọn **Create**

5. Trong giao diện **Create DB Subnet Group**:

   - **Name**: `blog-db-subnet-group`.

   - **Description**: `blog-db-subnet-group`.

   - Chọn VPC mà bạn đang sử dụng.

   - Trong phần **Add Subnets**, chọn các **Private Subnet**:
     - Chọn **ít nhất hai Private Subnet thuộc hai AZs khác nhau** (ví dụ subnet-xxxxxx1 ở AZ **us-east-1a**, subnet-xxxxxx2 ở AZ **us-east-1b**).
     - Nhấn **Add subnet**
       ![create-subnet-group.png](/images/3-create-vpc-instance/3.3-create-db-sg/3.3.2.png)

6. Nhấn nút **Create** để hoàn thành quá trình tạo DB Subnet Group.
  ![complete.png](/images/3-create-vpc-instance/3.3-create-db-sg/3.3.3.png)