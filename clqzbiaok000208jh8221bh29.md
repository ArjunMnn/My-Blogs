---
title: "Day 64 & 65: Terraform with AWS"
datePublished: Thu Jan 04 2024 14:43:52 GMT+0000 (Coordinated Universal Time)
cuid: clqzbiaok000208jh8221bh29
slug: day-64-65-terraform-with-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704379310534/e6c38b6c-a4c3-4581-aee2-620746275050.png
tags: cloud, aws, devops, terraform, 90daysofdevops

---

## Introduction

In the previous tutorial, we learned how to provision an EC2 instance using Terraform. In this guide, we'll enhance our infrastructure by adding a security group to control incoming traffic to our EC2 instance. Additionally, we'll modify our Terraform configuration to include the creation of an EC2 instance with a simple website hosted on it.

## Task 1: Create a Security Group

Open your [`main.tf`](http://main.tf) file and add the following code to create a security group:

```bash
# main.tf

provider "aws" {
  region = "us-east-1"  # Set your desired AWS region
}

resource "aws_security_group" "web_server" {
  name_prefix = "web-server-sg"

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

Now, initialize and apply the Terraform configuration:

```bash
terraform init
terraform apply
```

Confirm the action by typing `yes` and pressing Enter.

## Task 2: Create an EC2 Instance

Update your [`main.tf`](http://main.tf) file with the following code to create an EC2 instance:

```bash
# main.tf

resource "aws_instance" "web_server" {
  ami           = "ami-0557a15b87f6559cf"  # Replace with your desired AMI
  instance_type = "t2.micro"
  key_name      = "my-key-pair"             # Replace with your key pair name
  security_groups = [
    aws_security_group.web_server.name
  ]

  user_data = <<-EOF
                #!/bin/bash
                sudo apt-get update -y
                sudo apt-get install -y apache2
                sudo systemctl start apache2
                sudo systemctl enable apache2
                echo "<h1>Welcome to my website!</h1>" | sudo tee /var/www/html/index.html > /dev/null
              EOF
}
```

Make sure to replace the `ami` and `key_name` values with your own. You can find a list of available AMIs in the AWS documentation.

Now, apply the changes:

```bash
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704379402250/32aa44d2-5d3f-4ca1-886f-5ffd30cfbd78.png align="center")

## Task 3: Access Your Website

Now that your EC2 instance is up and running, you can access the website hosted on it. Follow these steps:

1. Log in to the AWS Management Console.
    
2. Navigate to the EC2 instances section.
    
3. Find the public IP address or public DNS of the newly created EC2 instance.
    
4. Open a web browser and enter the public IP address or DNS in the address bar.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704379287508/53974129-d692-4ce3-bfc0-c961e0261f94.png align="center")

You should see the welcome message on the website hosted on your EC2 instance.

## Conclusion

Congratulations! You've successfully created a security group to control incoming traffic and provisioned an EC2 instance with a simple website using Terraform. This example demonstrates how Terraform can be used to manage and automate the deployment of AWS resources. Explore further to customize and expand your infrastructure based on your specific requirements.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.