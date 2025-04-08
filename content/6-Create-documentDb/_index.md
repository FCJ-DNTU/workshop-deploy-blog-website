+++
title = "Create AWS DocumentDB Service"
date = 2025
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

![aws-documentdb.png](/images/6-create-documentdb/document-db.jpeg)

#### AWS DocumentDB

**Amazon DocumentDB** Amazon DocumentDB is a NoSQL database provided by AWS, storing data in JSON format, compatible with MongoDB. This is a fully managed service, helping you run critical applications without worrying about infrastructure management, saving time and costs.


#### Benefits of using DocumentDB:

- **MongoDB compatibility:** Can use MongoDB tools and code, easy to migrate data.
- **Good performance, easily scalable:** Fast processing, automatically increases capacity when needed.
- **Easy to manage:** AWS handles all backups and maintenance, so you can focus on your application.

#### Pricing of Amazon DocumentDB

The price of **Amazon DocumentDB** is calculated based on:
- **Instances (On-Demand Instances):** Pay by the hour, depending on the instance type you use.
Read/write data (Database I/O): Charged based on the number of accesses, with a rate per million accesses.
- **Storage (Database Storage):** Pay per GB per month.
- **Backup (Backup Storage):** Additional charge if backup storage exceeds the main storage, also per GB/month.

Pricing calculation for **Amazon DocumentDB**:

- **Standard (Pay-per-I/O-used):**
    - Suitable for applications with low to moderate data access (low - medium I/O).
    - Charges based on: Instances, Read/Write (I/O), Storage, Backup.
    - Ideal if I/O costs are below 25% of the total cost.
- **I/O-Optimized (I/O fees included in instance price)**
    - Suitable for applications with high data access (high I/O).
    - Charges only for: Instances, Storage, Backup – no separate I/O fees.
    - Easy to predict costs, suitable if I/O accounts for over 25% of the total cost.


#### Which configuration should this workshop choose?
- We will choose **Amazon DocumentDB Standard** to save costs, because:
    - Low queries at the start, helping to save costs.
    - Only pay for the actual read/write (I/O) usage.
    - Easy to upgrade to I/O-Optimized if queries increase later.

#### Create a DB Instance on AWS

1. Log in to the **AWS Management Console** and open **Amazon DocumentDB**

2. Create a **DocumentDB Cluster**
   ![Cluster-interface.png](/images/6-create-documentdb/6.1.png)

3. In **Create Amazon DocumentDB cluster**, fill in the following information:

   - **Cluster type**: Instance-based cluster
   - **Cluster identifier**: `docdb-blog-workshop`
   - **Engine version**: Select the latest version
   - **Cluster storage configuration**: Amazon DocumentDB Standard
   - **Instance class**: db.t3.medium
   - **Number of instances**: 2 (1 Primary + 1 Replica)
   - **Connectivity**: Don’t connect to an EC2 compute resource
   - **Username**: `user123`
   - Select **Self managed**
   - **Password**: `user1234`
   - **Confirm Password**: `user1234`
   - **Subnet group**: Select the subnet group created in **3.3**
   - **VPC security groups**: **private-sg-documentdb (VPC)**
   - **Deletion protection**: Check **Enable deletion protection**
   - Review the settings and click **Create cluster**
     ![create-1.png](/images/6-create-documentdb/6.2.png)
     ![create-2.png](/images/6-create-documentdb/6.3.png)
           ![create-1.png](/images/6-create-documentdb/6.4.png)
     ![create-2.png](/images/6-create-documentdb/6.5.png)
     ![create-1.png](/images/6-create-documentdb/6.6.png)
     ![create-2.png](/images/6-create-documentdb/6.7.png)
   - Wait a few minutes, and it will switch to **Cluster** creation successful
     ![create-2.png](/images/6-create-documentdb/6.8.png)

4. Check the connection from EC2 to DocumentDB

- Go to the newly created cluster, select the **Configuration** tab, and copy the **Cluster endpoint**
 ![create-2.png](/images/6-create-documentdb/6.9.png)
- Go to EC2, click the **Connect** button, and click **Connect** in the **EC2 Instance Connect** tab

    ```shell
    $ sudo apt-get install -y netcat
    $ nc -zv docdb-blog-workshopv1.cluster-cl8uqi4yidxz.ap-southeast-1.docdb.amazonaws.com 27017
    ```
    ![success.png](/images/6-create-documentdb/6.10.png)

### **Completed!**