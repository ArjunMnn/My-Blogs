---
title: "Declarative CICD Pipeline with GitHub Integration, Jenkins, Docker, and Agent-Based Automation"
datePublished: Wed Nov 22 2023 08:41:11 GMT+0000 (Coordinated Universal Time)
cuid: clp9im9kx000x08ld6dlv4n0a
slug: declarative-cicd-pipeline-with-github-integration-jenkins-docker-and-agent-based-automation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700642285042/525ef8bd-67b6-43b0-9a30-c4f50cc1f02c.png
tags: software-development, docker, devops, software-engineering, jenkins

---

Efficient deployment is a cornerstone of successful software development. In this tutorial, we'll guide you through the process of setting up a Jenkins pipeline to automate the deployment of your Django web application using Docker. What makes this tutorial special is the utilization of two EC2 instances – a Jenkins master server and an agent server – to facilitate seamless deployment.

### Section 1: Prerequisites and Project Setup

#### 1.1 Prerequisites:

Before initiating the deployment process, confirm that the following prerequisites are met:

* Two ec2 instances for master and agent servers.
    
* Jenkins installed and configured on the master instance.
    
* Jdk, Docker and docker-compose are installed on both instances.
    
* A DockerHub account for storing Docker images.
    

### Section 2: Configuring Jenkins Master and Agent

#### 2.1 Setting Up Jenkins Master:

1. Access your Jenkins master server and navigate to "Manage Jenkins" -&gt; "Manage Nodes and Clouds."
    
2. Click on "New Node" to add the agent EC2 instance.
    
3. Name the node, select "Permanent Agent," and click "OK."
    
4. Specify the necessary configurations, ensuring Docker is installed on the agent. Refer to [this article](https://arjunmenon.hashnode.dev/day-28-jenkins-agents) for more details
    

#### 2.2 Creating a New Pipeline in Jenkins:

1. Access Jenkins and click on "New Item."
    
2. Choose "Pipeline" and provide a name for your project.
    
3. In the pipeline configuration, select "Pipeline script from SCM."
    
4. Choose "Git" as the SCM, and enter your GitHub repository URL.
    
5. Save the configuration.
    

### Section 3: Building the Declarative CICD Pipeline

#### 3.1 Modifying Jenkinsfile:

Update your Jenkinsfile with the following steps to include agent configuration and deployment:

```dockerfile
pipeline {
    agent { label 'dev-server' }
    stages {
        stage('code clone') {
            steps{
                echo 'cloning'
                git url: "https://github.com/ArjunMnn/django-notes-app", branch: "main"
            }
        }
        stage('build') {
            steps{
                 echo 'building'
                 sh 'docker build --no-cache -t my-note-app .'
            }
        }
        stage('push to dockerhub') {
            steps{
                echo 'pushing'
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                    sh "docker tag my-note-app ${env.dockerHubUser}/my-note-app:latest"
                    sh "docker login -u ${env.dockerHubUser} -p ${dockerHubPass}"
                    sh "docker push ${env.dockerHubUser}/my-note-app:latest"
                }
            }
        }
        stage('deploy') {
           steps{
                echo 'deploying'
                sh "docker-compose down && docker-compose build --no-cache && docker-compose up -d --build"
           }
        }
    }
}
```

### Section 4: Configuring DockerHub Credentials

#### 4.1 Jenkins Master:

1. Navigate to "Manage Jenkins" -&gt; "Manage Credentials."
    
2. Add your DockerHub credentials.
    

### Section 5: Creating Docker Compose File

1. Include a comprehensive Docker Compose file in your GitHub repository.
    
2. Configure services, networks, and volumes based on your Django app and any related services.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700638538017/30e28dcc-9f31-4354-a504-d30b38d1a929.png align="center")

### Section 6: Configuring GitHub Webhook

1. In your GitHub repository, navigate to "Settings" -&gt; "Webhooks" -&gt; "Add webhook."
    
2. Set the Payload URL to your Jenkins master server's webhook URL.
    
3. Configure the webhook to trigger on push events.
    

### Section 7: Testing the Pipeline

1. Click on build now. It should deploy the app.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700638671657/c916bae6-5170-4717-851d-35ee1bab8807.png align="center")
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700638609439/e9673364-d867-4d32-84a0-4bffa026d76b.png align="center")
    
    Make a small change in your Django app code.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700641993157/80561264-27c7-4f8f-a3e5-d930fdbc6235.png align="center")
    
    Commit and push the changes to your GitHub repository.
    
5. Observe Jenkins triggering the pipeline on the master server, with deployment occurring on the agent server.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700639034856/58e70c3c-72b3-4cfd-a5fc-0ea068c67c4d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700642104697/d8f265e4-0444-4deb-a7d1-1689a38af9cd.png align="center")

### Conclusion

You've successfully established a robust CICD pipeline for your Django web application, incorporating GitHub integration, Jenkins, Docker, and an agent-based approach. This comprehensive guide allows for easy customization to suit your specific development needs. Explore additional optimizations and enhancements to further enhance your deployment workflow. Happy coding!

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [GitHub](https://github.com/ArjunMnn) profile.