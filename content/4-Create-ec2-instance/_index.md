+++
title = "Create EC2 Instance"
date = 2025
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Amazon EC2

**Amazon Elastic Compute Cloud (Amazon EC2)** is a service that provides virtual servers (cloud servers) on the Amazon Web Services (AWS) cloud platform. It allows you to easily rent and use computing resources as needed, instead of purchasing and maintaining physical servers.

#### What is an Amazon EC2 Instance?
An **Amazon EC2 Instance** is a virtual server (cloud server) running on Amazon EC2 infrastructure. With an AWS account, you can create multiple EC2 Instances to run applications, store data, or handle other tasks. EC2 Instances operate on the same physical server system and share resources such as CPU, RAM, and storage.

#### EC2 Deployment Model in the Workshop
- In this Workshop, we will create an EC2 Instance to:
  - Run the backend (Node.js, Express.js): Handle API and business logic.
  - Connect with DocumentDB: Retrieve and store data.
  - Communicate with the frontend: Receive requests from ReactJS and respond with data.
  - Secure the system: Open only necessary ports and connect DocumentDB within a Private Subnet.

#### Why choose **t2.micro**:
- **Low cost:** A Free Tier instance (free within AWS Free Tier limits), suitable for learning or experimentation.
- **Basic resources:** Includes 1 vCPU and 1GB RAM, sufficient for running simple Golang applications or testing basic AWS services.
- **Burstable Performance:** Can boost performance when needed, useful for applications with variable loads.

#### Reasons for Choosing **Ubuntu**:
- **High Compatibility:** Ubuntu supports many popular software and tools, making it suitable for deploying web applications, Golang, Docker, and Kubernetes.
- **LTS (Long Term Support):** Ubuntu 24.04 LTS offers long-term support, ensuring system stability over an extended period.
- **Frequent Updates:** Ubuntu receives regular updates, enhancing security and stability.

#### Creating an EC2 Instance

#### 1. Access AWS Console

- Open a browser and go to the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

#### 2. In the **Dashboard**, select **Launch instance**
![Launch.png](/images/4-create-ec2-instance/4.1.png)

#### 3. Name the instance

- In the **Name and tags** section:
- **Name:** `blog-ec2`

#### 4. Select an image (Amazon Machine Image - AMI)

- Under **Application and OS Images (Amazon Machine Image)**, follow these steps:
  - Select **Quick Start**, then choose **Ubuntu** as the operating system (OS) for your instance.
  - From **Amazon Machine Image (AMI)**, select **Ubuntu 24.04 LTS HVM**. Note that this AMI is marked as **Free tier eligible**.
  - An Amazon Machine Image (AMI) is a basic configuration used as a template for your instance.
![ami.png](/images/4-create-ec2-instance/4.2.png)

#### 5. Choose an instance type

- Under **Instance type**, select **t2.micro** and under **Key pair (login)**, choose **Create new key pair**.
![instance.png](/images/4-create-ec2-instance/4.3.png)

#### 6. Create a Key Pair

- In **Create key pair**, enter the following details:
  - **Key pair name**: `blog-kp`
  - **Key pair type**: Select **RSA**
  - **Private key file format**: **.pem**
  - Click **Create key pair**. A **.pem** file will be automatically downloaded to your device.
![instance.png](/images/4-create-ec2-instance/4.4.png)

{{% notice warning %}}
Warning: Do not select "Proceed without a key pair" (Not recommended). If you create an instance without a key pair, you will not be able to connect to it.
{{% /notice %}}

#### 7. Configure Security Group
- In **Network settings**, click **Edit**. For **Security group name**, you need to create and select a security group for EC2. Follow these steps:
  - Select **Select existing security group**.
  - From **Common security groups**, choose your security group from the list of available security groups.
  - Confirm and launch the instance.
  - Keep the default settings for the rest of your instance configuration.
  - Review the summary of your instance configuration in **Summary**, and when ready, select **Launch instance**.
![sg-config.png](/images/4-create-ec2-instance/4.5.png)

#### 8. Confirm and Check

- A page will notify you that your instance is launching. Click **View all instances** to return to the console.
![view.png](/images/4-create-ec2-instance/4.6.png)

- A confirmation page will indicate that your instance is starting. Click **View all instances** to close the confirmation page and return to the console.
- On the **Instances** screen, you can monitor the startup status. It may take some time for the instance to boot up. Initially, the status will be **pending**. Once the instance is running, its status will change to **running**, and it will receive a public DNS name. If the **Public IPv4 DNS** column is hidden, click the settings icon (⚙) in the top right corner, enable **Public IPv4 DNS**, and select **Confirm**.
- It may take a few minutes for the instance to be ready for connection. Check if your instance has passed the **status check**; this information is available in the **Status check** column.
- View the Public IPv4 address under **EC2 Instance** > **Networking** > **Public IPv4 Address**.
![review.png](/images/4-create-ec2-instance/4.7.review.png)

#### 9. Connect to the EC2 Instance
- Select the newly created EC2 Instance and click **Connect**.
![connect.png](/images/4-create-ec2-instance/4.8.png)

- In the **Connect to instance** interface, select the **EC2 Instance Connect** tab and click **Connect**.
![ssh-client.png](/images/4-create-ec2-instance/connect-ec2.png)

- Successfully connected.
![success.png](/images/4-create-ec2-instance/connect-successfully.png)
