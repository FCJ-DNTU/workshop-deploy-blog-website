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

### Kiến thức được cung cấp trong Workshop

**Các dịch vụ AWS và chi phí:**

**1. Amazon EC2 (Elastic Compute Cloud)**
**Công dụng:**
- Amazon EC2 được sử dụng để chạy các ứng dụng backend, xử lý dữ liệu và kết nối với Amazon DocumentDB để truy vấn dữ liệu.
- EC2 được đặt trong Public Subnet để có thể giao tiếp với Internet thông qua Internet Gateway.

**Chi phí:**
| Trạng thái | Loại máy chủ | Chi phí/ngày | Chi phí/tháng |
|------------|-------------|--------------|--------------|
| **Free Tier** | t2.micro (750 giờ miễn phí) | **$0.00** | **$0.00** |
| **Hết Free Tier** | t2.micro (~$0.30/ngày) | **$0.30** | **~$9** |

---

**2. Amazon DocumentDB**
**Công dụng:**
- DocumentDB đóng vai trò là cơ sở dữ liệu NoSQL để lưu trữ và quản lý dữ liệu.
- Hai instance DocumentDB được đặt trong các Private Subnet khác nhau để tăng tính sẵn sàng và có cơ chế replication để đảm bảo dữ liệu không bị mất mát.

**Chi phí:**
| Trạng thái | Loại instance | Chi phí/ngày | Chi phí/tháng |
|------------|--------------|--------------|--------------|
| **Free Tier** | db.t3.medium (750 giờ miễn phí) | **$0.00** | **$0.00** |
| **Hết Free Tier** | db.t3.medium (~$0.66/ngày) | **$0.66** | **~$20** |

---

**3. Amazon S3 (Simple Storage Service)**
**Công dụng:**
- Amazon S3 được sử dụng để lưu trữ tệp tĩnh, dữ liệu backend và các nội dung tĩnh như hình ảnh, video hoặc các file tài liệu phục vụ cho ứng dụng.

**Chi phí:**
| Trạng thái | Dung lượng | Chi phí/ngày | Chi phí/tháng |
|------------|-----------|--------------|--------------|
| **Free Tier** | 5GB (miễn phí) | **$0.00** | **$0.00** |
| **Hết Free Tier** | 5GB (~$0.03/ngày) | **$0.03** | **~$1** |

---

**4. Amazon CloudFront**
**Công dụng:**
- CloudFront là CDN (Content Delivery Network) giúp phân phối nội dung từ S3 và EC2.
- Giúp tối ưu hóa hiệu suất truy cập và giảm tải băng thông trực tiếp từ S3 và EC2.

**Chi phí:**
| Trạng thái | Dung lượng | Chi phí/ngày | Chi phí/tháng |
|------------|-----------|--------------|--------------|
| **Free Tier** | 50GB băng thông miễn phí | **$0.00** | **$0.00** |
| **Hết Free Tier** | 50GB (~$0.10 - $0.16/ngày) | **$0.10 - $0.16** | **~$3 - $5** |

---

**5. Internet Gateway (IGW)**
**Công dụng:**
- Internet Gateway được sử dụng để kết nối mạng VPC nội bộ với Internet, giúp Amazon EC2 có thể nhận và gửi dữ liệu ra bên ngoài.
- IGW là một thành phần quan trọng trong hệ thống networking của AWS.

**Chi phí:**
- **Miễn phí** theo AWS.

---

**6. IAM (Identity and Access Management) + VPC + Security Groups**
**Công dụng:**
- IAM được sử dụng để quản lý quyền truy cập của các user và nhóm trong hệ thống, đảm bảo bảo mật.
- Trong bài Workshop này, Amazon Virtual Private Cloud (VPC) được sử dụng để tạo một mạng riêng ảo (private network), cho phép tổ chức và quản lý các tài nguyên trong một không gian mạng riêng biệt trên AWS. VPC giúp bạn kiểm soát hoàn toàn môi trường mạng của mình, từ cấu hình địa chỉ IP, bảng định tuyến (route table), cổng internet (Internet Gateway) cho đến các mạng con (subnet).
- Trong Workshop này, chúng ta sẽ khởi tạo VPC Instance bao gồm: 2 Availability Zones (AZs) để đảm bảo tính sẵn sàng cao. 2 Public Subnets (dành cho EC2 chạy ứng dụng). 2 Private Subnets (dành cho Amazon DocumentDB). Internet Gateway (IGW) để EC2 có thể giao tiếp với Internet.
- Security Group để quản lý quyền truy cập an toàn, Security Groups đóng vai trò bảo vệ tài nguyên bằng cách kiểm soát truy cập mạng.

**Chi phí:**
- **Miễn phí** theo AWS.

---

**7. Tổng hợp chi phí**

**7.1. Chi phí khi còn Free Tier**  
| Dịch vụ | Loại | Chi phí/ngày | Chi phí/tháng |
|---------|------|--------------|--------------|
| **Amazon EC2** | t2.micro | **$0.00** | **$0.00** |
| **Amazon DocumentDB** | db.t3.medium | **$0.00** | **$0.00** |
| **Amazon S3** | 5GB lưu trữ | **$0.00** | **$0.00** |
| **Amazon CloudFront** | 50GB băng thông | **$0.00** | **$0.00** |
| **IAM + VPC + Security Groups** | Miễn phí | **$0.00** | **$0.00** |
| **Tổng cộng** |  | **$0.00** | **$0.00** |

---

**7.2. Chi phí khi hết Free Tier**  
| Dịch vụ | Loại | Chi phí/ngày | Chi phí/tháng |
|---------|------|--------------|--------------|
| **Amazon EC2** | t2.micro | **~$0.30** | **~$9** |
| **Amazon DocumentDB** | db.t3.medium | **~$0.66** | **~$20** |
| **Amazon S3** | 5GB lưu trữ | **~$0.03** | **~$1** |
| **Amazon CloudFront** | 50GB băng thông | **~$0.10 - $0.16** | **~$3 - $5** |
| **IAM + VPC + Security Groups** | Miễn phí | **$0.00** | **$0.00** |
| **Tổng cộng** |  | **~$1.10 - $1.15** | **~$33 - $35** |

---

**8. Kết luận**
- Khi còn trong Free Tier, hệ thống hoạt động với **chi phí $0**.
- Khi Free Tier hết hạn, chi phí duy trì hệ thống sẽ **dao động từ $33 - $35/tháng**.
- Nếu hệ thống mở rộng, chi phí có thể thay đổi tùy theo mức sử dụng tài nguyên, đặc biệt là DocumentDB, S3 và CloudFront.

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