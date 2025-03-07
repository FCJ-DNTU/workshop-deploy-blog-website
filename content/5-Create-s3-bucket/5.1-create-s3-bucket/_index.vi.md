+++
title = "Tạo S3 bucket"
date = 2025
weight = 1
chapter = false
pre = "<b>5.1 </b>"
+++


#### Tạo S3 bucket

1. Truy cập vào [AWS Management Console](https://console.aws.amazon.com/)
    - Tìm **S3**
    - Chọn **S3**
    ![Search S3](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.1.png)

2. Trong giao diện **S3**
    - Chọn **General purpose buckets**
    - Chọn **Create bucket**
    ![Dashboard S3](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.2.png)

3. Trong giao diện **Create bucket**
    - **Bucket name**, nhập `s3-blog-workshop`
    - Ở phần **Object Ownership**, chọn **ACLs disabled**
    ![Create bucket](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.3.png)

    - Ở phần **Block Public Access settings for this bucket**, giữ nguyên mặc định
    ![Create bucket](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.4.png)

    - Các phần còn lại giữ nguyên mặc định. Cuộn xuống và chọn **Create bucket**
    ![Create bucket](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.5.png)

4. Hoàn thành tạo **S3 bucket** để lưu trữ source website
    ![Create bucket](/images/5-create-s3-bucket/5.1-create-s3-bucket/5.6.png)








