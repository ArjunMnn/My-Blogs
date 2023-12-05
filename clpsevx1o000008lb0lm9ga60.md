---
title: "Day 4: Deploying a Two-Tier Web App with MySQL on Amazon RDS"
seoDescription: "Day 4 tutorial unveils the power of AWS as we deploy a Dockerized web app with MySQL on Amazon RDS. Elevate your cloud skills with this comprehensive guide!"
datePublished: Tue Dec 05 2023 14:04:21 GMT+0000 (Coordinated Universal Time)
cuid: clpsevx1o000008lb0lm9ga60
slug: day-4-deploying-a-two-tier-web-app-with-mysql-on-amazon-rds
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701785000894/5fbbe07c-8c0c-47fd-b9fc-9d233fd76384.png
tags: cloud, software-development, docker, aws, devops

---

Welcome to Day 4 of our AWS mastery journey! Today, we're embarking on an exciting project - deploying a two-tier application. Tier 1 features a Dockerized web app, while Tier 2 hosts a MySQL server on Amazon RDS. Let's dive into the world of containers, AWS, and seamless cloud integration.

### **Setting the Stage: Unleashing the Power of Docker and AWS**

**Defining Your Project:** Start by conceptualizing your project. Our goal is to create a two-tier application where the first tier is a Dockerized web app, and the second tier is a MySQL server hosted on Amazon RDS.

### **Tier 1: Dockerized Web App**

1. **Installation:** Begin by installing Docker on your EC2 instance. This will be the backbone of your containerized web app.
    
2. **Cloning the Repository:** Clone [this repository](https://github.com/LondheShubham153/two-tier-flask-app/tree/master) which contains the Dockerfile.
    
3. **Image Creation:** Execute `docker build` to create an image from your Dockerfile. This encapsulates your app and its dependencies.
    

### **Tier 2: MySQL on Amazon RDS**

**Configuring Amazon RDS:**

1. **Database Instance Creation:** Navigate to the AWS Management Console, select Amazon RDS, and create a new database instance. Choose MySQL as the engine.
    
2. **Instance Settings:** Define your instance details, including DB credentials, storage, and network configurations.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701784107249/f01bef96-3a4c-44cb-8b96-df202fa7c6d3.png align="center")

**Connecting EC2 to RDS:**

1. Go to your RDS database. Scroll to the "Connected compute resources" section and add your ec2 instance.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701784223323/9d4a31f5-89b9-4776-aaf7-0ef9d6e56c80.png align="center")
    
3. In your EC2 instance, run the following commands:
    
4. ```plaintext
      # Install mysql client
      sudo apt update
      sudo apt install mysql-client
      
      # Connecting your ec2 instance to the rds database.
      mysql -u admin -h <endpoint> -P 3306 -p
    ```
    
5. MySQL console will open. In the MySQL console, run the following:
    
6. ```plaintext
      create database aws;
      CREATE TABLE messages (
          id INT AUTO_INCREMENT PRIMARY KEY,
          message TEXT
      );
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701784577358/5475c83d-8da7-429c-b555-4a335c73026f.png align="center")
    

### **Deployment: Bringing Your Application to Life**

1. **Running the docker container:** Run the docker container we created before with MySQL environment variables as below
    
2. ```plaintext
      sudo docker run -d -p 5000:5000 -e MYSQL_HOST=<endpoint> -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin123 -e MYSQL_DB=aws two-tier
    ```
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701784753705/4535bd75-911b-4039-8bca-24ef9ca334ac.png align="center")
    
4. **Testing the Full Setup:** Validate your two-tier application in the browser, by going on the URL `http://<ec2-public-ip>:5000`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701784880208/33df214f-0796-4a12-99e9-ed34bbc344dd.png align="center")

### **Conclusion**

Congratulations on successfully deploying a two-tier application on AWS! Today's journey has taken you through the intricacies of Docker, Amazon RDS, and the orchestration of cloud resources.

Stay tuned for Day 5, where we'll explore advanced AWS services, propelling your cloud expertise even further!

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.