+++
title = "Tạo Cloudfront"
date = 2025
weight = 1
chapter = false
pre = "<b>8.1 </b>"
+++

#### Tạo Cloudfront

1. Truy cập vào [AWS Management Console](https://console.aws.amazon.com/)
    - Tìm **Cloudfront**
    - Chọn **Cloudfront**

        ![Find Cloudfront](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.1.png)

2. Trong giao diện  **Cloudfront**
    - Chọn **Distributions**
    - Chọn **Create distribution**

        ![Distributions](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.2.png)


3. Trong giao diện **Create distribution** 

    - **Origin domain**, chọn tên **S3 bucket** đã tạo
    - **Origin access**, chọn **Origin access control settings (recommended)**
    - **Origin access control**, chọn **Create new OAC**

        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.3.png)

    - Trong giao diện **Create new OAC**, để mặc định. Sau đó chọn **Create**

        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.4.png)

    - Sau khi **Create new OAC**, chọn OAC vừa tạo

        ![Create new OAC](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.5.png)

    - Kéo xuống phần **Viewer protocol policy**,chọn **Redirect HTTP to HTTPS**

    -  Ở phần **Allowed HTTP methods** chọn **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE**
        ![Allowed HTTP](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.6.png)

    - Ở phần **Web Application Firewall (WAF)**, chọn **Do not enable security protections**
        ![Application Firewall](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.7.png)

    - Các phần còn lại để mặc định. Kéo xuống và chọn **Create distribution**
        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.8.png)

    - Chúc mừng bạn đã tạo thành công **Distribution**

    - Quá trình khởi tạo sẽ mất 4-5 phút để hoàn thành.

        ![Create distribution Success](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.9.png)


