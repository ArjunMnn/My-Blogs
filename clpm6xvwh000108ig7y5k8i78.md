---
title: "Day 35: Mastering ConfigMaps and Secrets in Kubernetes"
datePublished: Fri Dec 01 2023 05:35:18 GMT+0000 (Coordinated Universal Time)
cuid: clpm6xvwh000108ig7y5k8i78
slug: day-35-mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701408887342/64121ce2-9b25-4f12-8904-6ebd9e1dc0fe.png
tags: software-development, kubernetes, devops, software-engineering

---

Welcome to Day 35 of #90daysofDevOps! Today, we're delving into the realm of ConfigMaps and Secrets in Kubernetes. These powerful tools allow you to manage configuration data and sensitive information, providing a robust solution for deploying applications. Let's dive into the tasks!

## Introduction to ConfigMaps and Secrets

In the intricate dance of orchestrating containerized applications, ConfigMaps and Secrets emerge as unsung heroes. **ConfigMaps** provide a flexible way to manage configuration data, while **Secrets** enhance security by safeguarding sensitive information. Together, they empower Kubernetes deployments with resilience and versatility.

## Task 1: Creating a ConfigMap for Your Deployment

### What are ConfigMaps?

**ConfigMaps** in Kubernetes provide a way to decouple configuration artifacts from image content, keeping containerized applications portable. They store key-value pairs of configuration data that can be used by Pods in the cluster.

### Step 1: ConfigMap Creation

Create a ConfigMap for your Deployment using a file or the command line. Open a new file, `configmap.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: todo-app-config
data:
  DATABASE_URL: "your_database_url"
  API_KEY: "your_api_key"
```

### Step 2: Updating Deployment YAML

Update your `deployment.yml` file to include the ConfigMap. Add the `envFrom` field under `spec.containers`:

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
        image: trainwithshubham/django-todo:latest
        ports:
        - containerPort: 8000
        envFrom:
        - configMapRef:
            name: todo-app-config
```

### Step 3: Applying and Verifying

Apply the updated deployment configuration:

```bash
kubectl apply -f deployment.yml -n <namespace-name>
```

Verify that the ConfigMap has been created:

```bash
kubectl get configmaps -n <namespace-name>
```

## Task 2: Creating a Secret for Your Deployment

### What are Secrets?

**Secrets** in Kubernetes are intended to store and manage sensitive information, such as API keys, passwords, and tokens. They enhance security by allowing the encryption of sensitive data at rest.

### Step 1: Secret Creation

Create a Secret for your Deployment using a file or the command line. Open a new file, `secret.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: todo-app-secret
type: Opaque
data:
  DATABASE_PASSWORD: YWRtaW4xMjM=  # Base64-encoded "admin123"
```

### Step 2: Updating Deployment YAML

Update your `deployment.yml` file to include the Secret. Add the `envFrom` field under `spec.containers`:

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
        image: trainwithshubham/django-todo:latest
        ports:
        - containerPort: 8000
        envFrom:
        - secretRef:
            name: todo-app-secret
```

### Step 3: Applying and Verifying

Apply the updated deployment configuration:

```bash
kubectl apply -f deployment.yml -n <namespace-name>
```

Verify that the Secret has been created:

```bash
kubectl get secrets -n <namespace-name>
```

## Conclusion

ConfigMaps and Secrets stand as indispensable allies in the realm of Kubernetes, offering a dynamic duo of configuration management and security enhancement. By mastering these tools, you've unlocked the potential to elevate your deployments with resilience and safeguard sensitive information. Stay tuned for more insights in the #90daysofDevOps journey! 🚀👨‍💻 #DevOps #Kubernetes #ConfigMaps #Secrets #DeploymentEnhancement