+++
title = "Workshop: Deploying a Fullstack Blog Website on AWS EC2 with DocumentDB, CloudFront & S3"
date = 2025
weight = 1
chapter = false
+++

# Workshop: Deploying a Fullstack Blog Website on AWS EC2 with DocumentDB, CloudFront & S3

### Overview

In this workshop, you will learn how to deploy a Fullstack Blog Website on AWS using EC2, leverage DocumentDB as a NoSQL database, and optimize performance and costs with CloudFront.

![Workshop Architecture](/images/workshop_architecture.png)

### Objectives:

- Understand how to create and configure EC2, DocumentDB, CloudFront, and IAM on AWS.
- Learn how to deploy a MERN fullstack blog application on EC2.
- Connect and interact with DocumentDB from EC2, including data migration from MongoDB to DocumentDB.
- Configure CloudFront to offload traffic from EC2 and enhance performance.
- Manage access control between AWS services using IAM.

### Prerequisites:

- An AWS account with IAM access permissions.
- A computer with an SSH client (e.g., Terminal or PuTTY).

---

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
- VPC (Virtual Private Cloud) creates an isolated network environment for the system, ensuring security and resource management flexibility.
- Security Groups act as a firewall, controlling network access to resources.

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

---

### Workshop Content

1. [Introduction](1-Introduction/)
2. [Restricting Access with IAM Service](2-restrict-access/)
3. [Prepare VPC](3-create-vpc-instance/)
4. [Create EC2 Instance](4-create-ec2-instance/)
5. [Create S3](5-create-s3-bucket/)
6. [Create AWS DocumentDB Service](6-create-documentdb/)
7. [Deploying the Application to EC2](7-deploy-the-application-to-ec2/)
8. [Create CloudFront](8-create-cloudfront/)
9. [Cleaning Up Resources](9-clean-up/)
