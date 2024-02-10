---
title: "Day 85: Deploying a Web App on AWS ECS with ECR"
datePublished: Sat Feb 10 2024 13:09:22 GMT+0000 (Coordinated Universal Time)
cuid: clsg3fa4c000d0ajthxir06g3
slug: day-85-deploying-a-web-app-on-aws-ecs-with-ecr
canonical: https://arjunmenon.hashnode.dev/deploying-a-todo-app-on-aws-ecs-with-ecr
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707570513081/19b80081-bcaf-4982-91f0-927bad7b253c.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

In the world of cloud computing, deploying applications has become more efficient and scalable. Amazon Web Services (AWS) provides a range of services that enable developers to easily deploy and manage their applications. In this step-by-step guide, we'll walk through the process of deploying a Todo app on AWS ECS (Elastic Container Service) using ECR (Elastic Container Registry). This tutorial assumes you have a basic understanding of AWS services and have an AWS account.

## Step 1: Set Up an EC2 Instance

1. Launch an EC2 instance with Amazon Linux or any other suitable Amazon Machine Image (AMI).
    
2. SSH into the instance.
    

```bash
ssh -i your-key.pem ec2-user@your-instance-ip
```

## Step 2: Clone the Todo App Repository

Clone the Todo app repository from your version control system (e.g., GitHub).

```bash
git clone https://github.com/your-username/todo-app.git
cd todo-app
```

## Step 3: Set Up ECR Repository

1. Navigate to the AWS Management Console and open the Elastic Container Registry (ECR).
    
2. Create a new repository named `node-app`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511171469/e928a615-1bd5-4d8d-87fc-c7169c641e14.png?auto=compress,format&format=webp align="left")

## Step 4: Install Docker and AWS CLI on EC2 Instance

Install Docker and the AWS CLI on your EC2 instance.

```bash
sudo apt update -y
sudo apt install docker.io
sudo usermod -a -G docker ubuntu
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

## Step 5: Authenticate Docker with ECR

Run the following command to retrieve an authentication token and authenticate your Docker client with your ECR registry.

```bash
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/u1o8l9k6
```

## Step 6: Build and Push Docker Image to ECR

Build your Docker image and push it to the ECR repository.

```bash
docker build -t node-app .
docker tag node-app:latest public.ecr.aws/u1o8l9k6/node-app:latest
docker push public.ecr.aws/u1o8l9k6/node-app:latest
```

## Step 7: Create ECS Cluster

1. Navigate to ECS in the AWS Management Console.
    
2. Create a new cluster named `node-todo-cluster`.
    
3. Choose Fargate as the launch type.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511284959/dc30802f-734b-47ba-b053-2b418a4faefa.png?auto=compress,format&format=webp align="left")

## Step 8: Create Task Definition and Deploy

1. Create a new task definition named `node-todo-app-task-definition`.
    
2. Select the task definition and click on "Deploy," then "Run Task."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511330000/424cd335-80be-4f76-8371-4bd23e6c0181.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511342831/fe4e4f07-6e65-4b34-a77b-ca62a0f355a4.png?auto=compress,format&format=webp align="left")

## Step 9: Check the App

1. Once the task is running, note the public IP of your Fargate instance.
    
2. Open a web browser and navigate to `<public-ip>:8000` to check if the Todo app is running.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511392237/93e55d7c-1601-4b29-afe3-165145467460.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703511423775/a22325b7-c56f-42b9-b7f0-002af8a84063.png?auto=compress,format&format=webp align="left")

## Conclusion

Congratulations! You have successfully deployed a Todo app on AWS ECS using ECR. This step-by-step guide covered setting up an EC2 instance, cloning the Todo app repository, configuring ECR, installing Docker and AWS CLI, building and pushing a Docker image, creating an ECS cluster, defining tasks, and finally deploying and checking the app. This workflow provides a scalable and efficient way to deploy containerized applications on AWS.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.