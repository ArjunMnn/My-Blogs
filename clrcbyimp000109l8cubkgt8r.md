---
title: "Deploying a Three-Tier Application with CI/CD using Jenkins, ReactJS, NodeJS, and MongoDB on Kubernetes"
datePublished: Sat Jan 13 2024 17:17:29 GMT+0000 (Coordinated Universal Time)
cuid: clrcbyimp000109l8cubkgt8r
slug: deploying-a-three-tier-application-with-cicd-using-jenkins-reactjs-nodejs-and-mongodb-on-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705166516019/26105c71-7045-4ce0-91a9-2a5aa7943280.png
tags: cloud, software-development, aws, kubernetes, devops

---

## Introduction

In this tutorial, we will guide you through the process of deploying a three-tier application on Kubernetes using ReactJS for the frontend, NodeJS for the backend, and MongoDB as the database. We'll use the provided GitHub repository and Docker containers for each tier. Additionally, we'll create Kubernetes manifest files to orchestrate the deployment.

## Prerequisites

Before starting, ensure you have the following prerequisites:

1. AWS account with IAM administrator access.
    
2. An EC2 instance with Ubuntu in your preferred region.
    
3. All the required code is available in [this](https://github.com/ArjunMnn/TWSThreeTierAppChallenge) GitHub repository.
    

## Step 1: IAM Configuration

Create a user `eks-admin` with AdministratorAccess and generate security credentials (Access Key and Secret Access Key).

```bash
# AWS CLI command
aws configure
```

## Step 2: EC2 Setup

Launch an Ubuntu instance and SSH into it.

## Step 3: Install AWS CLI v2

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install -i /usr/local/aws-cli -b /usr/local/bin --update
```

## Step 4: Install Docker

```bash
sudo apt-get update
sudo apt install docker.io
docker ps
sudo chown $USER /var/run/docker.sock
```

## Step 5: Install kubectl

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```

## Step 6: Install eksctl

```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

## Step 7: Setup EKS Cluster

```bash
eksctl create cluster --name three-tier-cluster --region us-west-2 --node-type t2.medium --nodes-min 2 --nodes-max 2
aws eks update-kubeconfig --region us-west-2 --name three-tier-cluster
kubectl get nodes
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705154550127/a0607b79-351b-4158-95c4-8ab3beb55400.png align="center")

## Step 8: Clone GitHub Repository

```bash
git clone https://github.com/ArjunMnn/TWSThreeTierAppChallenge
cd TWSThreeTierAppChallenge
```

## Step 9: Build Docker Images

Build Docker images for all three tiers (frontend, backend, and MongoDB). Refer to the provided Dockerfiles in the repository.

## Step 10: Create Kubernetes Manifests

Use the provided manifest files to deploy the application on Kubernetes.

```bash
kubectl create namespace workshop
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f deploy.yaml
kubectl apply -f secrets.yaml
kubectl apply -f service.yaml
kubectl apply -f full_stack_lb.yaml
```

## Step 11: Install AWS Load Balancer

```bash
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json
eksctl utils associate-iam-oidc-provider --region=us-west-2 --cluster=three-tier-cluster --approve
eksctl create iamserviceaccount --cluster=three-tier-cluster --namespace=kube-system --name=aws-load-balancer-controller --role-name AmazonEKSLoadBalancerControllerRole --attach-policy-arn=arn:aws:iam::626072240565:policy/AWSLoadBalancerControllerIAMPolicy --approve --region=us-west-2

sudo snap install helm --classic
helm repo add eks https://aws.github.io/eks-charts
helm repo update eks
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=my-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
kubectl get deployment -n kube-system aws-load-balancer-controller
kubectl apply -f full_stack_lb.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705154824872/49dd99f0-92db-4953-9f06-7915f1bc6750.png align="center")

## Step 12: Test the Application

### Access the Application

Open your web browser and navigate to the DNS of the AWS Load Balancer. This will take you to the frontend of your three-tier application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705154873593/23f26a39-c350-4f55-9cb6-07817d90f43c.png align="center")

### Create Tasks

1. On the frontend, you should see the application interface.
    
2. Click around and interact with the application, creating tasks to test the functionality.
    

### Verify MongoDB Entries

To ensure that entries are being added to the MongoDB database, follow these steps:

#### Access MongoDB Shell

```bash
# Example SSH command
kubectl exec -it -n workshop <mongodb-pod-name> -- mongo
```

#### Check Database and Collection

```bash
use todo
db.tasks.find()
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705155496318/83764b6a-e588-46ae-81ce-8efde59eca93.png align="center")

