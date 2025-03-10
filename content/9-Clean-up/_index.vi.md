+++
title = "Dọn dẹp tài nguyên"
date = 2025
weight = 9
chapter = false
pre = "<b>9. </b>"
+++


#### 1. Xóa CloudFront Distribution

- Truy cập vào [CloudFront](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home#/distributions)
- Chọn **distribution** cần xóa
- Nhấp **Disable**
- Khi trạng thái **Disabled successfully**, nhấp vào **Delete** để xóa
  ![delete-distribution.png](/images/9-clean-up/9.1.png)
  ![delete-distribution.png](/images/9-clean-up/9.2.png)


#### 2. Xóa DocumentDB Cluster

- Truy cập vào Amazon DocumentDB, mục
  [Clusters](https://ap-southeast-1.console.aws.amazon.com/docdb/home?region=ap-southeast-1#clusters)
- Chọn **Cluster to delete** cần xóa
- Nhấp vào **Action**, sau đó chọn **Delete**
- Một hộp thoại xác nhận sẽ xuất hiện
{{% notice note %}}
**Lưu ý:** Cụm **Amazon DocumentDB** có bật **Deletion Protection**, ngăn chặn việc xóa trực tiếp. Để xóa, vào **Modify**, tắt **Deletion Protection**, sau đó thử xóa lại
{{% /notice %}}
- Chọn **close**
![delete-cluster.png](/images/9-clean-up/9.3.1.png)
- Chọn **docdb-blog-workshopv1**, sau đó chọn **Modify**
![delete-cluster.png](/images/9-clean-up/9.3.2.png)
- Tắt **Disable Deletion protection**, chọn **continue**   
![delete-cluster.png](/images/9-clean-up/9.3.3.png)
- Chọn **Apply during**, Chọn **Modify cluster**
![delete-cluster.png](/images/9-clean-up/9.3.4.png)

- Thực hiện lại các bước đầu tiên, chọn **Cluster to delete**, nhấp vào **Action**, sau đó chọn **Delete**, 

- Hộp thoại xác nhận xuất hiện
- Nhập tên **Snapshot**: `blog-workshopv1` và gõ `delete entire cluster`
![confirmation_dialog.png](/images/9-clean-up/9.3.5.png)

- Sau khi xóa **successfully deleting the Cluster** thành công, truy cập vào
  [Snapshots](https://ap-southeast-1.console.aws.amazon.com/docdb/home?region=ap-southeast-1#snapshots) để xóa Snapshot
- Chọn **Snapshot to delete** cần xóa
- Nhấp vào **Action**, sau đó chọn **Delete**
  ![delete-snapshot.png](/images/9-clean-up/9.5.png)



#### 3. Xóa Tài Nguyên EC2

- Truy cập vào [EC2 Instances](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:)
- Chọn **Instance**, nhấp vào **Instance state**, sau đó chọn **Terminate**.
  ![delete-ec2.png](/images/9-clean-up/9.6.png)

#### 4. Xóa Tài Nguyên VPC

- Truy cập vào  [Your VPCs](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#vpcs:)
- Chọn **Instance**, sau đó nhấp vào **Actions** và chọn **Delete VPC**.
  ![delete-vpc.png](/images/9-clean-up/9.7.png)


#### 5. Dọn Dẹp IAM Resources

- Truy cập vào **Root user**.
- Truy cập vào [IAM Service](https://us-east-1.console.aws.amazon.com/iam/home?region=ap-southeast-1#/home)
- Trong **Policies**, chọn **Policy** và nhấp vào **Delete**

  ![delete-policy.png](/images/9-clean-up/9.8.png)

- Trong **User groups**, chọn **Groups** và nhấp vào **Delete**
  ![delete-groups.png](/images/9-clean-up/9.9.png)

- Trong **Users**, chọn user và nhấp vào **Delete**.

  ![delete-users.png](/images/9-clean-up/9.9.1.png)

#### 5. Xóa S3
- Truy cập vào giao diện **S3**
- Chọn **General purpose buckets**
- Chọn **Bucket name** you created
- Chọn **Delete**
![Clean S3.png](/images/9-clean-up/9.9.2.png)

- Trong giao diện **Delete bucket** 
    - Chọn **Empty bucket**
    ![Clean S3.png](/images/9-clean-up/9.9.3.png)


- Trong giao diện **Empty bucket**
    - Nhập `permanently delete` để xác nhận
    - Chọn **Empty**
    ![Clean S3.png](/images/9-clean-up/9.9.4.png)

- Sau khi **Empty** thành công
    - Chọn **Bucket**
    - Chọn lại tên Bucket bạn muốn xóa
    - Chọn **Delete**
    ![Clean S3.png](/images/9-clean-up/9.9.5.png)

- Trong giao diện  **Delete bucket**
    - Sao chép **Bucket name** bạn đã tạo
    - Dán vào ô  **confirm**
    - Chọn **Delete bucket**
    ![Clean S3.png](/images/9-clean-up/9.9.6.png)


#### Hoàn Thành    



