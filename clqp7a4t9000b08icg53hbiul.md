---
title: "CI/CD Pipeline using AWS CodeCommit, Codebuild, CodeDeploy and CodePipeline"
seoDescription: "Learn AWS DevOps step by step: CodeCommit, CodeBuild, CodeDeploy, and CodePipeline for deploying a Todo List web app with Nginx. Beginners welcome!"
datePublished: Thu Dec 28 2023 12:47:51 GMT+0000 (Coordinated Universal Time)
cuid: clqp7a4t9000b08icg53hbiul
slug: cicd-pipeline-using-aws-codecommit-codebuild-codedeploy-and-codepipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703767524408/a4dc3c51-d0a7-43b3-86f9-0bc60202963b.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Welcome to this comprehensive guide where we'll walk through the process of creating a CI/CD pipeline for deploying a Todo List web app using AWS DevOps services. This tutorial is designed to be beginner-friendly, providing detailed steps for setting up CodeCommit, CodeBuild, CodeDeploy, and CodePipeline. We'll be installing Nginx and deploying a Todo List web app on an EC2 instance.

## Code

All the required code is available at [this repository](https://github.com/ArjunMnn/AWS-devops-cicd.git).

## Step 1: Setting Up CodeCommit

1. **Create a CodeCommit Repository:**
    
    * Begin by navigating to the AWS Management Console and selecting CodeCommit.
        
    * Click on "Create Repository" and provide a unique name for your repository.
        
2. **Create IAM User and Generate Credentials:**
    
    * Proceed to create an IAM user with administrative permissions.
        
    * Generate HTTPS Git credentials for the IAM user.
        
3. **Clone Repository Locally:**
    
    * Clone the repository to your local machine using the HTTPS URL and the credentials generated.
        
4. **Create Project Files:**
    
    * Inside the local repository, create the following files: `index.html`, `app.js`, `styles.css`.
        
    * Push the changes to the CodeCommit repository.
        

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

## Step 2: Configuring CodeBuild

1. **Create a Build Project:**
    
    * Open the AWS CodeBuild console and create a new build project.
        
    * Use the provided `buildspec.yaml` file as the build specification.
        

```yaml
# buildspec.yaml
version: 0.2
phases:
  install:
    commands:
      - echo Installing Nginx...
      - sudo apt-get update
      - sudo apt-get install nginx -y
  build:
    commands:
      - echo Build started on `date`
      - cp index.html /var/www/html/
      - cp styles.css /var/www/html/
      - cp app.js /var/www/html/
      - cp appspec.yml /var/www/html/
  post_build:
    commands:
      - echo Restarting Nginx...
artifacts:
  files:
    - index.html
    - appspec.yml
    - scripts/**
    - app.js
    - styles.css
```

1. **Configure Artifacts:**
    
    * Edit the build project to specify an S3 bucket and a folder for storing artifacts.
        
    * Create a folder in the S3 bucket named `artifact`.
        
2. **Run the Build:**
    
    * Trigger a build in the CodeBuild console.
        
    * Verify that the build is successful, and artifacts are stored in the S3 bucket.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765629394/c269ddde-563a-48b6-897b-1bd52c5fc8a7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765654228/b8822dc5-3267-41dd-ad08-36a364c4ab57.png align="center")

## Step 3: Implementing CodeDeploy

1. **Create CodeDeploy Application:**
    
    * Navigate to the AWS CodeDeploy console and create a new application named `demo-app-application`.
        
    * Specify the compute platform as `ec2/on-premises`.
        
2. **Create Deployment Group:**
    
    * Create a deployment group and associate it with an EC2 instance.
        
3. **Install CodeDeploy Agent on EC2 Instance:**
    
    * SSH into the EC2 instance.
        
    * Execute the provided shell script to install the CodeDeploy agent.
        

```bash
#!/bin/bash 
# This installs the CodeDeploy agent and its prerequisites on Ubuntu 22.04.  
sudo apt-get update 
sudo apt-get install ruby-full ruby-webrick wget -y 
cd /tmp 
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/releases/codedeploy-agent_1.3.2-1902_all.deb 
mkdir codedeploy-agent_1.3.2-1902_ubuntu22 
dpkg-deb -R codedeploy-agent_1.3.2-1902_all.deb codedeploy-agent_1.3.2-1902_ubuntu22 
sed 's/Depends:.*/Depends:ruby3.0/' -i ./codedeploy-agent_1.3.2-1902_ubuntu22/DEBIAN/control 
dpkg-deb -b codedeploy-agent_1.3.2-1902_ubuntu22/ 
sudo dpkg -i codedeploy-agent_1.3.2-1902_ubuntu22.deb 
systemctl list-units --type=service | grep codedeploy 
sudo service codedeploy-agent status
```

1. **Create appspec.yaml and Scripts:**
    
    * Create an `appspec.yaml` file with the provided content.
        
    * Create a `scripts` folder with `install_`[`nginx.sh`](http://nginx.sh) and `start_`[`nginx.sh`](http://nginx.sh) scripts.
        

appspec.yaml:

```yaml
# appspec.yaml
version: 0.0
os: linux
files:
  - source: /
    destination: /var/www/html/
hooks:
  AfterInstall:
    - location: scripts/install_nginx.sh
      timeout: 300
      runas: root
  ApplicationStart:
    - location: scripts/start_nginx.sh
      timeout: 300
      runas: root
```

install\_nginx.sh

```bash
# scripts/install_nginx.sh
#!/bin/bash
apt-get update
apt-get install nginx -y
```

start\_nginx.sh

```bash
# scripts/start_nginx.sh
#!/bin/bash
service nginx start
```

1. **Build and Deploy:**
    
    * Trigger another CodeBuild to ensure the latest code artifact is in the S3 bucket.
        
    * Create a deployment in CodeDeploy, specifying the S3 location of the artifact.
        
2. **Configure EC2 Role:**
    
    * Create a role for the EC2 instance with permissions to access S3 and CodeDeploy.
        
    * Attach the role to the EC2 instance.
        
3. **Restart CodeDeploy Agent:**
    
    * On the EC2 instance, restart the CodeDeploy agent.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765608441/a886524c-7b22-44f4-8a39-f83a0d47ff27.png align="center")

## Step 4: Setting Up CodePipeline

1. **Configure CodePipeline:**
    
    * Open the AWS CodePipeline console and create a new pipeline.
        
    * Add CodeCommit as the source, CodeBuild as the build stage, and CodeDeploy as the deploy stage.
        
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765497088/80f2748d-f92c-48da-bff9-ef683808fd25.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765508529/239deb0a-466f-4d45-b0f1-06b4d87f92af.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765517839/c00cc4cf-9355-498c-8386-675a25851f0b.png align="center")
    
3. **Create Pipeline:**
    
    * Click "Create Pipeline" to initiate the pipeline.
        
    * The pipeline will automatically fetch code from CodeCommit, build using CodeBuild, and deploy using CodeDeploy.
        
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765984454/1767a1b5-faa9-4012-ab97-7c89ca7555ad.png align="center")
    
5. **Test the Web App:**
    
    * Access the public IP of the EC2 instance.
        
    * Verify that the Todo List web app is successfully deployed.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703765580343/0fe7a58a-db3d-4323-b6a4-341c2a2e108d.png align="center")

## Conclusion

Congratulations! You've successfully set up a CI/CD pipeline for deploying a Todo List web app using AWS DevOps tools. This tutorial has covered each step in detail, providing you with a solid foundation for implementing similar projects in the future.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.