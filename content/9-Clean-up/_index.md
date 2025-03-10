+++
title = "Clean Up Resources"
date = 2025
weight = 9
chapter = false
pre = "<b>9. </b>"
+++


#### 1. Delete CloudFront Distribution

- Go to [CloudFront](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home#/distributions)
- Select the **distribution** to delete
- Click **Disable**
- Once **Disabled successfully**, click **Delete** to remove it
  ![delete-distribution.png](/images/9-clean-up/9.1.png)
  ![delete-distribution.png](/images/9-clean-up/9.2.png)


#### 2. Delete DocumentDB Cluster

- Go to Amazon DocumentDB, section
  [Clusters](https://ap-southeast-1.console.aws.amazon.com/docdb/home?region=ap-southeast-1#clusters)
- Select the **Cluster to delete**
- Click the **Action** dropdown, then select **Delete**
- A confirmation dialog will appear
{{% notice note %}}
**Note**: Your **Amazon DocumentDB** cluster has **deletion protection** enabled, preventing direct deletion. To delete it, go to **Modify**, disable **Deletion Protection**, and then try deleting it again.
{{% /notice %}}
- Select **close**
![delete-cluster.png](/images/9-clean-up/9.3.1.png)
- Select **docdb-blog-workshopv1**, then select **Modify**
![delete-cluster.png](/images/9-clean-up/9.3.2.png)
- Then **Disable Deletion protection**, select **continue**   
![delete-cluster.png](/images/9-clean-up/9.3.3.png)
- Select **Apply during**, select **Modify cluster**
![delete-cluster.png](/images/9-clean-up/9.3.4.png)

- Repeat the first steps, Select the **Cluster to delete**, Click the **Action** dropdown, then select **Delete**, 

- A confirmation dialog will appear
- Name the **Snapshot**: `blog-workshopv1` and type `delete entire cluster`
![confirmation_dialog.png](/images/9-clean-up/9.3.5.png)

- After **successfully deleting the Cluster**, go to
  [Snapshots](https://ap-southeast-1.console.aws.amazon.com/docdb/home?region=ap-southeast-1#snapshots) to delete the
  snapshot
- Select the **Snapshot to delete**
- Click the **Action** dropdown, then select **Delete**
  ![delete-snapshot.png](/images/9-clean-up/9.5.png)



#### 3. Delete EC2 Resources

- Go to [EC2 Instances](https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:)
- Select the **Instance**, click the **Instance state** dropdown, and choose **Terminate**.
  ![delete-ec2.png](/images/9-clean-up/9.6.png)

#### 4. Delete VPC Resources

- Go to [Your VPCs](https://ap-southeast-1.console.aws.amazon.com/vpcconsole/home?region=ap-southeast-1#vpcs:)
- Select the **Instance**, then click **Actions** and choose **Delete VPC**.
  ![delete-vpc.png](/images/9-clean-up/9.7.png)


#### 5. Clean up IAM Resources

- Access **Root user**.
- Go to [IAM Service](https://us-east-1.console.aws.amazon.com/iam/home?region=ap-southeast-1#/home)
- Under **Policies**, select the **Policy** and choose **Delete**

  ![delete-policy.png](/images/9-clean-up/9.8.png)

- Under **User groups**, select the **Groups** and click **Delete**
  ![delete-groups.png](/images/9-clean-up/9.9.png)

- Under **Users**, select the user and click **Delete**.

  ![delete-users.png](/images/9-clean-up/9.9.1.png)

#### 5. Delete S3
- Access the interface of **S3**
- Select **General purpose buckets**
- Select the **Bucket name** you created
- Select **Delete**
![Clean S3.png](/images/9-clean-up/9.9.2.png)

- In the **Delete bucket** interface
    - Select **Empty bucket**
    ![Clean S3.png](/images/9-clean-up/9.9.3.png)


- In the **Empty bucket** interface
    - Type `permanently delete` in confirm
    - Select **Empty**
    ![Clean S3.png](/images/9-clean-up/9.9.4.png)

- After **Empty** is successful
    - Select **Bucket**
    - Re-select the Bucket name that you want to delete
    - Select **Delete**
    ![Clean S3.png](/images/9-clean-up/9.9.5.png)

- In the **Delete bucket** interface
    - Copy the **Bucket name** that you created
    - Paste in **confirm**
    - Select **Delete bucket**
    ![Clean S3.png](/images/9-clean-up/9.9.6.png)


#### Done    



