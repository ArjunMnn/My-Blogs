---
title: "Day 27: Jenkins Declarative Pipeline with Docker"
datePublished: Mon Nov 20 2023 14:00:04 GMT+0000 (Coordinated Universal Time)
cuid: clp6z4n5c000d08jt12myc0za
slug: day-27-jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700488649200/373fb0e9-f063-4e6c-b015-c45af51dfe9d.png
tags: software-development, docker, aws, devops, jenkins

---

Welcome to another chapter in our Jenkins exploration! Today, we're diving into the exciting world of Docker integration within Jenkins Declarative Pipelines. Even if you're new to Jenkins or Docker, fear not – we'll guide you through the process step by step.

## Docker Basics: A Quick Recap

Before we start with Jenkins, let's quickly review some Docker basics.

### `docker build` - Building Docker Images

In the context of our pipeline, it's like creating a blueprint for your application and packaging it into a standalone image.

```dockerfile
stages {
    stage('Build') {
        steps {
            sh 'docker build -t arjunmmnn/node-app:latest .'
        }
    }
}
```

### `docker run` - Running Docker Containers

In our pipeline, it's like deploying your application in an isolated environment.

```dockerfile
stages {
    stage('Run') {
        steps {
            sh 'docker run -d arjunmmnn/node-app:latest'
        }
    }
}
```

Now that we've got the basics down, let's tackle our tasks.

## Task-01: Docker Integration with `sh` Command

### Step 1: Create a New Pipeline Job

* Open Jenkins and navigate to the dashboard.
    
* Click on "New Item" to create a new pipeline job.
    

### Step 2: Configure Your Pipeline Script

* In the job configuration, scroll down to the "Pipeline" section.
    
* Choose "Pipeline script" from the Definition dropdown.
    
* In the script box, enter the following:
    

```dockerfile
pipeline{
    agent any
    stages{
        stage('code clone'){
            steps{
                git url: 'https://github.com/ArjunMnn/node-todo-cicd'
                echo 'code cloned'
            }
        }
        stage('build and test'){
            steps{
                sh 'docker build . -t  node-todo-cicd:latest'
                echo 'Build and test successful'
            }
        }
        stage('deploy'){
            steps{
                sh 'docker run -d -p 8000:8000 node-todo-cicd:latest'
            }
        }
    }
}
```

### Step 3: Save and Run Your Job

* Save your configuration.
    
* Run your Jenkins job.
    
* Check whether the application is working on port 8000 or not.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700461269855/bc594d71-afa5-4cb3-89d9-fabff48acf65.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700461335521/b728b628-5a63-4665-b7d6-1cbde0fe3881.png align="center")

* You will face errors in case of running a job twice, as the docker container will be already created.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700461418031/1e44c8c9-7469-4123-8149-71029ab2f932.png align="center")

## Task-02: Docker Integration with Docker Groovy Syntax

### Step 1: Update Your Pipeline Script

* Open the configuration of the same job you created for Task-01.
    
* Update the script box with the following:
    

```dockerfile
pipeline {
    agent any
    stages {
        stage('code clone') {
            steps {
                git url: 'https://github.com/ArjunMnn/node-todo-cicd'
                echo 'code cloned'
            }
        }
        stage('build and test') {
            steps {
                sh 'docker build . -t  django-todo-cicd:latest'
                echo 'Build and test successful'
            }
        }
        stage('deploy') {
            steps {
                script {
                    def Image = 'django-todo-cicd:latest'
                    docker.image(Image).withRun('-p 8000:8000') {
                    sleep time: 30, unit: 'SECONDS'
                    echo 'run'
                    }
                }
                echo 'Deployment successful'
            }
        }
    }
}
```

### Step 2: Save and Run Your Job

* Save your configuration.
    
* Run your Jenkins job again.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700488483536/9543b2c6-6172-435b-b800-29bdb68d3f33.png align="center")

### Step 3: Explore Additional Docker Groovy Options

* Refer to the Docker documentation to explore additional options and configurations available for Docker Groovy syntax in Jenkins pipelines.
    

Congratulations! You've just empowered your Jenkins pipeline with Docker magic. Enjoy the seamless builds and deployments powered by this dynamic duo!

## Conclusion

The dynamic duo of Jenkins and Docker empowers you to build, test, and deploy applications with ease. As you continue your journey in the world of continuous integration and delivery, remember to explore more advanced features, stay updated with the latest releases, and adapt your workflows to the evolving landscape of software development.

Congratulations on mastering Docker integration within Jenkins Declarative Pipelines! May your builds be swift, your deployments seamless, and your coding adventures ever-fulfilling. Happy coding!

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)