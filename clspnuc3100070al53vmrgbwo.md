---
title: "Day 89: Mounting AWS S3 Bucket on Amazon EC2 Linux Using S3FS"
datePublished: Sat Feb 17 2024 05:50:52 GMT+0000 (Coordinated Universal Time)
cuid: clspnuc3100070al53vmrgbwo
slug: day-89-mounting-aws-s3-bucket-on-amazon-ec2-linux-using-s3fs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708148552230/40ea3750-e461-49c7-a24b-b18a1e7b4f4e.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

In this tutorial, we will walk through the steps to mount an AWS S3 bucket on an Amazon EC2 Linux instance using S3FS. This process involves setting up an IAM user, configuring AWS CLI, installing and configuring S3FS, and finally mounting the S3 bucket on the EC2 instance.

**Task 1: Setting Up an IAM User**

1. **Log in to AWS Management Console**: Go to the AWS Management Console and sign in to your AWS account.
    
2. **Navigate to IAM Service**: Once logged in, navigate to the IAM service by typing "IAM" in the search bar or locating it under the "Security, Identity, & Compliance" section.
    
3. **Create a New IAM User**: Click on "Users" from the left-hand menu and then select "Add user." Enter a username for the new IAM User.
    
4. **Set Permissions**: Set permissions for S3 access by assigning a policy. You can either create a new policy or use an existing one that provides the necessary S3 access permissions.
    
5. **Review and Create User**: Review the user details and create the user. Ensure to securely save the provided access key and secret access key.
    

**Setting Up AWS CLI on EC2 Instance**

1. **Log in to EC2 Instance**: Connect to your EC2 Linux instance using SSH.
    
2. **Install AWS CLI**: If AWS CLI is not already installed, update the package list and install AWS CLI by running the following commands:
    

```bash
sudo apt update
sudo apt install awscli -y
```

1. **Configure AWS CLI**: Configure AWS CLI by running `aws configure` and providing the access key, secret key, default region, and preferred output format.
    

```bash
aws configure
```

1. **Test AWS Configuration**: Verify the AWS configuration by running `aws s3 ls` to list your S3 buckets. If configured correctly, it should display a list of buckets.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708148724091/68b0d6c4-687e-416c-b126-7513232236ca.png align="center")

**Task 2: Mounting the S3 Bucket Using S3FS**

1. **Install S3FS**: Install S3FS by updating the package list and installing S3FS using the following commands:
    

```bash
sudo apt-get update
sudo apt-get install s3fs -y
```

1. **Create Mount Directory**: Create a directory for mounting the S3 bucket. For example, create a directory named "bucket" in your home directory:
    

```bash
mkdir /home/ubuntu/bucket
```

1. **Add Files to Directory**: Add some files to the "bucket" directory. You can create empty files using the `touch` command.
    

```bash
cd /home/ubuntu/bucket
touch day89.txt arjun.txt hello.txt
```

1. **Mount S3 Bucket**: Mount your S3 bucket using S3FS. Replace `<your-bucket-name>` with the actual name of your S3 bucket:
    

```bash
aws s3 sync /home/ubuntu/bucket s3://<your-bucket-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708148794962/add0f4c4-cbf7-4255-a051-8ea7fe05a5ff.png align="center")

**Accessing S3 Data**

Your S3 bucket is now successfully mounted in the "bucket" directory. Navigate to the directory and access the contents of the S3 bucket as if they are local files on your EC2 instance.

```yaml
cd /home/ubuntu/bucket
ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708148773086/6de329fe-f452-4580-b834-369dbdce2e78.png align="center")

By following these steps, you have accomplished creating an IAM user, configuring AWS CLI, installing and configuring S3FS, and mounting an S3 bucket on your Amazon EC2 instance. You can now seamlessly work with your S3 data directly from your EC2 instance.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.