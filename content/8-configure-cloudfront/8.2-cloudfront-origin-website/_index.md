+++
title = "Configure Cloudfront"
date = 2025
weight = 2
chapter = false
pre = "<b>8.2 </b>"
+++

#### Cloudfront Origin request policy

1. In the **Distributions** interface
    - Select the **Distributions** you just created
        ![distribution](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.1.png)
    - Select **Origins**
    - Select the  **Origin name** you just created
    - Select **Edit** 
        ![Edit distribution](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.2.png)
    
2. On the **Edit origin** interface 
    - Select the **OAC** you just created.
    - Select **Copy policy**
    - Redirect to the **S3** bucket you created
    ![Edit origin](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.3.png)

    - After entering your **Bucket** select **Permissions**
    ![Bucket](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.4.png)

    - Scroll down to find **Bucket policy**, select **Edit**
    ![Bucket policy](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.5.png)

    - Paste the code into the **S3 Bucket policy**
    - Select **Save changes**
    ![Bucket policy](/images/8-configure-cloudfront/8.2-cloudfront-origin-website/8.2.6.png)

    - You have successfully created an **Origin request policy**




