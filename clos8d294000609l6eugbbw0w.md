---
title: "Day 17: Docker Project for DevOps Engineers"
datePublished: Fri Nov 10 2023 06:22:01 GMT+0000 (Coordinated Universal Time)
cuid: clos8d294000609l6eugbbw0w
slug: day-17-docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699596899476/03e8defb-f3f3-4560-ab5d-5ac1dcf9b6a2.png
tags: software-development, linux, docker, devops, software-engineering

---

## Introduction

DevOps engineers play a pivotal role in enhancing the efficiency and reliability of software development and deployment processes. Docker, a containerization platform, has emerged as an indispensable tool in the DevOps toolkit. In this blog post, we will guide you through a Docker project tailored for DevOps engineers. This project involves creating a Dockerfile for a Django-based Todo application, building the Docker image, running the container, verifying the application's functionality, and pushing the image to a repository.

## Step 1: Create an AWS EC2 Instance 🌐

1. Navigate to the AWS Management Console.
    
2. Launch an EC2 instance, choosing an Amazon Machine Image (AMI) based on your preference (e.g., Amazon Linux).
    
3. Configure the instance, set up security groups to allow inbound traffic on ports 22 (SSH) and 8001 (Django application).
    
4. Launch the instance and download the private key.
    
5. Connect to the instance using SSH:
    
    ```bash
    ssh -i /path/to/private-key.pem ec2-user@your-instance-ip
    ```
    

## Step 2: Clone the Django Todo App from GitHub 🔄

Once connected to your EC2 instance, clone your Django Todo application from GitHub:

```bash
# Clone the GitHub repository
git clone https://github.com/ArjunMnn/django-todo.git

# Navigate to the project directory
cd django-todo
```

## Step 3: Create a Dockerfile for the Django Todo App 🐍

The first step is to create a Dockerfile that defines the environment for our web application. For this example, let's consider a Node.js application. Create a file named `Dockerfile` with the following content:

```bash
FROM python:3

RUN pip install django==3.2

COPY . .

RUN python manage.py migrate

CMD ["python","manage.py","runserver","0.0.0.0:8001"]
```

This Dockerfile sets up a Python environment, installs the application dependencies, and specifies the command to run the Django Todo application.

## Step 4: Build the Docker Image and Run the Container 🏗️

Navigate to the directory containing your Dockerfile and application code in the terminal. Run the following commands:

```bash
# Build the Docker image
docker build . -t todo-app

# Run the Docker container
docker run -p 8001:8001 <image-id>
```

These commands build the Docker image with the `<image-id>` and run a container based on that image, mapping port 8001 from the container to the host.

## Step 5: Verify Application Functionality 👩‍💻

Open your web browser and navigate to [`http://<ipaddress>:8001`](http://localhost:8080), where &lt;ipaddress&gt; is the appropriate IP of your remote server. You should see your application running.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699596044512/5fcb5aa6-0d33-4ed7-871a-631f1a4c01f3.png align="center")

This step verifies that the application is working correctly within the Docker container.

## Step 6: Push the Image to a Repository ☁️

To share your Docker image or deploy it to other environments, push it to a container registry. For example, let's use Docker Hub as the repository:

```bash
# Log in to Docker Hub (replace USERNAME with your Docker Hub username)
docker login -u USERNAME

# Tag the image with your Docker Hub username and repository name
docker tag todo-app USERNAME/todo-app

# Push the image to Docker Hub
docker push USERNAME/todo-app
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699596299744/100a30b2-49a7-4aeb-b6ff-4f4db6abceb7.png align="center")

Now, your Docker image is available on Docker Hub and can be pulled by others for deployment.

## Conclusion

In conclusion, this Docker project for DevOps engineers guides you through the process of containerizing a Django Todo application. By creating a Dockerfile, building an image, running a container, and pushing the image to a repository, you ensure consistency and reproducibility in deploying your Django applications across different environments. 🌐

Let's connect on LinkedIn - [https://www.linkedin.com/in/arjunmenon-devops/](https://www.linkedin.com/in/arjunmenon-devops/)