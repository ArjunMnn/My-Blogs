---
title: "Day 67: AWS S3 Bucket Creation and Management"
datePublished: Sat Jan 06 2024 13:55:38 GMT+0000 (Coordinated Universal Time)
cuid: clr24nz36000708l6hrgs7qid
slug: day-67-aws-s3-bucket-creation-and-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704549302649/e7146e12-9b8a-49d1-9eed-059d3833a03f.png
tags: cloud, aws, devops, terraform, 90daysofdevops

---

## Introduction

Amazon Simple Storage Service (S3) is a scalable object storage service that allows you to store and retrieve any amount of data from anywhere on the web. Terraform is a powerful infrastructure as code (IaC) tool that enables you to define and provision infrastructure in a declarative configuration language. In this tutorial, we will walk through the process of creating and managing an S3 bucket using Terraform, including configuring public read access, setting up bucket policies, and enabling versioning.

## Step 1: Set Up Your Terraform Environment

Before you start managing your S3 bucket, make sure you have Terraform installed on your local machine. You can download Terraform from [terraform.io](http://terraform.io) and follow the installation instructions.

Once installed, create a new directory for your Terraform configuration files and navigate to it in your terminal.

```bash
mkdir terraform-s3-example
cd terraform-s3-example
```

## Step 2: Create a Terraform Configuration File

Create a new file named [`main.tf`](http://main.tf) in your project directory. This file will contain the Terraform configuration for your S3 bucket.

```bash
provider "aws" {
  region = "us-east-1"  # Set your desired AWS region
}

resource "aws_s3_bucket" "my_bucket" {
  bucket = "my-unique-bucket-name"  # Replace with your desired bucket name
  acl    = "public-read"
  
  versioning {
    enabled = true
  }
}
```

Replace `"my-unique-bucket-name"` with a globally unique name for your S3 bucket. The `acl` attribute is set to `"public-read"` to allow public read access.

## Step 3: Configure Public Read Access

In the same [`main.tf`](http://main.tf) file, add the following code to configure public read access for your S3 bucket.

```bash
resource "aws_s3_bucket_policy" "public_access" {
  bucket = aws_s3_bucket.my_bucket.bucket

  policy = <<EOF
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "${aws_s3_bucket.my_bucket.arn}/*"
    }
  ]
}
EOF
}
```

This block creates an S3 bucket policy allowing public read access to the objects in your bucket.

## Step 4: Create an S3 Bucket Policy for IAM User/Role Access

To create a policy that allows read-only access to a specific IAM user or role, add the following code to your [`main.tf`](http://main.tf) file.

```bash
resource "aws_iam_user" "s3_user" {
  name = "s3-read-only-user"  # Replace with your desired IAM user name
}

resource "aws_s3_bucket_policy" "user_access" {
  bucket = aws_s3_bucket.my_bucket.bucket

  policy = <<EOF
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "${aws_iam_user.s3_user.arn}"
      },
      "Action": "s3:GetObject",
      "Resource": "${aws_s3_bucket.my_bucket.arn}/*"
    }
  ]
}
EOF
}
```

This code creates an IAM user named `"s3-read-only-user"` and associates a bucket policy allowing read-only access.

## Step 5: Apply Your Terraform Configuration

Save your [`main.tf`](http://main.tf) file, and in your terminal, run the following commands to initialize and apply your Terraform configuration.

```bash
terraform init
terraform apply
```

Follow the prompts to confirm the changes. Terraform will create the specified resources in your AWS account.

## Conclusion

Managing AWS resources with Terraform provides a streamlined and consistent approach to infrastructure management. In this tutorial, we covered the fundamentals of creating an S3 bucket, configuring public read access, establishing IAM user or role policies, and enabling versioning.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.