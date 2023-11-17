---
title: "Day 23: Jenkins Freestyle Project for DevOps Engineers"
datePublished: Fri Nov 17 2023 14:12:49 GMT+0000 (Coordinated Universal Time)
cuid: clp2p9hd6000o09jshr3deuwt
slug: day-23-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700230334413/68b68ee6-47bd-48ca-9f7a-7b82e7e1c2a3.png
tags: docker, automation, devops, jenkins, ci-cd

---

Continuous Integration and Continuous Deployment (CI/CD) are fundamental practices in modern software development. In this detailed tutorial, we'll break down the basics of CI/CD, understand the concept of a build job, and dive into creating Jenkins Freestyle Projects to automate Docker tasks. Whether you're a beginner or an experienced developer, this guide aims to make the process accessible to all.

## Understanding CI/CD 🔄

**CI/CD** involves automating the process of integrating code changes and deploying applications. This ensures that your code is consistently tested and delivered, promoting a more efficient and reliable development workflow.

## What is a Build Job? 🏗️

In Jenkins, a **build job** is a task that takes your source code, compiles it, runs tests, and produces artifacts. These jobs are a crucial part of CI/CD pipelines, guaranteeing that your application is in a deployable state.

## Exploring Freestyle Projects 🎨

**Jenkins Freestyle Projects** are user-friendly and flexible, making them an excellent starting point for CI/CD beginners. These projects allow you to configure build jobs without needing extensive scripting.

For the tasks that follow, I have used the below projects:

1. [Dockerizing a Django To-Do App on AWS](https://arjunmenon.hashnode.dev/dockerizing-and-deploying-a-django-to-do-app-on-aws)
    
2. [Deploying a Two-Tier Flask App with Docker-Compose](https://arjunmenon.hashnode.dev/deploying-a-two-tier-flask-app-with-docker-compose)
    

### Task-01: Building and Running Docker Containers 🐳

#### Step 1: Create an Agent for Your App 🕵️‍♂️

1. In Jenkins, go to "Manage Jenkins" &gt; "Manage Nodes and Clouds."
    
2. Click "New Node" to create a new agent. Give it a name, choose "Permanent Agent," and configure the necessary settings.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700228510917/49cdd6ae-53a0-4971-be3c-b05a64abb314.png align="center")
    

#### Step 2: Configure a Freestyle Project ⚙️

1. Click on "New Item" on the Jenkins dashboard.
    
2. Enter a project name and choose "Freestyle project."
    
3. Under the "General" section, check "Restrict where this project can be run" and select your created agent.
    

#### Step 3: Add Build Steps 🛠️

1. In the project configuration, navigate to the "Build" section.
    
2. Click on "Add build step" and choose "Execute shell" (for Unix-based systems) or "Execute Windows batch command" (for Windows).
    
3. For the "Command," enter `docker build -t your-app-image .` to build your Docker image.
    
4. Add a second build step by clicking "Add build step" again. Choose "Execute shell" or "Execute Windows batch command," and enter `docker run -d -p 8001:8001 your-app-image` to run your Docker container.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700228615709/cc3c9470-b9f8-47f3-8a08-26301726856d.png align="center")
    

#### Step 4: Save and Build 💾

1. Save your project configuration.
    
2. Trigger a build by clicking "Build Now" on the project dashboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700228700490/a5b70bfc-cf5d-4434-93d2-3d7b6666b1f1.png align="center")
    

Jenkins will now execute the specified build steps, creating a Docker image and running a container for your app.

#### Step 5: Manual Browser Testing 🌐

1. Open your preferred web browser.
    
2. Navigate to [`http://localhost:8080`](http://localhost:8080) to access your Todo App manually.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700228931589/7082ed0a-4c64-4ad9-a022-c0dc8c4fb736.png align="center")
    

### Task-02: Docker Compose Automation 🤖

#### Step 1: Create a Jenkins Project 🏗️

1. Create a new Freestyle Project following the steps above.
    

#### Step 2: Configure Build Steps ⚙️

1. Under the "Build" section, click "Add build step" and choose "Execute shell" or "Execute Windows batch command."
    
2. Enter the command `docker-compose -f path/to/your/docker-compose-file.yml up -d` to start multiple containers defined in your Docker Compose file.
    
3. Add a cleanup step by clicking "Add build step" again. Choose "Execute shell" or "Execute Windows batch command," and enter `docker-compose -f path/to/your/docker-compose-file.yml down` to stop and remove containers.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700230033178/30ef5dea-c27c-4a5c-8c03-98bbc63f8199.png align="center")
    

#### Step 3: Save and Run 💾

1. Save your project configuration.
    
2. Trigger a build to see Jenkins automating the deployment of your Docker Compose application.
    

#### Step 4: Manual Browser Testing for Two-Tier Flask App 🌐

1. Open your preferred web browser.
    
2. Navigate to [`http://localhost:5000`](http://localhost:5000) to access your Two-Tier Flask App manually.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700230194388/8f2c01e8-b78d-4077-b17a-b57bac13fb69.jpeg align="center")
    

With these detailed steps, even beginners can successfully set up Jenkins Freestyle Projects for Docker automation. Remember, practice is key, so feel free to experiment with different configurations to enhance your CI/CD skills. Happy coding! 🚀

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)