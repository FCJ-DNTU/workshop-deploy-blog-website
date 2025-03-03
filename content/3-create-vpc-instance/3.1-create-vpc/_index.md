---
title: "Create a VPC Instance"
date: 2025
weight: 1
chapter: false
pre: "<b>3.1. </b>"
---

#### Introduction to VPC

In this workshop, *Amazon Virtual Private Cloud (VPC)* is used to create a **private network**, enabling the organization and management of resources within a dedicated network space on AWS.

VPC allows you to have complete control over your network environment, including IP address configuration, route tables, internet gateways, and subnets.

#### Key Use Cases of VPC in the Workshop

Trong Workshop này, chúng ta sẽ khởi tạo VPC Instance bao gồm:

- 2 Availability Zones (AZs) to ensure high availability.

- 2 Public Subnets (for EC2 running applications).

- 2 Private Subnets (for Amazon DocumentDB).

- An Internet Gateway (IGW) to allow EC2 instances to communicate with the Internet.

- Security Groups to manage secure access control.

![use-case-vpc](/images/3-create-vpc-instance/3.1-create-vpc/use-case-vpc.png)

#### Pricing for VPC

There is no cost associated with using VPC itself. However, charges apply for **VPC-related services**, such as NAT Gateways, IP Address Manager, traffic mirroring, Reachability Analyzer, and Network Access Analyzer.

#### Create a VPC Instance

In this section, we will create a **VPC Instance**, which includes 2 **Availability Zones (AZs)**, **2 Public Subnets** and **2 Private Subnets.**

#### 1. Create the VPC Instance
- Go to [Your VPCs](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#vpcs:), and
- Select **Create VPC**.
- In the **VPC Settings**, choose the option **VPC and more**.

![create-vpc](/images/3-create-vpc-instance/3.1-create-vpc/create-vpc.png)
- Enter a **name tag** and leave other fields as default, then click **Create VPC**.
![create-vpc-done](/images/3-create-vpc-instance/3.1-create-vpc/create-vpc-done.png)
- Click View VPC to see the details of the created VPC
![review-result](/images/3-create-vpc-instance/3.1-create-vpc/review-result.png)

#### 2. Assign Public IPv4 to Public Subnets
- Go to [Subnets](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#subnets:)
- Select the **Subnet ID** of the public subnet e.g. **deploy-fullstack-blog-workshop-subnet-public1-ap-southeast-1a**
![subnets](/images/3-create-vpc-instance/3.1-create-vpc/subnets.png)
- Click the **Actions** dropdown, then select **Edit subnet settings**
![edit-subnet](/images/3-create-vpc-instance/3.1-create-vpc/edit-subnet.png)
- Check **Enable auto-assign public IPv4 address**, then **Save**
![enable-ipv4](/images/3-create-vpc-instance/3.1-create-vpc/enable-ipv4.png)
- Successfully assigned a Public IPv4 to the public subnet 
**deploy-fullstack-blog-workshop-subnet-public1-ap-southeast-1a**
![complete](/images/3-create-vpc-instance/3.1-create-vpc/complete.png)

