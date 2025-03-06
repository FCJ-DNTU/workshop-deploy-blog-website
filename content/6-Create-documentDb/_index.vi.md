+++
title = "Khởi tạo AWS DocumentDB Service"
date = 2025
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

![aws-documentdb.png](/images/6-create-document/document-db.jpeg)

#### AWS DocumentDB

**Amazon DocumentDB** Amazon DocumentDB là một cơ sở dữ liệu NoSQL do AWS cung cấp, lưu trữ dữ liệu dạng JSON, tương thích với MongoDB. Đây là dịch vụ quản lý hoàn toàn, giúp bạn chạy các ứng dụng quan trọng mà không cần lo quản lý hạ tầng, tiết kiệm thời gian và chi phí.


#### Lợi ích khi sử dụng DocumentDB:

- **Tương thích MongoDB:** Dùng được các công cụ và mã của MongoDB, dễ chuyển đổi dữ liệu.
- **Hiệu suất tốt, dễ mở rộng:** Xử lý nhanh, tự động tăng dung lượng khi cần.
- **Dễ quản lý:** AWS lo hết việc sao lưu, bảo trì, bạn chỉ cần tập trung vào ứng dụng.

#### Giá của Amazon DocumentDB

Giá **Amazon DocumentDB** được tính dựa trên:
- **Máy chủ (On-Demand Instances):** Trả tiền theo giờ, tùy loại máy bạn dùng.
Đọc/ghi dữ liệu (Database I/O): Tính theo số lần truy cập, mỗi triệu lần là một mức giá.
- **Dung lượng lưu trữ (Database Storage):** Trả theo GB mỗi tháng.
- **Bản sao lưu (Backup Storage):** Tính thêm nếu dung lượng sao lưu vượt quá dung lượng chính, cũng theo GB/tháng.

Cách tính giá **Amazon DocumentDB**:

- **Standard (Trả tiền theo I/O sử dụng):**
    - Dành cho ứng dụng ít hoặc vừa phải truy cập dữ liệu (I/O thấp - trung bình).
    - Tính phí dựa trên: Máy chủ (Instance), Đọc/ghi (I/O), Lưu trữ (Storage), Sao lưu (Backup).
    - Phù hợp nếu chi phí I/O dưới 25% tổng chi phí.
- **I/O-Optimized (Gộp phí I/O vào giá máy chủ)**
    - Dành cho ứng dụng truy cập dữ liệu nhiều (I/O cao).
    - Chỉ tính phí: Máy chủ (Instance), Lưu trữ (Storage), Sao lưu (Backup) – không tính riêng I/O.
    - Dễ dự đoán chi phí, phù hợp nếu I/O chiếm trên 25% tổng chi phí.


#### Workshop này nên chọn cấu hình nào?
- Chúng ta sẽ chọn **Amazon DocumentDB Standard** để tiết kiệm chi phí, vì:
    - Truy vấn ít lúc đầu, giúp tiết kiệm chi phí.
    - Chỉ trả tiền cho lượng đọc/ghi (I/O) thực tế.
    - Dễ nâng cấp lên I/O-Optimized nếu sau này truy vấn nhiều hơn.

#### Tạo một DB Instance trên AWS

1. Đăng nhập vào **AWS Management Console** và mở **Amazon DocumentDB**

2. Tạo **DocumentDB Cluster**
   ![Cluster-interface.png](/images/6-create-documentdb/6.1.png)

3. Trong **Create Amazon DocumentDB cluster**, điền thông tin sau:

   - **Cluster type**: Instance-based cluster
   - **Cluster identifier**: `docdb-blog-workshop`
   - **Engine version**: Chọn phiên bản mới nhất
   - **Cluster storage configuration**: Amazon DocumentDB Standard
   - **Instance class**: db.t3.medium
   - **Number of instances**: 2 (1 Primary + 1 Replica)
   - **Connectivity**: Don't connect to an EC2 compute resource
   - **Username**: `user123`
   - Select **Self managed**
   - **Password**: `user1234`
   - **Confirm Password**: `user1234`
   - **Subnet group**: chọn subnet group đã tạo ở **3.3**
   - **VPC security groups**: **private-sg-documentdb (VPC)**
   - **Deletion protection**: Tích **Enable deletion protection**
   - Kiểm tra lại các thiết lập và nhấn **Create cluster**
     ![create-1.png](/images/6-create-documentdb/6.2.png)
     ![create-2.png](/images/6-create-documentdb/6.3.png)
           ![create-1.png](/images/6-create-documentdb/6.4.png)
     ![create-2.png](/images/6-create-documentdb/6.5.png)
     ![create-1.png](/images/6-create-documentdb/6.6.png)
     ![create-2.png](/images/6-create-documentdb/6.7.png)
   - Đợi ít phút nó sẻ chuyển sang Tạo **Cluster** thành công
     ![create-2.png](/images/6-create-documentdb/6.8.png)

4. Kiểm tra kết nối từ EC2 tới DocumentDB

- Vào cluster vừa mới tạo, chọn tab **Configuration** và copy **Cluster endpoint**
 ![create-2.png](/images/6-create-documentdb/6.9.png)
- Vào EC2, ấn nút **Connect** và ấn nút **Connect** trong tab **EC2 Instance Connect**

    ```shell
    $ sudo apt-get install -y netcat
    $ nc -zv docdb-blog-workshopv1.cluster-cl8uqi4yidxz.ap-southeast-1.docdb.amazonaws.com 27017
    ```

    ![success.png](/images/6-create-documentdb/6.10.png)

### **Hoàn thành!**