---
title: "Day 36: Managing Persistent Volumes in Your Deployment"
datePublished: Tue Dec 12 2023 04:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clq1uggyz000208l0d3i18kuc
slug: day-36-managing-persistent-volumes-in-your-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702108720600/c443cb0a-cdd4-4a4c-aec0-87def7d2d562.png
tags: software-development, kubernetes, devops, software-engineering, 90daysofdevops

---

## Introduction

Welcome to Day 36 of the 90 Days of DevOps Challenge! In today's challenge, we'll enhance the resilience and data persistence of your application by adding a Persistent Volume to your Kubernetes Deployment. This will ensure that your application data persists even if pods are rescheduled or moved.

## Task 1: Adding Persistent Volume to Your Deployment

### Step 1: Create a Persistent Volume (pv.yml)

In this step, we create a Persistent Volume that will act as the storage for our Todo application. The `pv.yml` file defines the volume's capacity, access modes, and the path on the host node where the data will be stored. Be sure to update the `path` field with the correct path on your node. Apply the Persistent Volume using:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv-volume
  namespace: mysql
  labels:
    app: mysql
spec:
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteOnce
  storageClassName: manual
  hostPath:
    path: /tmp
```

```plaintext
kubectl apply -f pv.yml
```

### Step 2: Create a Persistent Volume Claim (pvc.yml)

Now, we create a Persistent Volume Claim that requests a specific amount of storage. The `pvc.yml` file specifies the storage capacity required and the access mode. Apply the Persistent Volume Claim using:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-volume
  namespace: mysql
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: manual
  resources:
    requests:
      storage: 1Gi
```

```plaintext
kubectl apply -f pvc.yml
```

### Step 3: Update Deployment File (deployment.yml)

Update your Deployment file (`deployment.yml`) to include the Persistent Volume Claim. This ensures that each pod in your deployment has access to the persistent storage. Apply the updated deployment using:

```yaml
# deployment.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-deployment
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
        - name: todo-container
          image: your-todo-image:latest
          volumeMounts:
            - mountPath: "/app/data"
              name: my-persistent-storage
      volumes:
        - name: my-persistent-storage
          persistentVolumeClaim:
            claimName: my-pvc
```

```plaintext
kubectl apply -f deployment.yml
```

### Step 4: Verify the Deployment

Check the status of your deployment and persistent volumes to ensure the changes have been applied successfully:

```plaintext
kubectl get pods
kubectl get pv
```

## Task 2: Accessing Data in the Persistent Volume

### Step 1: Connect to a Pod

To interact with the data stored in the Persistent Volume, connect to a pod using the following command:

```plaintext
kubectl exec -it <pod-name> -- /bin/bash
```

### Step 2: Verify Access to Persistent Volume Data

Inside the pod, navigate to the mount path and verify that you can access the data:

```plaintext
cd /app/data
ls
```

## Conclusion

Congratulations! You've successfully added a Persistent Volume to your Todo application's deployment, providing data persistence across pod restarts. This ensures that your application remains robust and resilient, even in dynamic Kubernetes environments. Keep up the good work on your DevOps journey! Don't forget to apply changes or create files in your Kubernetes deployments separately.

Stay tuned for more exciting challenges in the 90 Days of DevOps series!

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Check out my [**GitHub**](https://github.com/ArjunMnn) profile.