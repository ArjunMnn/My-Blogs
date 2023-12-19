---
title: "Day 45: Deploy Wordpress website on AWS"
datePublished: Tue Dec 19 2023 06:51:05 GMT+0000 (Coordinated Universal Time)
cuid: clqbzkoe7000s08la7uoy3daf
slug: day-45-deploy-wordpress-website-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702968637701/a786d3e4-494e-4e64-9752-e1192ddd5d74.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

WordPress, the world's most popular Content Management System (CMS), can be seamlessly deployed on Amazon Web Services (AWS) for a scalable and reliable web experience. In this blog post, we'll guide you through the process of deploying a WordPress website on AWS, leveraging the power of Amazon EC2 for hosting and Amazon RDS for MySQL as the database backend.

## Task-01: Create an RDS for MySQL Database

Before configuring the WordPress site, let's set up the MySQL database using Amazon RDS.

### Step 1: Log in to AWS Management Console

Navigate to the AWS Management Console and log in to your AWS account.

### Step 2: Access Amazon RDS

Click on the "Services" dropdown, select "RDS" under the Database category.

### Step 3: Create a New RDS Instance

1. Click on "Create database."
    
2. Choose "MySQL" as the database engine.
    
3. Select the desired version and template (choose the "Free tier" if applicable).
    
4. Configure the instance details, including DB instance identifier, master username, and password.
    
5. Set up additional configurations such as DB instance size, storage, and networking.
    
6. Review your settings and click "Create database."
    

### Step 4: Wait for RDS Instance to be Available

The RDS instance creation process may take a few minutes. Once it's available, note down the endpoint for future reference.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968280058/545d9000-a3d9-44e6-887c-9dd9a57e5e75.png align="center")

## Task-02: Set Up Amazon EC2 Instance for WordPress

### Step 1: Navigate to EC2 Dashboard

1. Go to the AWS Management Console.
    
2. Click on "Services" and select "EC2" under the Compute category.
    

### Step 2: Launch a New EC2 Instance

1. Click "Launch Instance."
    
2. Choose an Amazon Machine Image (AMI) – select an image that suits your requirements.
    
3. Select an instance type, configure instance details, storage, and add tags as needed.
    
4. Configure security groups to allow traffic on port 80 (HTTP) and port 443 (HTTPS).
    
5. Review your configurations and launch the instance.
    

### Step 3: Connect to EC2 Instance

1. Once the instance is running, connect to it using SSH.
    
2. Connect the EC2 instance to the RDS instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968330053/e28e95d5-477f-4036-bd8b-17448d906d5d.png align="center")
    

## Task-03: Install and Configure WordPress

### Step 1: Download and Install WordPress

1. SSH into your EC2 instance.
    
2. Download and install WordPress:
    
    ```bash
    sudo apt-get update
    sudo apt-get install apache2 mysql-server php php-mysql libapache2-mod-php php-cli
    sudo service apache2 start
    sudo service mysql start
    sudo wget https://wordpress.org/latest.tar.gz
    sudo tar -xzf latest.tar.gz -C /var/www/html/
    ```
    

### Step 2: Configure WordPress

1. Create a WordPress configuration file:
    
    ```bash
    cd /var/www/html/wordpress
    sudo cp wp-config-sample.php wp-config.php
    ```
    
2. Edit the configuration file with your RDS database details:
    

```bash
sudo vim wp-config.php
```

Update the following lines with your RDS database details:

```bash
define('DB_NAME', 'your_database_name');
define('DB_USER', 'your_database_user');
define('DB_PASSWORD', 'your_database_password');
define('DB_HOST', 'your_rds_endpoint');
```

1. Save and close the file.
    

### Step 3: Access WordPress

1. Open your web browser and navigate to your EC2 instance's public IP or domain.
    
2. Complete the WordPress installation by entering the required details.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968206269/265061ec-3af6-45a5-b5fc-7d797dfb9a28.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702968220118/1e5b529c-df53-4986-a81c-be083bf16354.png align="center")
    

## Conclusion

Congratulations! You've successfully deployed a WordPress website on AWS, integrating Amazon EC2 for hosting and Amazon RDS for MySQL as the backend database. Stay tuned for more DevOps adventures in the remaining days of the 90 Days of DevOps challenge!

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.