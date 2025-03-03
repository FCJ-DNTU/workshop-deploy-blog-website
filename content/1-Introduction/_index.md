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

