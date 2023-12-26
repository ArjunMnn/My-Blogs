---
title: "Day 49: AWS Interview Questions"
seoDescription: "Prepare for your AWS interview with key questions on services, security, and infrastructure. Get ready to showcase your AWS expertise!"
datePublished: Tue Dec 26 2023 05:07:25 GMT+0000 (Coordinated Universal Time)
cuid: clqlvyaxm000908ichuc3cv4b
slug: day-49-aws-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703567124291/58a6863e-6936-4aab-8a49-f1f6ca371f93.png
tags: cloud, software-development, aws, devops, 90daysofdevops

---

### Question 1:

**Name 5 AWS services you have used and what's the use cases?**

**Answer:**

1. **Amazon S3 (Simple Storage Service):** Used for scalable object storage, ideal for hosting static websites or storing and retrieving large amounts of data.
    
2. **Amazon EC2 (Elastic Compute Cloud):** Provides scalable compute capacity in the cloud, commonly used for hosting applications.
    
3. **AWS Lambda:** Enables serverless computing, allowing you to run code without provisioning or managing servers.
    
4. **Amazon RDS (Relational Database Service):** Managed database service for relational databases like MySQL, PostgreSQL, and others.
    
5. **Amazon IAM (Identity and Access Management):** Manages access to AWS services and resources securely.
    

### Question 2:

**What are the tools used to send logs to the cloud environment?**

**Answer:** Commonly used tools for sending logs to the cloud include:

1. **Amazon CloudWatch Logs:** Collects and monitors log data.
    
2. **AWS CloudTrail:** Records AWS API calls for your account and delivers log files.
    

### Question 3:

**What are IAM Roles? How do you create/manage them?**

**Answer:** IAM Roles are AWS Identity and Access Management entities that define a set of permissions for making AWS service requests. They are not associated with a specific user or group but are assumed by trusted entities.

To create/manage IAM Roles:

1. Go to the IAM Console.
    
2. Choose "Roles" in the navigation pane.
    
3. Select "Create Role" and follow the wizard to define the role's permissions, trusted entities, and tags.
    

### Question 4:

**How to upgrade or downgrade a system with zero downtime?**

**Answer:** To achieve zero downtime during system upgrades or downgrades, you can use strategies like Blue-Green deployments or canary releases. This involves deploying the new version alongside the existing one and gradually shifting traffic.

### Question 5:

**What is infrastructure as code, and how do you use it?**

**Answer:** Infrastructure as Code (IaC) is the practice of managing and provisioning infrastructure through machine-readable script files. It allows for automated and consistent infrastructure deployment. AWS provides tools like AWS CloudFormation for defining and deploying IaC templates.

### Question 6:

**What is a load balancer? Give scenarios of each kind of balancer based on your experience.**

**Answer:** A load balancer distributes incoming network traffic across multiple servers to ensure no single server bears too much load. There are Application Load Balancers (ALBs) for HTTP/HTTPS traffic and Network Load Balancers (NLBs) for TCP/UDP traffic.

Scenario:

* **ALB:** Distributes web traffic to multiple EC2 instances for a scalable web application.
    
* **NLB:** Ensures even distribution of TCP traffic for a reliable and fault-tolerant application.
    

### Question 7:

**What is CloudFormation, and why is it used for?**

**Answer:** AWS CloudFormation is a service that helps you model and set up your Amazon Web Services resources so you can spend less time managing resources and more time focusing on your applications. It allows you to use a template to provision and deploy AWS infrastructure in a repeatable and automated way.

### Question 8:

**Difference between AWS CloudFormation and AWS Elastic Beanstalk?**

**Answer:**

* **CloudFormation:** Infrastructure as Code service, allowing you to define and provision AWS infrastructure.
    
* **Elastic Beanstalk:** Platform as a Service (PaaS) offering, simplifying application deployment and management. It abstracts infrastructure details.
    

### Question 9:

**What are the kinds of security attacks that can occur on the cloud? And how can we minimize them?**

**Answer:** Common security attacks include DDoS attacks, data breaches, and unauthorized access. To minimize them, employ measures such as:

* Regularly updating and patching systems.
    
* Using firewalls and security groups.
    
* Implementing encryption for data at rest and in transit.
    
* Monitoring and auditing activities with services like AWS CloudTrail.
    

### Question 10:

**Can we recover the EC2 instance when we have lost the key?**

**Answer:** Yes, you can recover an EC2 instance when you have lost the key by creating an Amazon Machine Image (AMI) of the instance, launching a new instance from the AMI, and specifying a new key pair.

### Question 11:

**What is a gateway?**

**Answer:** In AWS, a gateway is a network device that connects different networks. For example, an Amazon VPC (Virtual Private Cloud) can be connected to an on-premises network using an AWS VPN Gateway.

### Question 12:

**What is the difference between Amazon RDS, DynamoDB, and Redshift?**

**Answer:**

* **Amazon RDS:** Managed relational database service supporting various database engines.
    
* **DynamoDB:** Fully managed NoSQL database service designed for high-performance applications.
    
* **Redshift:** Fully managed data warehouse service designed for analytics queries on large datasets.
    

### Question 13:

**Do you prefer to host a website on S3? What's the reason if your answer is either yes or no?**

**Answer:** Yes, hosting a website on Amazon S3 is often a cost-effective and scalable solution. S3 provides low-latency access to content, supports static website hosting, and integrates well with other AWS services. It also simplifies content distribution through services like Amazon CloudFront.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.