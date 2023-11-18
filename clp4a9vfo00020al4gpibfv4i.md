---
title: "Day 24 & 25: Complete Jenkins CI/CD Project"
datePublished: Sat Nov 18 2023 16:48:45 GMT+0000 (Coordinated Universal Time)
cuid: clp4a9vfo00020al4gpibfv4i
slug: day-24-25-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700325882249/0c134984-73cd-4f1a-8732-f3f38a801d1a.png
tags: software-development, docker, devops, jenkins, ci-cd

---

Welcome to this comprehensive guide on setting up a Jenkins CI/CD pipeline for deploying a Node.js To-Do app using Docker Compose, seamlessly integrated with GitHub. This tutorial will walk you through each step, providing detailed explanations and additional information to ensure a smooth setup.

## Introduction

In the ever-evolving landscape of software development, Continuous Integration and Continuous Deployment (CI/CD) have become integral components for delivering reliable and efficient applications. Jenkins, coupled with Docker and GitHub, offers a powerful solution to automate your application deployment process.

This tutorial focuses on the seamless integration of Jenkins with GitHub using webhooks. With GitHub webhooks, any changes made to your repository trigger automatic deployments through Jenkins, ensuring your application is always up-to-date.

### Prerequisites

Before we begin, ensure the following prerequisites are met:

* Your ec2 instance is up and running.
    
* Jenkins is installed and running.
    
* Docker and Docker Compose are installed on your server.
    

## Setting Up Jenkins Job

### Step 1: Create a New Freestyle Project

1. **Open Jenkins and Navigate to Dashboard:** Log in to your Jenkins instance and click on "New Item" to create a new project.
    
2. **Enter Project Details:** Provide a name for your project, such as "todo-node-app," and select the "Freestyle project" option. Click "OK" to create the project.
    

### Step 2: Configure GitHub Project

1. **Enable GitHub Project:** Check the "GitHub project" checkbox.
    
2. **Enter Project URL:** In the "Project URL" field, input the URL of your GitHub repository (e.g., [`https://github.com/ArjunMnn/node-todo-cicd/`](https://github.com/ArjunMnn/node-todo-cicd/)).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321755680/88642c53-edb0-4691-b4dc-b06080fa31cc.png align="center")

### Step 3: Set Up Source Code Management

1. **Choose Git:** In the "Source Code Management" section, select "Git."
    
2. **Enter Repository URL:** Input the URL of your GitHub repository (e.g., [`https://github.com/ArjunMnn/node-todo-cicd.git`](https://github.com/ArjunMnn/node-todo-cicd.git)).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321789046/240666c7-ad12-4923-ac63-c19fec9c5089.png align="center")

### Step 4: Configure Credentials

1. **Generate SSH Keys:** On your EC2 instance, run `ssh-keygen` to generate SSH keys. Use the generated public key for GitHub
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700321967447/db50585c-5d4e-48cf-9fa1-1d801800f1a1.png align="center")
    
2. **Add SSH Key to GitHub:** In GitHub settings, add a new SSH key with the generated public key.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322022793/bc6cdda0-ee0b-43c9-b096-794e51142c37.png align="center")
    
3. **Jenkins Credentials:** In Jenkins credentials section, select "SSH username with private key" in the "Kind" field. Use "github-jenkins" as the ID and "ubuntu" as the username. Enter the private key directly.
    

### Step 5: Set Up Build Triggers

1. **Enable GitHub Hook Trigger:** In the "Build Triggers" section, check "GitHub hook trigger for GITScm polling." This ensures that Jenkins is triggered upon code changes in your GitHub repository.
    

### Step 6: Define Build Steps

1. **Add Execute Shell Build Step:** In the "Build" section, add an "Execute shell" build step. Enter the command `docker-compose down && docker-compose build --no-cache && docker-compose up -d --build` to handle Docker Compose actions.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322099142/58cbf32b-213f-4456-95ed-03f05b3fc595.png align="center")
    

### Step 7: Save the Jenkins Job

Click "Save" to store your Jenkins job configuration.

## GitHub Webhook Configuration

### Step 8: GitHub Webhook Setup

1. **Navigate to GitHub Settings:** In your GitHub repository, click on "Settings" and select "Webhooks."
    
2. **Add Webhook:** Click "Add webhook" to set up a new webhook.
    

### Step 9: Configure Webhook

1. **Enter Payload URL:** In the "Payload URL" field, enter `<ipaddress:8080/github-webhook/>`. Ensure to replace `<ipaddress>` with the actual IP of your Jenkins server.
    
2. **Set Content Type:** Choose "application/json" as the content type.
    
3. **Save Webhook:** Click "Add webhook" to save your webhook configuration.
    

## Install GitHub Integration Plugin

### Step 10: Install GitHub Integration Plugin

1. **Navigate to Jenkins Plugin Manager:** In Jenkins, go to "Manage Jenkins" &gt; "Manage Plugins."
    
2. **Install Plugin:** In the "Available" tab, search for "GitHub Integration" and install the plugin. Restart Jenkins when prompted.
    

### Step 11: Test the Jenkins Job

1. **Build Now:** Go to your Jenkins job and click "Build Now" to test if the setup is correct.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322655193/9e89569b-a67b-46d5-a3bc-3c35fb39fbbc.png align="center")
    
2. **Check Console Output:** Monitor the build console output for any errors or issues.
    

### Step 12: Test the Deployment

1. **Open Browser:** In your web browser, navigate to `<ipaddress:8000>` to verify that your app is successfully deployed.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322311537/4040b30b-2f06-44dc-b893-f0148852d21b.png align="center")

### Step 13: Verify Webhook

1. **Make Changes in GitHub:** Make changes to your GitHub repository to test the webhook.
    
2. **Check Jenkins:** Observe Jenkins for triggered builds and successful deployments.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322609384/1637ee84-e805-4c88-a973-f68afeb2914c.png align="center")
    
3. **Verify Deployment:** Confirm the changes by checking the deployed app in the browser at `<ipaddress:8000>`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700322319183/020e8884-b3b0-4eec-8f53-3bbc0f1e6b16.png align="center")

## Conclusion

Congratulations! You've successfully configured a Jenkins CI/CD pipeline to automate the deployment of your Node.js To-Do app, integrated seamlessly with GitHub. Embrace the power of CI/CD for efficient and reliable software delivery. Happy coding! 🎉

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)