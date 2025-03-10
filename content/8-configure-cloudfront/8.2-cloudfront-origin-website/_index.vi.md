+++
title = "Cấu hình Cloudfront"
date = 2025
weight = 2
chapter = false
pre = "<b>8.2 </b>"
+++

#### Cloudfront Origin request policy

1. Ở giao diện **Distributions**
    - Chọn **Distributions** bạn vừa tạo
        ![distribution](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.1.png)
    - Chọn **Origins**
    - Chọn **Origin name** bạn vừa tạo
    - Chọn **Edit**
        ![Edit distribution](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.2.png)
    
2. Ở giao diện **Edit origin**
    - Chọn **OAC** vừa tạo.
    - Chọn **Copy policy**
    - Chuyển hướng đến **S3 bucket** bạn đã tạo
    ![Edit origin](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.3.png)

    - Sau khi vào **Bucket** của bạn, chọn **Permissions**
    ![Bucket](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.4.png)

    - Kéo xuống tìm **Bucket policy**, chọn **Edit**
    ![Bucket policy](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.5.png)

    - Dán mã vào **Bucket policy** của **S3**
    - Chọn **Save changes**
    ![Bucket policy](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.6.png)

    - Bạn đã tạo thành công **Origin request policy**




