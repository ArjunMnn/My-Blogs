---
title: "Building a Mass Emailing System Using AWS Lambda and SES"
datePublished: Wed May 01 2024 07:00:48 GMT+0000 (Coordinated Universal Time)
cuid: clvngxb1r00060aih7lkt7qde
slug: building-a-mass-emailing-system-using-aws-lambda-and-ses
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714546457398/3dae2bd0-82d7-45f7-a21d-20e5f929ae77.png
tags: cloud, software-development, aws, software-engineering, serverless

---

A mass emailing system allows businesses to reach out to customers efficiently, and building one using Amazon Web Services (AWS) can be both scalable and cost-effective. In this blog post, I'll guide you through setting up a mass emailing system using AWS Lambda, Simple Email Service (SES), and S3.

### Step 1: Create an S3 Bucket

Amazon S3 will store the CSV files containing the email addresses of the recipients.

1. **Navigate to S3:** In the AWS Management Console, click on “S3” under the Storage category.
    
2. **Create a Bucket:** Click on “Create bucket”. Name your bucket (it must be unique across AWS), select a region close to you for better performance, and then create the bucket.
    

### Step 2: Set Up AWS Simple Email Service (SES)

AWS SES will handle the email sending operations.

1. **Navigate to SES**
    
2. **Verify Your Email Address:** Before sending emails, SES requires verification of your ownership of the email address. On the left pane, go to **Identities,** and then verify the email address you want to send from.
    

**Important Note: As we are using SES in sandbox mode, you must manually verify each email address that you wish to send emails to before they can receive emails from your application. This is a restriction in the sandbox environment intended to prevent spam and abuse.**

3. **Add and verify all Recipient Email Addresses:** You can use Temp Mail for testing.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714545254466/2316f540-3c6f-45ef-b9b9-57319de9e70a.png align="center")

### Step 3: Create an IAM Role for Lambda

This role will allow your Lambda function to access AWS resources securely.

1. **Navigate to IAM:** Go to “IAM” under Security, Identity, & Compliance.
    
2. **Create a New Role:** Click on “Roles”, then “Create role”. Choose “Lambda” for the service that will use this role, then proceed to permissions.
    
3. **Attach Policies:** Add policies like AmazonSESFullAccess, AmazonS3FullAccess, and AWSLambdaExecute.
    

### Step 4: Create a Lambda Function

This function will process the CSV file and send emails.

1. **Navigate to Lambda:** Go to “Lambda” under Compute.
    
2. **Create Function:** Choose “Author from scratch”, name your function, select Python 3.x for the runtime.
    
3. **Set Permissions:** Choose the IAM role you created earlier.
    
4. **Create Function:** Finalize the creation of your function.
    

### Step 5: Write Lambda Function Code

The function will read from S3, parse CSV, and send emails via SES.

```python
import boto3
import csv

def lambda_handler(event, context):
    s3 = boto3.client('s3')
    ses = boto3.client('ses')
    bucket_name = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    response = s3.get_object(Bucket=bucket_name, Key=key)
    lines = response['Body'].read().decode('utf-8').split()
    for row in csv.DictReader(lines):
        ses.send_email(
            Source='your-verified-email@example.com',
            Destination={'ToAddresses': [row['email']]},
            Message={
                'Subject': {'Data': 'Your Email Subject'},
                'Body': {'Text': {'Data': "Your email content"}}
            }
        )
```

### Step 6: Set Up S3 Event Trigger

Trigger your Lambda function when a CSV file is uploaded to S3.

1. **Select Your Function:** In Lambda, open your function’s configuration.
    
2. **Add Trigger:** Choose “S3” from the list. Configure the trigger for “PUT” events, and set the file prefix or suffix (like .csv).
    
3. **Save:** Save your configuration.
    

### Step 7: Test Your Setup

Upload a CSV file with an ‘email’ column to your S3 bucket and check the Lambda execution logs. Make sure the emails are being sent out successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714545363288/b7f75b71-dbfa-4095-8e07-9823cc69215f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714545344937/c3736750-f0b1-423a-aa75-d64c5aa258ce.png align="center")

**Email Recieved:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714545572478/85e675ab-2e43-4ba6-804a-a33b3d24437d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714545583936/6632ecfb-889b-4a51-9557-0c45add5f6e4.png align="center")

**Reminder: As we are using SES in sandbox mode, you must manually verify each email address that you wish to send emails to before they can receive emails from your application. This is a restriction in the sandbox environment intended to prevent spam and abuse.**

### Conclusion

You've now successfully set up a basic mass emailing system using AWS. This system is not only scalable but also cost-effective, perfect for businesses looking to manage their email marketing efforts. Always ensure to comply with legal requirements and manage opt-ins and opt-outs to respect user privacy and avoid spam.