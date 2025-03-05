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
