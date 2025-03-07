+++
title = "Create CloudFront"
date = 2025
weight = 1
chapter = false
pre = "<b>8.1 </b>"
+++

#### Create Cloudfront

1. Access the [AWS Management Console](https://console.aws.amazon.com/)
    - Find **Cloudfront**
    - Select **Cloudfront**

        ![Find Cloudfront](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.1.png)

2. In the **Cloudfront** interface
    - Select **Distributions**
    - Select **Create distribution**

        ![Distributions](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.2.png)


3. In the **Create distribution** interface

    - **Origin domain**, select the name of the created **S3 bucket**
    - **Origin access**, select **Origin access control settings (recommended)**
    - **Origin access control**, select **Create new OAC**

        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.3.png)

    - In the **Create new OAC interface**, leave it to default. Then select **Create**

        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.4.png)

    - After **Create new OAC**, select the OAC you just created
        ![Create new OAC](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.5.png)

    - Scroll down to the **Viewer protocol policy** section, select **Redirect HTTP to HTTPS**

    - In the Allowed HTTP methods section, select **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE**
        ![Allowed HTTP](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.6.png)

    - In the Web Application Firewall (WAF) section, select **Do not enable security protections**
        ![Application Firewall](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.7.png)

    - The rest is left to default. Scroll down and select **Create distribution**
        ![Create distribution](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.8.png)

    - Congratulations on successfully creating **Distribution**

    - The initialization process will take 4-5 minutes to complete.

        ![Create distribution Success](/images/8-configure-cloudfront/8.1-create-cloudfront/8.1.9.png)


