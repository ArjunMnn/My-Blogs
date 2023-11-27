---
title: "Day 32: Launching your Kubernetes Cluster with Deployment"
datePublished: Mon Nov 27 2023 09:22:25 GMT+0000 (Coordinated Universal Time)
cuid: clpgpaja6000v09lecm43daha
slug: day-32-launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701076662831/88786318-919c-4b6d-a3d0-247c5b77d52e.png
tags: software-development, kubernetes, devops, software-engineering

---

Welcome to this exciting tutorial where we embark on a journey to deploy a Django Todo application on Kubernetes. 🚀 Whether you're just starting with Kubernetes or looking to enhance your skills, this guide will provide you with a step-by-step process to set up a robust environment for your Django Todo app, complete with auto-scaling and auto-healing capabilities. 🛠️

## Introduction

Kubernetes, the container orchestration powerhouse, offers more than just deployment. In this tutorial, we'll not only deploy our Django Todo app but also explore Kubernetes' auto-scaling and auto-healing features. These functionalities ensure your application is not only scalable to handle increased loads but also resilient to recover from unexpected failures.

### Step 1: Clone the Git Repository

To kick off our journey, let's clone the Django Todo app Git repository to your local machine. 🧑‍💻

```bash
git clone https://github.com/LondheShubham153/django-todo-cicd.git
```

### Step 2: Build Docker Image

Navigate to the project directory and build the Docker image, turning your Django Todo app into a containerized masterpiece. 🐳

```bash
cd django-todo-cicd
docker build -t your-dockerhub-username/django-todo:latest .
```

### Step 3: Push Docker Image to DockerHub

Push the image to DockerHub, making it accessible to Kubernetes for deployment. 🚢

```bash
docker push your-dockerhub-username/django-todo:latest
```

### Step 4: Create Deployment YAML

Define the deployment configuration, showcasing the auto-scaling prowess of Kubernetes. 🚀

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-deployment
  labels:
    app: todo-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: todo-app
  template:
    metadata:
      labels:
        app: todo-app
    spec:
      containers:
      - name: todo-app
        image: your-dockerhub-username/django-todo:latest
        ports:
        - containerPort: 8000
```

### Step 5: Deploy the Application

Watch as Kubernetes scales your app with ease. 🔄

```bash
kubectl apply -f deployment.yml
```

### Step 6: Check Pods

Ensure your pods are thriving in the Kubernetes ecosystem. 🌐

```bash
kubectl get pods
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701076501929/0b5a96d2-748d-497a-8d62-6c979f2f5f89.png align="center")

### Step 7: Create Service YAML

Define the service configuration to expose your app to the world. 🌍

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-service
spec:
  type: NodePort
  selector:
    app: todo-app
  ports:
    - port: 80
      targetPort: 8000
      nodePort: 30007
```

### Step 8: Apply the Service Configuration

Expose your Django Todo app for the world to see. 🌐

```bash
kubectl apply -f service.yml
```

### Step 9: Check Service

Ensure your service is up and running. 🚀

```bash
kubectl get svc
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701076530264/e95834e9-5bf1-4f8d-8c45-f16a1a7d6a07.png align="center")

### Step 10: Test the Application

Open your browser and experience the magic at [http://your-kubernetes-node-ip:30007](http://your-kubernetes-node-ip:30007). 🌟

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701076556054/e25453dc-9327-4264-a18e-870e2aeb5dac.png align="center")

## Conclusion

Congratulations, you've successfully deployed a Django Todo app on Kubernetes, unlocking the full potential of auto-scaling and auto-healing features. 🎉 As you continue your Kubernetes journey, feel free to explore further and customize your application based on your evolving needs. Happy coding! 🚀👨‍💻

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [GitHub](https://github.com/ArjunMnn) profile.