+++
title = "Bật Static website hosting"
date = 2025
weight = 3
chapter = false
pre = "<b>5.3 </b>"
+++

#### Bật Static website hosting

1. Vào **S3 bucket** đã tạo
    - Chọn **Properties**
    ![S3 bucket](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.1.png)

2. Trong giao diện **Properties**
    - Kéo xuống tìm **Static website hosting** và chọn **Edit**

    ![Properties](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.2.png)

3. Trong giao diện **Edit static website hosting**

    - Ở mục **Static website hosting**, chọn **Enable**
    - Ở mục **Hosting type**, chọn **Host a static website**
    - Ở mục **Index document**, nhập `index.html`
    - Ở mục **Error document**, nhập `error.html`
    ![Edit static website hosting](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.3.png)
    
    - Kéo xuống và chọn **Save changes**
    ![Save changes](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.4.png)


#### Chỉnh sửa Bucket Policy
- Trong **Permissions**, chỉnh **Block public access** thành **Off** 
    ![Edit Bucket Policy](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.5.png)

- Trong **Bucket policy**, chọn Edit và Dán đoạn Json sau:
    ```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "PublicReadGetObject",
                "Effect": "Allow",
                "Principal": "*",
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::s3-blog-workshop/*"
            }
        ]
    }
    ```
    ![Edit Bucket Policy](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.6.png)

