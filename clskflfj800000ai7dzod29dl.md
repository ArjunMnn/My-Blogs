---
title: "Day 87: Deploying a React App on AWS Elastic Beanstalk using GitHub Actions"
datePublished: Tue Feb 13 2024 14:01:09 GMT+0000 (Coordinated Universal Time)
cuid: clskflfj800000ai7dzod29dl
slug: day-87-deploying-a-react-app-on-aws-elastic-beanstalk-using-github-actions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707832835813/59fea2d4-1432-4fcf-baf6-62b67364bda3.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

### Introduction

Deploying web applications involves multiple steps, from setting up infrastructure to ensuring smooth deployments. AWS Elastic Beanstalk provides an easy-to-use platform for deploying and managing applications on AWS. By integrating GitHub Actions into the deployment pipeline, you can automate the deployment process, reducing manual errors and saving time.

### Prerequisites:

1. An Ubuntu machine with Git installed.
    
2. Access to an AWS account.
    
3. Basic familiarity with Docker, React, AWS Elastic Beanstalk, and GitHub.
    

### Step 1: Clone the Source Code

If you haven't already, clone the repository containing your React app.

```json
git clone https://github.com/ArjunMnn/AWS_Elastic_BeanStalk_On_EC2.git
cd AWS_Elastic_BeanStalk_On_EC2
```

### Step 2: Set Up Docker

Make sure Docker is installed and enabled. Use the provided shell script to install Docker.

```json
chmod +x docker_install.sh
sh docker_install.sh
```

### Step 3: Create a Multi-Stage Dockerfile

Create a Dockerfile to build your React app image.

```bash
FROM node:14-alpine as builder
WORKDIR /app 
COPY package.json . 
RUN npm install 
COPY . . 
RUN npm run build

FROM nginx 
EXPOSE 80 
COPY --from=builder /app/build /usr/share/nginx/html
```

### Step 4: Build the Docker Image

Build the Docker image for your React app.

```bash
sudo docker build -t react-app-image .
```

### Step 5: Run the Docker Container

Run a Docker container with the built image.

```bash
sudo docker run -d -p 80:80 react-app-image
```

### Step 6: Configure AWS Elastic Beanstalk

* Go to AWS Elastic Beanstalk and click "Create Application".
    
* Provide application details, select Docker as the platform, and choose "Sample Code" as a starting point.
    
* Wait for the environment setup.
    
* Access your deployed app using the provided URL.
    

### Step 7: Enable CI/CD with GitHub Actions

* Locate the "deploy-react.yaml" file provided in your repository.
    
* Move it under the ".github/workflows" directory.
    
* Update the file with relevant parameters such as branch name, application name, environment name, AWS access key, AWS secret access key, and region.
    

### Step 8: Trigger GitHub Action CI/CD

Push all changes to the "main" branch of your GitHub repository. GitHub Actions will automatically trigger the CI/CD process.

```bash
git add .
git commit -m "Add CI/CD workflow"
git push origin main
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707832628229/16d691b5-dec6-452f-a866-eb03bb7652a1.png align="center")

### Step 9: Check the Result

* Verify the Elastic Beanstalk link received earlier.
    
* The sample application should now be replaced with your React app, confirming successful deployment.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707832645172/95828d93-7aa9-406c-bf40-1eed0fac514b.png align="center")

### Conclusion

Automating the deployment process using GitHub Actions and AWS Elastic Beanstalk simplifies the workflow and ensures consistent deployments. By following this tutorial, you've learned how to integrate CI/CD into your React app deployment pipeline, making it efficient and scalable for future projects.