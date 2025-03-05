+++
title = "Introduction"
date = 2020-05-14T00:38:32+07:00
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

In this workshop, you will learn how to deploy a Website Blog Fullstack on AWS EC2, using **DocumentDB** as the database. This step-by-step guide will help you set up a complete AWS environment, including **IAM**, **VPC**, **EC2**, and **DocumentDB**, as well as test and deploy the application efficiently while ensuring security and scalability.

![Workshop Architecture](/images/workshop_architecture.png)

### Objectives:

- Understand how to create and configure  **EC2, DocumentDB, CloudFront and IAM on AWS**.

- Deploy a Website Blog Fullstack on EC2.

- Connect and use DocumentDB from EC2,

- Learn how to configure CloudFront

### Requirements:

- An AWS account with IAM access.

- A computer with an SSH client (such as Terminal or PuTTY).


### AWS Services and Costs

**1. Amazon EC2 (Elastic Compute Cloud)**
**Purpose:**
- Amazon EC2 is used to host the backend application, process data, and connect to Amazon DocumentDB for querying.
- The EC2 instance is placed in a Public Subnet to allow communication with the internet via an Internet Gateway.

**Cost:**
| Status | Instance Type | Daily Cost | Monthly Cost |
|--------|-------------|------------|--------------|
| **Free Tier** | t2.micro (750 free hours) | **$0.00** | **$0.00** |
| **Beyond Free Tier** | t2.micro (~$0.30/day) | **$0.30** | **~$9** |

---

**2. Amazon DocumentDB**
**Purpose:**
- DocumentDB serves as a NoSQL database for storing and managing data.
- Two DocumentDB instances are placed in different Private Subnets for high availability and data replication.

**Cost:**
| Status | Instance Type | Daily Cost | Monthly Cost |
|--------|--------------|------------|--------------|
| **Free Tier** | db.t3.medium (750 free hours) | **$0.00** | **$0.00** |
| **Beyond Free Tier** | db.t3.medium (~$0.66/day) | **$0.66** | **~$20** |

---

**3. Amazon S3 (Simple Storage Service)**
**Purpose:**
- Amazon S3 is used for storing static files, backend data, and media content such as images, videos, and documents for the application.

**Cost:**
| Status | Storage | Daily Cost | Monthly Cost |
|--------|---------|------------|--------------|
| **Free Tier** | 5GB (free) | **$0.00** | **$0.00** |
| **Beyond Free Tier** | 5GB (~$0.03/day) | **$0.03** | **~$1** |

---

**4. Amazon CloudFront**
**Purpose:**
- CloudFront is a Content Delivery Network (CDN) that distributes content from S3 and EC2.
- It enhances access performance and reduces direct bandwidth usage from S3 and EC2.

**Cost:**
| Status | Bandwidth | Daily Cost | Monthly Cost |
|--------|----------|------------|--------------|
| **Free Tier** | 50GB free bandwidth | **$0.00** | **$0.00** |
| **Beyond Free Tier** | 50GB (~$0.10 - $0.16/day) | **$0.10 - $0.16** | **~$3 - $5** |

---

**5. Internet Gateway (IGW)**
**Purpose:**
- The Internet Gateway connects the internal VPC network to the internet, enabling EC2 to send and receive data externally.
- IGW is a critical component of AWS networking.

**Cost:**
- **Free of charge** per AWS pricing.

---

**6. IAM (Identity and Access Management) + VPC + Security Groups**
**Purpose:**
- IAM is used to manage access control for users and groups, ensuring security.
- In this workshop, *Amazon Virtual Private Cloud (VPC)* is used to create a **private network**, enabling the organization and management of resources within a dedicated network space on AWS.
VPC allows you to have complete control over your network environment, including IP address configuration, route tables, internet gateways, and subnets.
- In this Workshop, we will initialize VPC Instance including: 2 Availability Zones (AZs) to ensure high availability. 2 Public Subnets (for EC2 running applications), 2 Private Subnets (for Amazon DocumentDB). An Internet Gateway (IGW) to allow EC2 instances to communicate with the Internet. 
- Security Groups to manage secure access control. Security Groups act as a firewall, controlling network access to resources.

**Cost:**
- **Free of charge** per AWS pricing.

---

**7. Cost Summary**

**7.1. Cost Within Free Tier**  
| Service | Type | Daily Cost | Monthly Cost |
|---------|------|------------|--------------|
| **Amazon EC2** | t2.micro | **$0.00** | **$0.00** |
| **Amazon DocumentDB** | db.t3.medium | **$0.00** | **$0.00** |
| **Amazon S3** | 5GB storage | **$0.00** | **$0.00** |
| **Amazon CloudFront** | 50GB bandwidth | **$0.00** | **$0.00** |
| **IAM + VPC + Security Groups** | Free | **$0.00** | **$0.00** |
| **Total** |  | **$0.00** | **$0.00** |

---

**7.2. Cost Beyond Free Tier**  
| Service | Type | Daily Cost | Monthly Cost |
|---------|------|------------|--------------|
| **Amazon EC2** | t2.micro | **~$0.30** | **~$9** |
| **Amazon DocumentDB** | db.t3.medium | **~$0.66** | **~$20** |
| **Amazon S3** | 5GB storage | **~$0.03** | **~$1** |
| **Amazon CloudFront** | 50GB bandwidth | **~$0.10 - $0.16** | **~$3 - $5** |
| **IAM + VPC + Security Groups** | Free | **$0.00** | **$0.00** |
| **Total** |  | **~$1.10 - $1.15** | **~$33 - $35** |

---

**8. Conclusion**
- Within the Free Tier, the system operates at **$0 cost**.
- Once the Free Tier expires, the maintenance cost will be **approximately $33 - $35 per month**.
- If the system scales up, costs may increase, especially for DocumentDB, S3, and CloudFront usage.


### Workflow:

**1. Client sends a request**
- The user accesses the blog through a web browser.
- Static frontend data (ReactJS) is stored on Amazon S3 and delivered via AWS CloudFront to enhance loading speed.
- The request from the client is processed.

**2. CloudFront receives the request**
- CloudFront forwards the client’s API requests to the Internet Gateway, enabling connectivity to the backend server.
- The backend server processes the business logic.

**3. EC2 processes the request**
- The EC2 instance retrieves data from Amazon DocumentDB (MongoDB) to serve API requests, such as fetching blog posts, user information, and comments.
- Data storage and management take place.

**4. Querying data from Amazon DocumentDB**
- The MongoDB database is deployed on Amazon DocumentDB with a replication setup across Availability Zone 1 and Availability Zone 2, ensuring high availability and data durability.
- Access control and security measures are enforced.

**5. Returning results to the client**
- DocumentDB sends the requested data back to EC2.
- EC2 processes the data and returns the response to CloudFront.
- CloudFront may cache the response for faster delivery in subsequent requests.
- Finally, the response is sent to the client.

**6. Managing access with IAM**
- AWS IAM controls access permissions for users and services.
- IAM Users are assigned to IAM Groups, following specific Policies that restrict access to AWS resources such as EC2 and DocumentDB.

