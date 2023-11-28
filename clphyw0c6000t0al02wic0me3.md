---
title: "Day 33: Working with Namespaces and Services in Kubernetes"
datePublished: Tue Nov 28 2023 06:38:49 GMT+0000 (Coordinated Universal Time)
cuid: clphyw0c6000t0al02wic0me3
slug: day-33-working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701153499961/bf633009-0802-4295-91cd-bbb3b74cb21f.png
tags: software-development, kubernetes, devops, software-engineering

---

Welcome back, fellow tech enthusiasts! In this exciting sequel to our previous tutorial, we're taking our Kubernetes deployment to new heights by introducing Namespaces. 🚀 Namespaces provides a streamlined way to organize and manage resources within your cluster, offering a cleaner and more organized Kubernetes environment.

# Introduction

In the ever-evolving landscape of container orchestration, Namespaces emerge as the unsung heroes, providing a structured approach to resource isolation. Today, we embark on a journey to integrate Namespaces into our deployment, ensuring a more organized and efficient Kubernetes experience.

### Step 1: Create a Namespace

Let's kick things off by creating a dedicated Namespace for our deployment. Execute the following command and give your Namespace a distinctive identifier:

```bash
kubectl create namespace <namespace-name>
```

Choose a name that resonates with your deployment strategy and sets the tone for a well-organized Kubernetes environment.

### Step 2: Update the Deployment YAML

Next, dive into your `deployment.yml` file and infuse it with the power of Namespaces. Open the file and add the `namespace` field under the `metadata` section:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-deployment
  namespace: <namespace-name>
  labels:
    app: todo-app
# ... (existing configuration)
```

Injecting this configuration ensures that your deployment will reside gracefully within the confines of your newly created Namespace.

### Step 3: Apply the Updated Deployment

It's showtime! Apply the updated deployment configuration using the following command:

```bash
kubectl apply -f deployment.yml -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701153403421/4398595a-2c50-4455-9236-e95d28549437.png align="center")

Watch as your Django Todo app gracefully adapts to its new Namespace home, ready to showcase its enhanced organizational prowess.

### Step 4: Verify Namespace Creation

No journey is complete without verification. Peek into the inner workings of your cluster and verify the presence of your freshly minted Namespace:

```bash
kubectl get namespaces
```

Behold, as your Namespace proudly stands among its peers,a testament to the refined elegance of your Kubernetes environment.

# Services in Kubernetes

#### What are Services?

In Kubernetes, a Service is an abstraction layer that defines a logical set of Pods and enables external traffic exposure, often acting as a stable endpoint for communication.

#### Creating a Service

Let's dive into creating a Service for our Django Todo app. Open a new file, `service.yml`, and add the following configuration:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-service
spec:
  selector:
    app: todo-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8000
  type: LoadBalancer
```

Apply the service configuration:

```bash
kubectl apply -f service.yml -n <namespace-name>
```

This configuration exposes the Pods labeled `app: todo-app` within your Namespace.

# Load Balancing

#### Load Balancing in Kubernetes

Kubernetes Services come with built-in load balancing, distributing traffic across multiple Pods, ensuring optimal resource utilization and high availability.

#### Verifying Load Balancing

Check the status of your Load Balancer:

```bash
kubectl get services -n <namespace-name>
```

You should see your `todo-service` with an external IP, indicating the provisioned load balancer.

# Networking in Kubernetes

#### Networking Fundamentals

Kubernetes networking enables communication between Pods, Services, and external entities. Understanding networking ensures seamless data flow within your cluster.

#### Checking Network Policies

Explore existing network policies:

```bash
kubectl get networkpolicies -n <namespace-name>
```

This command reveals the network policies in place, governing the communication rules within your Namespace.

# Conclusion

By mastering Services, Load Balancing, and Networking in Kubernetes, you've fortified your deployment with essential capabilities. As we continue to explore advanced concepts, your Kubernetes expertise will soar. Stay tuned for more insights into orchestrating containerized applications! 🌐🛠️ #DevOps #Kubernetes #Services #LoadBalancing #Networking

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [GitHub](https://github.com/ArjunMnn) profile.