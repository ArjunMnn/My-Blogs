---
title: "Day 2: Building a Secure Foundation with WAF"
seoDescription: "Elevate your AWS skills on Day 2 as we explore WAF, Auto Scaling, and Docker deployment. Learn to secure your infrastructure, deploy a Todo List App, and tr"
datePublished: Sun Dec 03 2023 15:43:56 GMT+0000 (Coordinated Universal Time)
cuid: clppnkaeb000409l78zka4pbs
slug: day-2-building-a-secure-foundation-with-waf
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701618167241/b13499af-0f9d-496c-8a5e-b8a4334302f7.png
tags: cloud, software-development, aws, devops, software-engineering

---

### **Introduction:**

Welcome back to the 7 Days of AWS challenge! Today, we'll focus on fortifying our infrastructure with AWS Web Application Firewall (WAF). Buckle up as we delve into the essentials of WAF and embark on a hands-on project to bolster our security measures.

---

### **Understanding AWS Web Application Firewall (WAF):**

AWS Web Application Firewall (WAF) is your shield against malicious attacks on your web applications. It allows you to create custom rules that filter and monitor HTTP and HTTPS requests. WAF works seamlessly with Amazon CloudFront and Application Load Balancers, giving you granular control over the traffic entering your applications.

To get started, navigate to the AWS WAF console. Here, you can create WebACLs (Access Control Lists) to define the rules that govern which requests are allowed or denied. The rule sets include conditions such as IP addresses, geographic locations, and even custom rules based on the content of the requests.

---

### **Hands-On Project: Building a Secure Infrastructure**

**Step 1 - Creating a Launch Template:**

Our first step is to create a Launch Template, a powerful resource that defines the parameters for launching instances within our Auto Scaling Groups.

1. In the EC2 Dashboard, find the "Launch Templates" section.
    
2. Click "Create Launch Template" and configure the necessary settings, including the Amazon Machine Image (AMI), instance type, and storage.
    
3. In the "Advanced Details" section, under "User data," paste the following script to deploy a todo list web app from a Docker image:
    
4. ```bash
    #!/bin/bash
    
    # Update the package list
    sudo apt-get update -y
    
    # Install Docker
    sudo apt-get install -y docker.io
    sudo systemctl start docker
    sudo systemctl enable docker
    
    # Pull the Docker image from DockerHub
    sudo docker pull arjunmmnn/todo-app:latest
    
    # Run the Docker container, exposing port 8001
    sudo docker run -d -p 80:8001 arjunmmnn/todo-app:latest
    ```
    
5. Save the template.
    

**Step 2 - Auto Scaling Group (ASG):**

Now, let's use the Launch Template to set up an Auto Scaling Group, ensuring our applications can handle varying workloads seamlessly.

1. In the EC2 Dashboard, under "Auto Scaling Groups," click "Create Auto Scaling Group."
    
2. Select the Launch Template you created earlier.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701613826407/bf2814b7-a258-4330-bf69-ff2ea16d6a6a.png align="center")
    
4. Configure scaling policies, desired capacity, and other parameters.
    
5. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701613948556/ae819468-0cc4-43b5-aa7c-93adf03e8e03.png align="center")
    
6. Complete the setup.
    

**Step 3 - Application Load Balancer (ALB):**

With our Auto Scaling Group in place, it's time to distribute traffic efficiently using an Application Load Balancer.

1. In the EC2 Dashboard, navigate to "Load Balancers" and click "Create Load Balancer."
    
2. Choose "Application Load Balancer" and configure the settings, including listener configurations.
    
3. Add the instances from your Auto Scaling Group to the target group.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701613905813/0df7912f-55d9-466c-96c0-e77fd82ae3da.png align="center")
    

---

### **Securing Your Infrastructure with WAF:**

**Subtitle: Step 4 - Configuring WAF WebACL:**

Now that our infrastructure is set up let’s enhance its security by configuring a WebACL in WAF.

1. In the AWS WAF console, go to WebACLs and click "Create WebACL."
    
2. Define the conditions for your WebACL, specifying the rules to allow or block requests.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701614012367/71e331e9-d8ca-409f-825f-e21d0f78317b.png align="center")
    
4. Associate the WebACL with your Application Load Balancer.
    

By configuring a WAF WebACL, you add an additional layer of protection to your applications, safeguarding them against various cyber threats.

**Subtitle: Step 5 - Testing the Todo App:**

It's time to put our todo list web app to the test. Open your web browser and navigate to:

```plaintext
http://<Your_Load_Balancer_DNS_Name>:80
```

Replace `<Your_Load_Balancer_DNS_Name>` with the DNS name of your Application Load Balancer. If everything is configured correctly, you should see your todo list web app in action. Congratulations on successfully deploying and testing your application!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701616479078/ff636707-b5b6-4a92-af34-b49888758b07.png align="center")

---

### **Conclusion:**

Congratulations! You've successfully strengthened your AWS infrastructure on Day 2 of the challenge. Understanding the nuances of AWS Web Application Firewall and implementing a secure project with launch templates, auto-scaling groups, and application load balancers are crucial steps in your AWS journey.

Stay tuned for Day 3, where we'll explore more AWS services to optimize and enhance your cloud experience. Remember, each day brings us closer to mastering the art of AWS.

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [GitHub](https://github.com/ArjunMnn) profile.