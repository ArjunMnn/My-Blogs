---
title: "Day 44: Relational Database Service in AWS"
seoDescription: "Discover the simplicity of deploying a two-tier application on AWS. Set up a Free tier MySQL RDS instance, EC2, and IAM roles for seamless cloud experience."
datePublished: Mon Dec 18 2023 05:48:45 GMT+0000 (Coordinated Universal Time)
cuid: clqahwnc0000108l3ceg62hkd
slug: day-44-relational-database-service-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702878425192/ae2523e0-fe9a-4e87-8ae3-5aadcbbfb0a2.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Amazon Relational Database Service (Amazon RDS) is a fully managed relational database service provided by Amazon Web Services (AWS). It allows you to set up, operate, and scale a relational database in the cloud with ease. In this blog post, we will walk through the process of creating a Free tier RDS instance of MySQL, setting up an EC2 instance, creating an IAM role with RDS access, and connecting the EC2 instance to the RDS instance.

For those interested in deploying a comprehensive two-tier application architecture on AWS, you may also want to check out our earlier guide: [**Deploying a Two-Tier Application with MySQL on Amazon RDS**](https://arjunmenon.hashnode.dev/day-4-deploying-a-two-tier-web-app-with-mysql-on-amazon-rds). This tutorial provides valuable insights into the benefits of a two-tier architecture and covers the essential steps for setting up a seamless connection between an EC2 instance and an Amazon RDS database.

## Step 1: Create a Free Tier RDS Instance of MySQL

1. Log in to your AWS Management Console.
    
2. Navigate to the Amazon RDS service.
    
3. Click on "Create database."
    
4. Choose the "MySQL" engine and select the "Free tier" template.
    
5. Configure the settings, including DB instance identifier, master username, and password.
    
6. Set the remaining configurations such as DB instance size, storage, and networking options.
    
7. Review your configurations and click "Create database."
    
8. Wait for the RDS instance to be created. Once it's available, note down the endpoint for future reference.
    

## Step 2: Create an EC2 Instance

1. Navigate to the Amazon EC2 service in the AWS Management Console.
    
2. Click on "Instances" in the left-hand navigation pane.
    
3. Click "Launch Instance."
    
4. Choose an Amazon Machine Image (AMI), such as Amazon Linux 2 or Ubuntu.
    
5. Select an instance type, and configure instance details, storage, and security groups.
    
6. Review your configurations and click "Launch."
    
7. Create or select an existing key pair to securely connect to your EC2 instance.
    
8. Launch the instance and wait f
    
9. or it to become running.
    

## Step 3: Create an IAM Role with RDS Access

1. Navigate to the IAM service in the AWS Management Console.
    
2. Click on "Roles" in the left-hand navigation pane.
    
3. Click "Create role."
    
4. Choose "Amazon EC2" as the service that will use this role.
    
5. Attach the "AmazonRDSFullAccess" policy to the role to grant RDS access.
    
6. Review the configuration and click "Create role."
    

## Step 4: Assign the Role to EC2

1. Go back to the EC2 service in the AWS Management Console.
    
2. Select the EC2 instance you created earlier.
    
3. Click on "Actions" &gt; "Security" &gt; "Modify IAM Role."
    
4. Choose the IAM role you created in Step 3 and save the changes.
    

## Step 5: Connect EC2 to RDS

1. SSH into your EC2 instance using the key pair you created.
    
2. Install the MySQL client on the EC2 instance:
    

```bash
sudo apt-get install mysql-client
```

1. Use the following command to connect to your RDS instance from the EC2 instance, replacing `<RDS_ENDPOINT>`, `<DB_USERNAME>`, and `<DB_PASSWORD>` with your actual values:
    
2. ```bash
    mysql -h <RDS_ENDPOINT> -u <DB_USERNAME> -p<DB_PASSWORD>
    ```
    
    You will be prompted to enter the password.
    
3. Once connected, you can start working with your MySQL database on RDS from your EC2 instance.
    

Congratulations! You have successfully set up an Amazon RDS instance, an EC2 instance, created an IAM role with RDS access, assigned the role to EC2, and connected the EC2 instance to the RDS instance using a MySQL client. This hands-on tutorial should help you get started with managing relational databases on AWS.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.