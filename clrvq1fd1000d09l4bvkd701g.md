---
title: "Day 82: Securely Hosting Your Website with Amazon S3 and CloudFront"
datePublished: Sat Jan 27 2024 06:59:17 GMT+0000 (Coordinated Universal Time)
cuid: clrvq1fd1000d09l4bvkd701g
slug: day-82-securely-hosting-your-website-with-amazon-s3-and-cloudfront
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706338693041/9cfbd908-ed38-4f2f-b572-09258849104d.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

In this tutorial, we will walk through the steps to securely host a static website using Amazon S3 for storage and Amazon CloudFront for content delivery. By using CloudFront, we can ensure secure and faster access to our website without making the S3 objects public.

### Step 1: Create an S3 Bucket

1. Log in to the AWS Management Console.
    
2. Navigate to the S3 service.
    
3. Click the "Create bucket" button.
    
4. Provide a unique and meaningful name for your bucket, and leave all other settings as default. Click "Create bucket."
    

### Step 2: Upload Your Files to S3

1. Select your newly created bucket.
    
2. Click the "Upload" button.
    
3. Choose the HTML file and any images you want to upload.
    
4. Click "Upload" to upload the files.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337433284/78b68fab-d7e1-4c7f-a635-c5044223d90a.png align="center")

### Step 3: Verify Access Denied

If you try to access the HTML file directly from the S3 object URL, you will receive an access denied error since the objects are not public.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337469910/4ea6ae99-a0e0-46b0-a364-437b90291622.png align="center")

### Step 4: Create a CloudFront Distribution

1. Navigate to the CloudFront service in the AWS Management Console.
    
2. Click the "Create Distribution" button.
    
3. In "Origin Domain", choose the S3 bucket created in Step 1.
    
4. In "Origin Access," select "Origin access control settings", and create a control setting.
    
5. In WAF, choose "Do not enable security protections".
    
6. In "Default Root Object," enter 'index.html.'
    
7. Click "Create Distribution." This process may take some time.
    

### Step 5: Set Up Origin Access Control

1. While the CloudFront distribution is being created, click on 'Copy Policy".
    
2. Go back to your S3 bucket in the AWS Management Console.
    
3. Navigate to the "Permissions" tab and click on "Bucket Policy."
    
4. Edit the bucket policy and paste the policy that you copied to grant CloudFront access to the S3 objects.
    
5. Save the bucket policy.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337718498/c1ebbf06-e901-4d46-9a74-daf8fe889756.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337729707/18f40730-335f-4aab-8084-0b215b91434f.png align="center")

### Step 6: Access Your Website Using CloudFront

1. Once the CloudFront distribution is created (check the status in the CloudFront console), copy the provided Distribution Domain Name.
    
2. Paste the Distribution Domain Name into a browser to access your website securely.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337776814/8aecad03-6a1f-4712-8c8a-4b8015c68613.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706337790227/68907dbb-cccf-42a6-a416-76a48a55c651.png align="center")

> If you reload the page, you will notice faster loading times for images due to CloudFront caching. CloudFront stores images in its edge locations, making subsequent retrievals quicker.

Congratulations! You have successfully set up a secure and efficient static website using Amazon S3 and CloudFront. The use of CloudFront's edge locations enhances the loading speed of your website's images upon reloads.