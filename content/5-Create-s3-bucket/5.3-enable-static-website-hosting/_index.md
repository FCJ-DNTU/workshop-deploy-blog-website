+++
title = "Enable Static website hosting"
date = 2025
weight = 3
chapter = false
pre = "<b>5.3 </b>"
+++

#### Enable Static website hosting

1. Go to the created **S3** bucket
    - Select **Properties**
    ![S3 bucket](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.1.png)

2. In the **Properties** interface
    - Scroll down to find **Static website hosting** and select **Edit**

    ![Properties](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.2.png)

3. In the interface **Edit static website hosting**
    - In the **Static website hosting**, select **Enable**
    - In the **Hosting type**, select **Host a static website**
    - In the **Index document**, enter `index.html`
    - In the **Error document**, enter `error.html`
    ![Edit static website hosting](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.3.png)

    - Scroll down and select **Save changes**
    ![Save changes](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.4.png)


#### Edit Bucket Policy
- In **Permissions**, set **Block public access** to **Off**
    ![Edit Bucket Policy](/images/5-create-s3-bucket/5.3-enable-static-website-hosting/5.3.5.png)

- In the **Bucket policy**, Select Edit and Paste the following Json:
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


