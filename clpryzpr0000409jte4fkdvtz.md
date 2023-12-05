---
title: "Day 3: S3, AWS CLI, and IAM"
seoDescription: "Day 3 of the AWS Challenge delves into securing data with private S3 buckets, configuring AWSCLI on Ubuntu for command-line efficiency, and mastering IAM."
datePublished: Tue Dec 05 2023 06:39:24 GMT+0000 (Coordinated Universal Time)
cuid: clpryzpr0000409jte4fkdvtz
slug: day-3-s3-aws-cli-and-iam
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701758326913/dc1f05f8-8c28-41c6-b9c4-92d313c82f35.png
tags: cloud, software-development, aws, security, devops

---

Embarking on Day 3 of the "7 Days of AWS Challenge," let's simplify the AWS landscape for beginners. Today, we'll explore creating private S3 buckets, configuring AWSCLI on Ubuntu, and laying the foundation for IAM (Identity and Access Management).

### **Securing Your Data: Private S3 Buckets in AWS**

**Creating a Private S3 Bucket:**

1. **Access AWS Console:** Log in to AWS and find the S3 service.
    
2. **Bucket Creation:** Click "Create Bucket" and follow the prompts, ensuring the bucket is private.
    
3. **Policy Adjustment:** Modify the bucket policy to allow your IAM user access while keeping it private.
    

Ensuring the security of your S3 bucket is crucial. Follow these simple steps to keep your data safe and accessible only to authorized users.

### **Command-Line Basics: Configuring AWSCLI on Ubuntu**

**Setting Up AWSCLI:**

1. **Installation:** Open your terminal on Ubuntu and run below commands:
    
2. ```json
    sudo apt update
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    sudo apt install unzip
    unzip awscliv2.zip
    sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update
    ```
    
3. **Configuration:** Execute `aws configure` and input your AWS access key, secret key, default region, and output format.
    

Now, you're ready to harness the power of AWSCLI directly from your Ubuntu terminal. Simple, right?

### **Commanding the Cloud: Creating an EC2 Instance with AWSCLI**

**Crafting an EC2 Instance:**

1. **Command Execution:** Use `below commands` to create an EC2 instance. Specify AMI, instance type, and key pair.
    
2. ```json
    aws ec2 create-key-pair --key-name MyKeyPair
    ```
    
    ```json
    aws ec2 authorize-security-group-ingress --group-id=<security-group-id> --protocol=tcp --port=443 --cidr=0.0.0.0/0
    aws ec2 authorize-security-group-ingress --group-id=<security-group-id> --protocol=tcp --port=22 --cidr=0.0.0.0/0
    aws ec2 authorize-security-group-ingress --group-id=<security-group-id> --protocol=tcp --p
    ```
    
    ```json
    aws ec2 run-instances --image-id=ami-0fc5d935ebf8bc3bc --instance-type=t2.micro --region=u
    ```
    
    **Verification:** Confirm the instance creation with `aws ec2 describe-instances`.
    

With a few commands, you've spawned a virtual server, showcasing the magic of AWSCLI.

### **IAM Basics: Tailoring Access for Your Team**

**Scenario: Configuring IAM for Alex at GlobalTech Inc.**

**Configuring IAM for Alex's AWS Access:**

**Understanding IAM Basics:** Before we dive into the specifics, let's recap the essence of IAM. IAM is AWS's access management service, enabling you to control who can access your AWS resources and what actions they can perform.

1. **Accessing IAM Console:** Head to the AWS Management Console and locate the IAM service.
    
2. **Creating a New IAM User - Alex:** Begin by creating a new IAM user for Alex. Specify the user details and choose programmatic access for AWS CLI usage.
    
3. **Assigning IAM Policies:** IAM policies define permissions. For Alex's role, we'll create custom policies to grant access to EC2 instances and S3 bucket creation.
    

### **Granting Access to View EC2 Instances**

**Creating an EC2 Monitoring Policy:**

1. **Policy Creation:** Craft a new IAM policy named "EC2-Monitoring-Policy" allowing the `ec2:DescribeInstances` action.
    
    ```json
    {
       "Version":"2012-10-17",
       "Statement":[
          {
             "Effect":"Allow",
             "Action":"ec2:DescribeInstances",
             "Resource":"*"
          }
       ]
    }
    ```
    
2. **Attaching the Policy:** Attach this policy to Alex's IAM user. Now, Alex has the capability to view, but not modify, EC2 instances.
    

### **Granting Access to Create S3 Buckets**

**Designing an S3 Bucket Creation Policy:**

1. **Policy Creation:** Develop a new IAM policy named "S3-Bucket-Creation-Policy" granting the `s3:CreateBucket` action.
    
    ```json
    {
       "Version":"2012-10-17",
       "Statement":[
          {
             "Effect":"Allow",
             "Action":"s3:CreateBucket",
             "Resource":"*"
          }
       ]
    }
    ```
    
2. **Attaching the Policy:** Attach this policy to Alex's IAM user. Now, Alex holds the authority to create S3 buckets for diverse projects.
    

### **Testing Alex's Access**

**Verification for Peace of Mind:**

1. **IAM User Credentials:** Ensure Alex has received the necessary IAM user credentials.
    
2. **AWS CLI Check - EC2 Instances:** Let Alex use AWS CLI with the configured credentials to run `aws ec2 describe-instances`. The response should display information on EC2 instances.
    
3. **AWS CLI Check - S3 Bucket Creation:** Encourage Alex to run `aws s3 mb s3://new-project-bucket`. Success here confirms Alex's ability to create S3 buckets.
    

---

### **Conclusion**

Congratulations on completing Day 3 of the "7 Days of AWS Challenge"! Today's journey introduced you to private S3 buckets, AWSCLI on Ubuntu, and IAM basics in a beginner-friendly manner.

Stay tuned for Day 4, where we'll explore more AWS wonders, making your cloud journey enjoyable and educational!

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.