This will show you the entries in the `tasks` collection of the `todo` database. You should see the tasks you created through the application.

## Step 13: Configure Jenkins for CI/CD

### Configure AWS Credentials

1. In Jenkins, go to "Manage Jenkins" &gt; "Manage Credentials."
    
2. Under the "Stores scoped to Jenkins" section, click on "(global)".
    
3. Add new credentials:
    
    * Kind: Secret text
        
    * Access Key ID: Use the Jenkins credentials ID for Access Key.
        
    * Secret Access Key: Use the Jenkins credentials ID for Secret Access Key.
        

### Configure Kubeconfig Credential

1. In Jenkins, go to "Manage Jenkins" &gt; "Manage Credentials."
    
2. Under the "Stores scoped to Jenkins" section, click on "(global)".
    
3. Add new credentials:
    
    * Kind: Secret file
        
    * File: Upload the kubeconfig file.
        
    * ID: Set a unique ID for the credential.
        

Note: Kubeconfig file is in the path `/home/ubuntu/.kube/config.` Download it to your local using scp.

### Create a Jenkins Pipeline Job

1. In Jenkins, click on "New Item."
    
2. Choose "Pipeline" and give your job a name.
    
3. Under the "Pipeline" section, select "Pipeline script from SCM."
    
4. Set the SCM to Git and provide your repository URL.
    
5. In the "Script Path," specify the path to your Jenkinsfile (e.g., `Jenkinsfile`).
    
6. Save the job.
    

### Trigger the Pipeline

1. Make a change in your GitHub repository, commit, and push.
    
2. Jenkins should automatically detect the change and trigger the pipeline.
    
3. Monitor the Jenkins dashboard for the progress of each stage in the pipeline.
    

## Step 14: Verify CI/CD Deployment

### Check AWS ECR

1. Open the AWS ECR console.
    
2. Verify that the images for the frontend and backend have been pushed successfully.
    

### Check Kubernetes Deployment

1. Open your Kubernetes dashboard or use the following command:
    

```bash
kubectl --kubeconfig=/path/to/kubeconfig get deployments -n workshop
kubectl --kubeconfig=/path/to/kubeconfig get services -n workshop
kubectl --kubeconfig=/path/to/kubeconfig get pods -n workshop
```

1. Verify that the frontend and backend deployments are running.
    

### Make a Change in GitHub

1. Make another change in your GitHub repository, commit, and push.
    
2. Jenkins should automatically trigger the pipeline again.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705165593381/00a07881-0215-4127-8058-aa65eee36104.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705165696187/d0c4e788-3ea7-46c2-813c-c17c3d6e3e58.png align="center")

### Verify Updated Deployment

1. Check the AWS ECR console for new image versions.
    
2. Monitor the Jenkins dashboard for the progress of each stage in the updated pipeline.
    
3. Verify that the changes reflect in your Kubernetes deployment.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705165646113/a6f4c9a6-e2d7-46d5-9f1c-0263379b8d4c.png align="center")

### Conclusion

If you can access the application through the DNS and see the tasks you created in the MongoDB database, congratulations! You have successfully deployed and tested your three-tier application on Kubernetes.

Remember to clean up your resources after testing by deleting the EKS cluster and any associated resources to avoid incurring unnecessary costs. Use the following command:

```bash
eksctl delete cluster --name three-tier-cluster --region us-west-2
```

This will delete the EKS cluster and associated resources.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.