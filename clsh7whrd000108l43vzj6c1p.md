---
title: "Day 86: Deploying a Static Website on AWS S3 Using GitHub Actions"
datePublished: Sun Feb 11 2024 08:02:29 GMT+0000 (Coordinated Universal Time)
cuid: clsh7whrd000108l43vzj6c1p
slug: day-86-deploying-a-static-website-on-aws-s3-using-github-actions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707638378782/554c3597-a24b-42ec-881f-fbdf6e61e9fa.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

In this tutorial, we'll walk through the process of deploying a static website to AWS S3 using GitHub Actions. We'll set up an S3 bucket, configure it for static website hosting, and then create a GitHub Actions workflow to automatically deploy changes to the S3 bucket whenever changes are pushed to the repository.

## Prerequisites

Before we begin, make sure you have the following:

* An AWS account with permissions to create S3 buckets and IAM roles.
    
* A GitHub account.
    

## Step 1: Create an S3 Bucket

1. Log in to your AWS Management Console.
    
2. Navigate to the S3 service.
    
3. Click on "Create bucket".
    
4. Provide a unique name for your bucket and choose the region.
    
5. Leave other settings as default and proceed to create the bucket.
    

## Step 2: Configure Bucket Policy

1. Once the bucket is created, click on it to open its properties.
    
2. Go to the "Permissions" tab and click on "Bucket Policy".
    
3. Paste the following bucket policy, replacing `YOUR_BUCKET_NAME` with your actual bucket name:
    

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
        }
    ]
}
```

1. Click "Save" to apply the policy.
    

## Step 3: Configure Static Website Hosting

1. Still in the bucket properties, navigate to the "Static website hosting" tab.
    
2. Click on "Edit".
    
3. Enter `index.html` in the "Index document" field.
    
4. Click "Save".
    

## Step 4: Set Up GitHub Actions Workflow

1. Go to your GitHub repository where your static website code resides.
    
2. Click on the "Actions" tab.
    
3. Click on "Create new workflow" and choose "Set up a workflow yourself".
    
4. Paste the following workflow code into the editor:
    

```bash
name: Portfolio Deployment

on:
  push:
    branches:
    - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v1

    - name: Configure AWS Credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-1

    - name: Deploy static site to S3 bucket
      run: aws s3 sync . s3://YOUR_BUCKET_NAME --delete
```

1. Replace `YOUR_BUCKET_NAME` with the name of your S3 bucket.
    
2. Click on "Start commit" and then "Commit new file" to save the workflow file.
    

## Step 5: Test Deployment

1. Make any changes to your website code locally.
    
2. Commit and push the changes to your GitHub repository.
    
3. Go to the "Actions" tab on GitHub to monitor the workflow execution.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707638495500/6433b09c-2d73-4cea-b880-f5fe7b20d7ac.png align="center")
    
5. Once the workflow completes successfully, visit your S3 bucket URL to see the deployed website.
    
6. Any further changes made to the repository will trigger the workflow automatically, updating the deployed website accordingly.
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707638512461/379e1be1-a029-471f-8652-ecc531e657a7.png align="center")
    

Congratulations! You have successfully set up automated deployment of your static website to AWS S3 using GitHub Actions.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.