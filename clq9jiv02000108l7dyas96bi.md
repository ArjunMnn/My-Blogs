---
title: "Day 42 & 43: S3 Programmatic access with AWS-CLI"
seoDescription: "Master AWS CLI for S3: Launch EC2, manage snapshots, and seamlessly interact with S3. Your step-by-step guide to AWS automation."
datePublished: Sun Dec 17 2023 13:46:15 GMT+0000 (Coordinated Universal Time)
cuid: clq9jiv02000108l7dyas96bi
slug: day-42-43-s3-programmatic-access-with-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702820683962/0613cd2e-d988-4d2b-9672-12d1203ec701.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

## Introduction

Amazon Simple Storage Service (S3) is a highly scalable and durable object storage service provided by Amazon Web Services (AWS). In this blog post, we will explore how to leverage AWS Command Line Interface (AWS CLI) for programmatic access to S3. We'll cover two tasks that involve launching an EC2 instance, creating an S3 bucket, uploading and accessing files, creating EC2 snapshots, and downloading files from S3 using the AWS CLI.

## Task-01: Setting Up EC2 Instance and S3 Bucket

### Step 1: Launch an EC2 Instance

1. Log in to the AWS Management Console.
    
2. Navigate to the EC2 service.
    
3. Click on "Launch Instance" and follow the wizard to configure your EC2 instance.
    
4. Download the key pair and launch the instance.
    

### Step 2: Connect to the EC2 Instance

1. Open a terminal window.
    
2. Use the downloaded key pair to SSH into the EC2 instance:
    

```bash
ssh -i path/to/keypair.pem ec2-user@<your-instance-ip>
```

### Step 3: Create an S3 Bucket and Upload a File

1. In the AWS Management Console, go to the S3 service.
    
2. Click "Create Bucket" and follow the prompts to create a bucket.
    
3. Upload a file to the bucket.
    

### Step 4: Access the File from the EC2 Instance using AWS CLI

1. Install AWS CLI on the EC2 instance:
    

```bash
sudo yum install aws-cli -y
```

1. Configure AWS CLI with your credentials:
    

```bash
aws configure
```

1. Use the following command to copy the file from S3 to the EC2 instance:
    

```bash
aws s3 cp s3://your-bucket-name/your-file.txt /path/on/ec2/instance/
```

## Task-02: Creating EC2 Snapshots and Downloading from S3

### Step 1: Create a Snapshot of the EC2 Instance

1. In the AWS Management Console, navigate to the EC2 service.
    
2. Right-click on your running instance, select "Create Image," and follow the prompts to create a snapshot.
    

### Step 2: Launch a New EC2 Instance from the Snapshot

1. In the AMIs section of the EC2 service, launch a new instance using the created snapshot.
    

### Step 3: Download a File from S3 Using AWS CLI

1. On the new EC2 instance, install and configure AWS CLI as in Task-01.
    
2. Use the following command to download the file from S3:
    

```bash
aws s3 cp s3://your-bucket-name/your-file.txt /path/on/ec2/instance/
```

### Step 4: Verify Contents on Both EC2 Instances

1. Compare the contents of the file on both EC2 instances:
    

```bash
diff /path/on/first/ec2/instance/your-file.txt /path/on/second/ec2/instance/your-file.txt
```

This command will show no output if the files are identical.

## Conclusion

By following the detailed steps outlined in this blog post, you should now have a solid understanding of how to perform S3 programmatic access with AWS CLI. Whether you are managing EC2 instances, creating snapshots, or interacting with S3 buckets, the AWS CLI provides a powerful and flexible interface for automating your AWS workflows.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Check out my [**GitHub**](https://github.com/ArjunMnn) profile.