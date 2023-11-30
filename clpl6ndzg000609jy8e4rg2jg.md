---
title: "Day 34: Working with Services in Kubernetes"
datePublished: Thu Nov 30 2023 12:39:23 GMT+0000 (Coordinated Universal Time)
cuid: clpl6ndzg000609jy8e4rg2jg
slug: day-34-working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701347917864/e2e5ed70-ce45-4c3d-96e9-014bfb70aa40.png
tags: software-development, kubernetes, devops, software-engineering

---

Welcome back to the #90daysofDevOps challenge! On Day 34, we're diving into the intricacies of working with Services in Kubernetes. Today's tasks involve creating and configuring various types of Services for our todo-app Deployment from Day 32. Let's embark on this journey together!

## Introduction

In the complex landscape of container orchestration, Kubernetes Services play a pivotal role in facilitating communication between various components within a cluster. They act as an abstraction layer, providing a stable endpoint for applications, ensuring seamless connectivity, and simplifying the management of networking complexities.

## Task-1: Creating a Service for todo-app Deployment

### Step 1: Service Definition

Create a Service definition for your todo-app Deployment. Open a new file, `service.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-app-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8000
  type: NodePort
```

### Step 2: Applying the Service Definition

Apply the Service definition to your Kubernetes cluster using the following command:

```bash
kubectl apply -f service.yml -n <namespace-name>
```

### Step 3: Verifying the Service

Verify that the Service is working by accessing the todo-app using the Service's IP and Port within your Namespace.

```bash
kubectl get svc -n <namespace-name>
```

Access your todo-app using the provided IP and Port.

## Task-2: Creating a ClusterIP Service for Internal Access

### Understanding ClusterIP Service

The ClusterIP service type exposes the Service on a cluster-internal IP. This type of Service is accessible only within the cluster, making it ideal for internal communication between Pods.

### Step 1: ClusterIP Service Definition

Create a ClusterIP Service definition for your todo-app Deployment. Open a new file, `cluster-ip-service.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-app-cluster-ip-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8000
  type: ClusterIP
```

### Step 2: Applying the ClusterIP Service Definition

Apply the ClusterIP Service definition to your Kubernetes cluster using the following command:

```bash
kubectl apply -f cluster-ip-service.yml -n <namespace-name>
```

### Step 3: Verifying the ClusterIP Service

Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster within your Namespace.

```bash
kubectl get svc -n <namespace-name>
```

Access your todo-app from another Pod using the ClusterIP.

## Task-3: Creating a LoadBalancer Service for External Access

### Understanding LoadBalancer Service

The LoadBalancer service type exposes the Service externally using a cloud provider's load balancer. It is ideal for scenarios where external access to the Service is required.

### Step 1: LoadBalancer Service Definition

Create a LoadBalancer Service definition for your todo-app Deployment. Open a new file, `load-balancer-service.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-app-load-balancer-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8000
  type: LoadBalancer
```

### Step 2: Applying the LoadBalancer Service Definition

Apply the LoadBalancer Service definition to your Kubernetes cluster using the following command:

```bash
kubectl apply -f load-balancer-service.yml -n <namespace-name>
```

### Step 3: Verifying the LoadBalancer Service

Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster within your Namespace.

```bash
kubectl get svc -n <namespace-name>
```

Access your todo-app from outside the cluster using the provided external IP.

## Conclusion

In the dynamic landscape of Kubernetes, Services act as the linchpin, orchestrating connectivity and accessibility within your cluster. Mastering the art of creating and configuring Services enhances your ability to design resilient and scalable applications. As we continue our #90daysofDevOps journey, stay tuned for more Kubernetes adventures and advanced concepts! 🚀👩‍💻 #DevOps #Kubernetes #Services #Deployment #AccessManagement

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [GitHub](https://github.com/ArjunMnn) profile.