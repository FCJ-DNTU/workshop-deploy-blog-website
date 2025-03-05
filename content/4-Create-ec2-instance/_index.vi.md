+++
title = "Khởi tạo EC2 Instance"
date = 2025
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Amazon EC2

**Amazon Elastic Compute Cloud (Amazon EC2)** à dịch vụ cung cấp máy chủ ảo (cloud server) trên nền tảng đám mây của Amazon Web Services (AWS). Nó cho phép bạn dễ dàng thuê và sử dụng tài nguyên máy tính theo nhu cầu, thay vì phải mua và duy trì máy chủ vật lý.

#### Amazon EC2 Instance là gì?
**Amazon EC2 Instance** là một máy chủ ảo (cloud server) chạy trên hạ tầng của Amazon EC2. Khi có tài khoản AWS, bạn có thể tạo nhiều EC2 Instance để chạy ứng dụng, lưu trữ dữ liệu hoặc xử lý các tác vụ khác. Các EC2 Instance được vận hành trên cùng một hệ thống máy chủ vật lý và chia sẻ tài nguyên như CPU, RAM, ổ cứng...

#### Mô hình triển khai EC2 trong Workshop
- Trong Workshop này, chúng ta sẽ khởi tạo EC2 Instance để cchạy backend (Node.js, Express.js): Xử lý API và logic nghiệp vụ. Kết nối với DocumentDB: Truy xuất và lưu trữ dữ liệu. Giao tiếp với frontend: Nhận request từ ReactJS, phản hồi dữ liệu. Bảo mật hệ thống: Chỉ mở các cổng cần thiết, kết nối DocumentDB trong Private Subnet.

#### Lý do chọn **t2.micro**:
- **Chi phí thấp:** Là một loại instance thuộc Free Tier (miễn phí trong giới hạn AWS Free Tier), phù hợp cho việc học tập hoặc thử nghiệm.  
- **Tài nguyên cơ bản:** Bao gồm 1 vCPU và 1GB RAM, đủ để chạy ứng dụng Golang đơn giản hoặc thử nghiệm các dịch vụ AWS cơ bản.  
- **Burstable Performance:** Có khả năng tăng cường hiệu năng khi cần, rất hữu ích cho các ứng dụng có tải không đều.  

#### Lý do chọn **Ubuntu**:
- **Tương thích cao:** Ubuntu hỗ trợ nhiều phần mềm và công cụ phổ biến, phù hợp cho việc triển khai các ứng dụng web, Golang, Docker, và Kubernetes.
- **Hỗ trợ LTS (Long Term Support):** Ubuntu 24.04 LTS có hỗ trợ dài hạn, giúp duy trì hệ thống ổn định trong thời gian dài.
- **Cập nhật thường xuyên:** Ubuntu có các bản cập nhật định kỳ, đảm bảo bảo mật và tính ổn định.

#### Khởi tạo EC2 Instance

#### 1. Truy cập AWS Console

- Mở trình duyệt và truy cập vào Amazon EC2 console tại https://console.aws.amazon.com/ec2/.

#### 2. Trong **Dashboard**, chọn **Launch instance**
![Launch.png](/images/4-create-ec2-instance/4.1.png)


#### 3. Đặt tên cho instance

- Trong phần **Name and tags**:
- **Name:** `blog-ec2`

#### 4. Chọn image (Amazon Machine Image - AMI)

- Dưới phần Application and OS Images (Amazon Machine Image), làm theo các bước sau đây:
- Chọn **Quick Start**, sau đó chọn **Ubuntu**. Đây là hệ điều hành (OS) cho instance của bạn.
- Từ Amazon Machine Image (AMI), chọn **Ubuntu 24.04 LTS HVM**. Lưu ý rằng AMI này được đánh dấu là **Free tier
eligible**. Một Amazon Machine Image (AMI) là một cấu hình cơ bản dùng làm mẫu cho instance của bạn.
![ami.png](/images/4-create-ec2-instance/4.2.png)


#### 5. Chọn loại instance

- Trong Instance type, chọn loại instance **t2.micro** và dưới phần **Key pair (login)**, chọn **Create new key pair**
![instance.png](/images/4-create-ec2-instance/4.3.png)

#### 6. Tạo Key Pair

- Trong **Create key pair**, điền những thông tin sau:
- **Key pair name**: `blog-kp`
- **Key pair type**: chọn **RSA**
- **Private key file format**: **.pem**
- Sau đó chọn **Create key pair**. Một file **.pem** sẽ tự động tải về máy
![instance.png](/images/4-create-ec2-instance/4.4.png)

{{% notice warning %}}
Cảnh báo: Đừng chọn Proceed without a key pair (Không được khuyến nghị). Nếu bạn tạo instance mà không có key pair, bạn
sẽ không thể kết nối vào nó.
{{% /notice %}}


#### 7. Cấu hình Security Group
- Trong **Network settings**, chọn **Edit** ở bên cạnh. Đối với Security group name, bạn đã tạo và chọn một security
group cho EC2. Bạn chọn security group mà bạn đã tạo khi cài đặt bằng các bước sau đây:

- Chọn **Select existing security group**.
- Từ **Common security groups**, chọn security group của bạn từ danh sách các security group hiện có.
- Xác nhận và khởi động instance
- Giữ nguyên các lựa chọn mặc định cho các cài đặt khác của instance của bạn.
- Xem lại bản tóm tắt về cấu hình instance của bạn trong **Summary**, và khi bạn đã sẵn sàng, chọn **Launch instance**.

![sg-config.png](/images/4-create-ec2-instance/4.5.png)

#### 8. Xác nhận và kiểm tra

- Một trang thông báo rằng instance của bạn đang được khởi động. Chọn **View all instances** để quay lại giao diện
console..
![view.png](/images/4-create-ec2-instance/4.6.png)

- Một trang xác nhận sẽ thông báo rằng instance của bạn đang được khởi động. Chọn **View all instances** để đóng trang xác nhận và trở lại giao diện console.
- Trên màn hình Instances, bạn có thể xem trạng thái của quá trình khởi động. Có một thời gian ngắn để instance được khởi động. Khi bạn khởi động instance, trạng thái ban đầu của nó là pending. Sau khi instance khởi động, trạng thái của nó sẽ thay đổi thành running và nó sẽ nhận được một tên DNS công cộng. Nếu cột Public IPv4 DNS bị ẩn, hãy chọn biểu tượng cài đặt (Biểu tượng cài đặt) ở góc trên bên phải, bật Public IPv4 DNS và chọn Confirm.
- Có thể mất vài phút để instance sẵn sàng để bạn kết nối vào. Hãy kiểm tra xem instance của bạn đã vượt qua kiểm tra trạng thái; bạn có thể xem thông tin này trong cột Status check.
- Xem Public IPv4 tại **EC2 Instance** > **Networking** > **Public IPv4 Address**.
![review.png](/images/4-create-ec2-instance/4.7.review.png)


#### 9. Kết nối bằng EC2 Instance
- Chọn EC2 Instance vừa khởi tạo, chọn **Connect**
![connect.png](/images/4-create-ec2-instance/4.8.png)
- Tại giao diện **Connect to instance**, chọn tab **EC2 Instance Connect** và chọn **Connect**
![ssh-client.png](/images/4-create-ec2-instance/connect-ec2.png)

- Kết nối thành công
![success.png](/images/4-create-ec2-instance/connect-successfully.png)