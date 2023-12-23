---
title: "Day 47: AWS Elastic Beanstalk"
datePublished: Sat Dec 23 2023 06:46:08 GMT+0000 (Coordinated Universal Time)
cuid: clqhp5pa5000809lab0i69fbs
slug: day-47-aws-elastic-beanstalk
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703313928097/06019a25-17b9-4ee5-9af4-2b82894d359a.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Welcome to this step-by-step tutorial on deploying a game using AWS Elastic Beanstalk. In this guide, we will walk through the process of creating an application, setting up a web server environment, and deploying a Dockerized game using Elastic Beanstalk.

### Prerequisites

Before you begin, make sure you have:

* An AWS account with the necessary permissions.
    
* Docker installed on your local machine.
    
* A Dockerfile for your game setup.
    

## Step 1: Login to the AWS Console

1. Open your web browser and navigate to the [AWS Management Console](https://aws.amazon.com/).
    
2. Log in with your AWS account credentials.
    

## Step 2: Search for the Elastic Beanstalk Service

1. In the AWS Management Console, use the search bar at the top and type "Elastic Beanstalk."
    
2. Click on the Elastic Beanstalk service in the search results.
    

## Step 3: Create a New Application

1. In the Elastic Beanstalk dashboard, click "Create Application."
    

## Step 4: Select Web Server Environment

1. Choose the type of environment that will host your application. Here, we select the web server environment.
    

## Step 5: Name the Application

1. Provide a name for your application.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703313152361/7245123b-9fee-4fc4-924e-84abcb7ffe99.png align="center")

## Step 6: Name Environment and Add Description

1. Assign a name to the environment and include a brief description.
    
2. You can leave the domain name blank for an auto-generated value.
    

## Step 7: Choose Docker Platform

1. Select the Managed Platform and specify Docker as the platform type.
    

## Step 8: Upload Docker File

1. Opt for "Upload your code" and upload the Dockerfile you've created. Here's an example Dockerfile:
    
2. ```bash
    FROM ubuntu:22.04
    
    RUN apt-get update
    RUN apt-get install -y nginx zip curl
    
    RUN echo "daemon off;" >>/etc/nginx/nginx.conf
    RUN curl -o /var/www/html/master.zip -L https://github.com/ArjunMnn/2048-game/archive/refs/heads/master.zip
    RUN cd /var/www/html/ && unzip master.zip && mv 2048-game-master/* . && rm -rf 2048-game-master master.zip
    
    EXPOSE 80
    
    CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703313393244/a92f6ef8-f42c-400d-a032-bc2bccdc1bae.png align="center")

## Step 9: Select Free Tier Eligible Option

1. Choose the option that falls under the AWS Free Tier to ensure cost-effective deployment.
    

## Step 10: Configure Service Access

1. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703313512248/aafaa6e5-b7be-48b5-8d0a-82ed807e1738.png align="center")
    

## Step 11: Review and Submit

1. Review the settings and click "Create" to confirm the deployment.
    

## Step 12: Initiate Environment Creation

1. The process of creating the environment will begin. Wait for the deployment to complete.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703313866743/8cbd4291-dcc3-4778-a2f6-03265ce20693.png align="center")

## Step 13: Load the Domain

1. After successful environment creation, access your game using the provided domain.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703313793145/e1676f33-527d-4437-aad6-93f0c0f1fc20.png align="center")

## Conclusion

Congratulations! You have successfully deployed a game using AWS Elastic Beanstalk. Your game should now be accessible via the provided domain, providing a scalable and cost-effective hosting solution.