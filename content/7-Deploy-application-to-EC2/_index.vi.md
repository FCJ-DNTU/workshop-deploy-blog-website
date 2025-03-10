+++
title = "Triển khai ứng dụng lên EC2"
date = 2025
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

#### 1. Cài đặt Git và NodeJS

- Cài đặt Git

    ```shell
    $ sudo apt install -y git
    $ git --version
    ```

- Cài đặt NodeJS và npm

    ```shell
    $ curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    $ sudo apt install -y nodejs
    $ node -v
    $ npm -v
    ```

- Cài đặt PM2 để quản lý ứng dụng

    ```shell
    $ sudo npm install -g pm2
    $ pm2 -v
    ```

#### 2. Cài đặt mongosh và kết nối đến Amazon DocumentDB 
- Cài đặt **mongosh**

    ```shell
    $ wget -qO - https://pgp.mongodb.com/server-6.0.asc | sudo tee /usr/share/keyrings/mongodb-server-key.asc

    $ echo "deb [signed-by=/usr/share/keyrings/mongodb-server-key.asc] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

    $ sudo apt update
    $ sudo apt install -y mongodb-mongosh
    $ mongosh --version
    ```

- Kiểm tra kết nối với **DocumentDB**
- Vào giao diện **Cluster** của **Amazon DocumentDB**, sau đó chọn cluster đã tạo
    ![choose-cluster](/images/7-deploy-application-to-ec2/7.3.png)

- Tải file **global-bundle.pem** về EC2 và kết nối tới DocumentDB trong EC2 (thay thế **insertYourPassword** trong chuỗi kết nối thành password bạn đã đặt cho DocumentDB)

    ![connect](/images/7-deploy-application-to-ec2/7.4.png)
    ![connect2](/images/7-deploy-application-to-ec2/7.5.png)

- Gõ lệnh **show dbs**, bạn sẽ thấy hiện tại trong DocumentDB chưa có database nào hết
    ![check](/images/7-deploy-application-to-ec2/7.6.png)



#### 3. Clone Repository

```shell
$ git clone https://github.com/NguyenNhatHuynh/fullStack-Blog.git
```

- Dùng lệnh **`ls`** để kiểm tra xem project đã được clone về chưa
![clone-project](/images/7-deploy-application-to-ec2/7.1.png)

- Vào thư mục **fullStack-Blog**. Sau đó, cài đặt các dependencies

    ```shell
    $ cd fullStack-Blog
    $ ls
    $ cd server
    $ npm install
    ```
    ![clone-project](/images/7-deploy-application-to-ec2/7.2.png)

#### 4. Thêm biến môi trường (.env)

  - Tạo file **.env** chứa thông tin kết nối database và cấu hình ứng dụng

    ```shell
    $ cd fullStack-Blog
    $ cd server
    $ touch .env
    $ nano .env
    ```
    ![env](/images/7-deploy-application-to-ec2/7.7.png)

  - Thêm các biến môi trường
  Tải file **.env** và thêm các biến môi trường vào
  **[.env](https://drive.google.com/file/d/1hfSqTRdFHizg6yuORS67atge8BDl4RpK/view?usp=sharing)**

    ![build](/images/7-deploy-application-to-ec2/7.8.png)

#### 5. Chạy ứng dụng

  - Chạy ứng dụng với **pm2**

    ```
    pm2 start npm --name "blog-web" -- run start
    pm2 save
    pm2 startup
    ```

  - Kiểm tra ứng dụng có chạy không:
    ```
    pm2 list
    ```
    ![build](/images/7-deploy-application-to-ec2/7.9.png)



#### 6. Kiểm tra deployment

  - Mở trình duyệt và truy cập

  ```
     http://s3-blog-workshop.s3-website-us-east-1.amazonaws.com/
  ```

  ![build](/images/7-deploy-application-to-ec2/7.10.png)