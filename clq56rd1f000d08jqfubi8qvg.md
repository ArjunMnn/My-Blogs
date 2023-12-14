---
title: "Day 38 & 39: Getting Started with AWS Basics"
seoDescription: "Set up IAM users, launch Linux instances, and build a DevOps Avengers team. Strengthen your foundation for DevOps success."
datePublished: Thu Dec 14 2023 12:37:51 GMT+0000 (Coordinated Universal Time)
cuid: clq56rd1f000d08jqfubi8qvg
slug: day-38-39-getting-started-with-aws-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702562910041/e8ad76ef-8560-4610-bdf1-759c7b24acb8.png
tags: cloud, software-development, aws, software-engineering, 90daysofdevops

---

## Introduction

Welcome to Day 38 and Day 39 of your AWS learning journey! In this tutorial, we'll guide you through hands-on tasks to master Identity and Access Management (IAM), launch EC2 instances, set up Jenkins, and deploy Docker. Whether you're a beginner or looking to enhance your AWS skills, follow these step-by-step instructions for a comprehensive understanding.

---

## Task 1: Empowering Your IAM User for EC2 Access

### Step 1: Create an IAM User with EC2 Access

1. Navigate to the AWS Management Console.
    
2. Open the IAM dashboard and click on "Users."
    
3. Click "Add user," enter a username, and select "Programmatic access."
    
4. Attach the "AmazonEC2FullAccess" policy.
    
5. Review and create the user, noting the access key and secret key.
    

### Step 2: Launch a Linux EC2 Instance with Jenkins and Docker

Create a Shell Script, e.g., [`setup.sh`](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html):

```bash
#!/bin/bash

# Install Jenkins
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
sudo yum install -y jenkins

# Install Docker
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -aG docker ec2-user
```

Make the script executable and run it:

```bash
chmod +x setup.sh
./setup.sh
```

This script installs Jenkins and Docker on your EC2 instance.

---

## Task 2: Assembling Your DevOps Avengers

### Step 1: Create DevOps IAM Users

1. Head to the IAM dashboard.
    
2. Create three users: DevOpsUser1, DevOpsUser2, and DevOpsUser3.
    
3. Attach policies such as "AmazonEC2FullAccess" to each user.
    

### Step 2: Group Users into DevOps Groups

1. In the IAM dashboard, navigate to "Groups."
    
2. Create a group named "DevOpsGroup."
    
3. Add the three DevOps users to this group.
    

---

## Task 3: Launching Jenkins on EC2

### Step 1: Launch an EC2 Instance with Jenkins

1. Go to the EC2 dashboard.
    
2. Launch an instance with Amazon Linux 2 AMI.
    
3. In the user data section, add:
    

```bash
#!/bin/bash
sudo yum install -y jenkins
sudo service jenkins start
sudo chkconfig jenkins on
```

1. Complete the instance creation process.
    

### Step 2: Access Jenkins Page

1. Once the instance is running, note its public IP address.
    
2. In your browser, enter `http://<your-instance-ip>:8080`.
    
3. Retrieve the Jenkins initial password from the instance:
    

```bash
bash
```

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

1. Follow the on-screen instructions to set up Jenkins.
    

---

## Task 4: Unraveling IAM Roles

### Step 1: Understand IAM Roles

Before creating IAM roles, let's delve into the concept of IAM Roles. IAM Roles are AWS Identity and Access Management entities that define a set of permissions for making AWS service requests. Unlike IAM users, roles do not have any credentials; instead, they rely on temporary security tokens.

Roles are useful in scenarios such as cross-account access, temporary access for users or applications, and delegating permissions to AWS services.

Read more about IAM Roles [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html).

### Step 2: Create IAM Roles

1. In the IAM dashboard, navigate to "Roles."
    
2. Create three roles: DevOps-User, Test-User, and Admin.
    
3. Define the respective policies for each role.
    

---

## Conclusion

Congratulations! You've successfully navigated through IAM, EC2, Jenkins, and Docker on AWS. These foundational skills will empower you in your cloud journey. As you continue exploring AWS, don't hesitate to experiment and adapt these learnings to real-world scenarios.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Check out my [**GitHub**](https://github.com/ArjunMnn) profile.