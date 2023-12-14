---
title: "Day 38: Getting Started with AWS Basics"
seoDescription: "Set up IAM users, launch Linux instances, and build a DevOps Avengers team. Strengthen your foundation for DevOps success."
datePublished: Thu Dec 14 2023 12:37:51 GMT+0000 (Coordinated Universal Time)
cuid: clq56rd1f000d08jqfubi8qvg
slug: day-38-getting-started-with-aws-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702557309507/5cfdb5d1-afc9-4060-8b5f-8d73eeb4ff3b.png
tags: cloud, software-development, aws, software-engineering, 90daysofdevops

---

## Introduction

Welcome to Day 38 of our Journey to DevOps Mastery! Today, we embark on tasks that will deepen your understanding of Identity and Access Management (IAM) in AWS and strengthen your ability to assemble and manage a DevOps team.

## Task 1: Setting Up IAM User and Launching Linux Instance

### Create IAM User with EC2 Access

Transitioning into Day 38 of our DevOps journey, let's start by setting up an IAM user to manage access to our AWS resources. Choose a username that aligns with your preferences and grant EC2 access to this user.

1. Log in to your AWS Management Console.
    
2. Navigate to IAM (Identity and Access Management).
    
3. Create a new user with the desired username.
    
4. Attach the "AmazonEC2FullAccess" policy to grant EC2 access.
    

### Launch Linux Instance and Install Jenkins and Docker

Now, let's leverage the IAM user we just created to launch a Linux instance and install Jenkins and Docker using a single Shell Script.

1. Use the IAM user credentials to log in to the AWS EC2 Dashboard.
    
2. Launch a new instance, selecting a suitable Linux AMI.
    
3. Configure security groups and key pairs for secure access.
    
4. Once the instance is running, connect to it via SSH.
    
5. Create a Shell Script to install Jenkins and Docker.
    
6. ```bash
    #!/bin/bash
    
    # Update and install Docker
    sudo apt update -y
    sudo apt install docker.io -y
    
    # Install Jenkins
    sudo apt install openjdk-11-jdk -y
    sudo wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    sudo apt update -y
    sudo apt install jenkins -y
    
    # Start Docker and Jenkins services
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo systemctl start jenkins
    sudo systemctl enable jenkins
    ```
    
7. Execute the script to set up your environment seamlessly.
    

## Task 2: Building Your DevOps Avengers Team

### Creating DevOps IAM Users

Transitioning to the next task, let's assemble our DevOps Avengers team by creating three IAM users.

1. Return to the IAM Dashboard in AWS.
    
2. Create three IAM users, naming them after your favorite Avengers.
    
3. Assign unique access credentials to each user.
    

### Assigning Users to DevOps Groups

To streamline our DevOps operations, let's group these IAM users into a DevOps group and assign a custom IAM policy.

1. Create a new IAM group named "DevOpsGroup."
    
2. Add the three DevOps Avengers users to this group.
    
3. Create a custom IAM policy granting access to necessary resources.
    
4. Attach the policy to the "DevOpsGroup."
    

Now, your DevOps Avengers team is ready to collaborate and conquer the DevOps landscape.

## Conclusion

Day 38 of our DevOps journey has empowered you to set up IAM users, launch Linux instances, and create a DevOps team worthy of the Avengers. By mastering these fundamental tasks, you've laid a robust foundation for your DevOps skills.

As you reflect on today's achievements, remember that every step forward brings you closer to DevOps excellence. Tomorrow holds new challenges and opportunities, so stay committed to your learning journey.