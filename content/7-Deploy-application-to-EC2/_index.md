+++
title = "Deploy application to EC2"
date = 2025
weight = 7
chapter = false
pre = "<b>7. </b>"
+++


#### 1. Install Git and NodeJS

- Install Git

    ```shell
    $ sudo apt install -y git
    $ git --version
    ```

- Install NodeJS and npm

    ```shell
    $ curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    $ sudo apt install -y nodejs
    $ node -v
    $ npm -v
    ```

- Install PM2 to manage the application

    ```shell
    $ sudo npm install -g pm2
    $ pm2 -v
    ```

#### 2. Install mongosh and connect to Amazon DocumentDB
- Install **mongosh**

    ```shell
    $ wget -qO - https://pgp.mongodb.com/server-6.0.asc | sudo tee /usr/share/keyrings/mongodb-server-key.asc

    $ echo "deb [signed-by=/usr/share/keyrings/mongodb-server-key.asc] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

    $ sudo apt update
    $ sudo apt install -y mongodb-mongosh
    $ mongosh --version
    ```

- Check connection with **DocumentDB**
- Go to the **Cluster** interface of **Amazon DocumentDB**, then select the created cluster
    ![choose-cluster](/images/7-deploy-application-to-ec2/7.3.png)

- Download the **global-bundle.pem** file to EC2 and connect to DocumentDB in EC2 (replace **insertYourPassword** in the connection string with the password you set for DocumentDB)

    ![connect](/images/7-deploy-application-to-ec2/7.4.png)
    ![connect2](/images/7-deploy-application-to-ec2/7.5.png)

- Type the command **show dbs**, you will see that there are no databases in **DocumentDB** yet
    ![check](/images/7-deploy-application-to-ec2/7.6.png)


#### 3. Clone Repository

```shell
$ git clone https://github.com/NguyenNhatHuynh/fullStack-Blog.git
```

- Use the **`ls`** command to check if the project has been cloned successfully
![clone-project](/images/7-deploy-application-to-ec2/7.1.png)

- Navigate to the **fullStack-Blog**. Then, install dependencies

    ```shell
    $ cd fullStack-Blog
    $ ls
    $ cd server
    $ npm install
    ```
    ![clone-project](/images/7-deploy-application-to-ec2/7.2.png)

#### 4. Add environment variables (.env)

  - Create a **.env** file containing database connection information and application configuration

    ```shell
    $ cd fullStack-Blog
    $ cd server
    $ touch .env
    $ nano .env
    ```
    ![env](/images/7-deploy-application-to-ec2/7.7.png)

  - Add environment variablesDownload the **.env** file and add the environment variables **.env**
  **[.env](https://drive.google.com/file/d/1hfSqTRdFHizg6yuORS67atge8BDl4RpK/view?usp=sharing)**

    ![build](/images/7-deploy-application-to-ec2/7.8.png)

#### 5. Run the application

  - Run the application using **pm2**

    ```
    pm2 start npm --name "blog-web" -- run start
    pm2 save
    pm2 startup
    ```

  - Check if the application is running:
    ```
    pm2 list
    ```
    ![build](/images/7-deploy-application-to-ec2/7.9.png)



#### 6. Verify deployment

  - Open a browser and access

  ```
     http://s3-blog-workshop.s3-website-us-east-1.amazonaws.com/
  ```

  ![build](/images/7-deploy-application-to-ec2/7.10.png)
