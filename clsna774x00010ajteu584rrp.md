---
title: "Day 88: Deploying a Django App on a Kubernetes Cluster with kubeadm"
datePublished: Thu Feb 15 2024 13:53:25 GMT+0000 (Coordinated Universal Time)
cuid: clsna774x00010ajteu584rrp
slug: day-88-deploying-a-django-app-on-a-kubernetes-cluster-with-kubeadm
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708005107122/e61373a3-75cc-4867-af2d-f210173daaf6.png
tags: cloud, software-development, aws, kubernetes, devops

---

In this tutorial, we will guide you through deploying a Django Todo app on a Kubernetes cluster using `kubeadm`. We'll cover setting up the Kubernetes cluster, creating the necessary YAML files for Deployment and Service, and running the project.

## Step 1: Clone the GitHub Repository

Begin by cloning the Django Todo app from the provided GitHub repository:

```bash
git clone https://github.com/LondheShubham153/django-todo-cicd.git
```

## Step 2: Setup the Kubernetes Cluster

### Master Node Setup:

Execute the following commands on the master node:

```bash
# Update package lists
apt update -y

# Install Docker
apt install docker.io -y

# Start and enable Docker service
systemctl start docker
systemctl enable docker

# Add the Kubernetes repository and update package lists
curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg
echo 'deb https://packages.cloud.google.com/apt kubernetes-xenial main' > /etc/apt/sources.list.d/kubernetes.list
apt update -y

# Install specific versions of kubeadm, kubectl, and kubelet
apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y

# Initialize the Kubernetes cluster on the Master Node
kubeadm init

# Set up Kubernetes configuration
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

# Apply a Weave networking addon to enable communication between pods
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml

# Generate the join command for the Worker Node
kubeadm token create --print-join-command
```

### Worker Node Setup:

Run the following commands on the worker node:

```bash
# Update package lists
apt update -y

# Install Docker
apt install docker.io -y

# Start and enable Docker service
systemctl start docker
systemctl enable docker

# Add the Kubernetes repository and update package lists
curl -fsSL "https://packages.cloud.google.com/apt/doc/apt-key.gpg" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg
echo 'deb https://packages.cloud.google.com/apt kubernetes-xenial main' > /etc/apt/sources.list.d/kubernetes.list
apt update -y

# Install specific versions of kubeadm, kubectl, and kubelet
apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y

# Reset the Worker Node (if already initialized)
kubeadm reset

# Paste the join command generated from the Master Node and append "--v=5" at the end to enable verbose output during join
kubeadm join <master_node_ip>:6443 --token <token> \
    --discovery-token-ca-cert-hash <hash> --v=5
```

Remember to replace `<master_node_ip>`, `<token>`, and `<hash>` in the Worker Node commands with the appropriate values obtained from the Master Node.

## Step 3: Setup Deployment and Service for Kubernetes

Create the Deployment and Service YAML files for the Django app.

### Deployment.yaml:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: django-todo-app-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: django-todo-app
  template:
    metadata:
      labels:
        app: django-todo-app
    spec:
      containers:
        - name: django-todo-app
          image: estebanmorenoit/django-notes-app:latest
          ports:
            - containerPort: 80
```

Apply the Deployment YAML:

```bash
kubectl apply -f deployment.yaml
```

### Service.yaml:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: django-todo-app-service
spec:
  type: NodePort
  selector:
    app: django-todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30080
```

Apply the Service YAML:

```bash
kubectl apply -f service.yaml
```

## Step 4: Run the Project

With the Kubernetes Deployment and Service set up, your Django Todo app should now be accessible through the specified port on the master server. You can access it using the public IP or DNS name of the master server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708005249722/949c1033-22ec-475e-a599-5e9332417975.png align="center")

Congratulations! You have successfully deployed a Django app on a Kubernetes cluster using kubeadm.