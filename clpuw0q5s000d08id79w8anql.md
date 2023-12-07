---
title: "A Beginner's Guide to VPC Peering in AWS: Connecting Instances Across Virtual Networks"
seoDescription: "Learn the step-by-step process of setting up VPC peering in AWS. Connect instances across different VPCs for seamless communication."
datePublished: Thu Dec 07 2023 07:39:31 GMT+0000 (Coordinated Universal Time)
cuid: clpuw0q5s000d08id79w8anql
slug: a-beginners-guide-to-vpc-peering-in-aws-connecting-instances-across-virtual-networks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701937506461/41857795-b8e7-4eda-9965-01678829475e.png
tags: cloud, software-development, aws, security, devops

---

### **Introduction**

Embarking on your cloud computing journey with AWS opens up a world of possibilities. One crucial aspect of managing your infrastructure efficiently is establishing connections between Virtual Private Clouds (VPCs). In this tutorial, we'll guide you through the process of setting up VPC peering, allowing seamless communication between instances in distinct VPCs.

---

### **Creating Test VPC**

*Title: Setting Up the Test Environment*

1. **Create a VPC:** Begin by creating a VPC named "test-vpc" with the CIDR block 10.0.0.0/16. This step lays the foundation for your testing environment.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933435678/79b6e01e-6029-4c34-bff2-2c452cfa72e8.png align="center")
    
3. **Subnet Creation:** Establish a subnet named "test-public-subnet" within "test-vpc" using the CIDR block 10.0.0.0/16. Subnets help organize resources within your VPC.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933490228/6d5d241f-528a-4f4e-a2ab-d9434180297b.png align="center")
    
5. **Route Table Configuration:** Create a route table named "test-rt" associated with "test-vpc." This table will define the traffic flow within the VPC.
    
6. **Internet Gateway Setup:** Introduce an internet gateway named "test-igw" and attach it to "test-vpc." This step enables instances within the VPC to communicate with the internet.
    
7. **Routing to Internet:** Edit the routes in the "test-rt" route table, allowing all access to the internet gateway "test-igw." This is a crucial step for outbound internet communication.
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933612375/c6dbcaab-8f42-4a73-b915-030f3640de0a.png align="center")
    
9. **Subnet Association:** Add the created subnet "test-public-subnet" to the route table associations. This associates the subnet with the specified route table.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933648424/a1ef8bf3-8c9a-446c-b4b6-371ea6481f32.png align="center")
    
11. **EC2 Instance Launch:** Launch an EC2 instance named "test-ec2-instance" within "test-vpc." Ensure to add an inbound rule for HTTP traffic and select CIDR 10.0.0.0/16.
    
12. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933692390/398a8326-9ba1-45ea-9f1b-5ff662388b24.png align="center")
    

---

### **Creating Prod VPC**

*Title: Setting Up the Production Environment*

1. **Create a VPC:** Mirror the steps for the production environment. Create a VPC named "prod-vpc" with the CIDR block 172.16.0.0/16.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933461497/ba694081-115b-446d-a40d-02c0325c9c38.png align="center")
    
3. **Subnet Creation:** Establish a subnet named "prod-public-subnet" within "prod-vpc" using the CIDR block 172.16.0.0/16.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933513563/5fea4739-86b8-4c77-8a3f-e93ba52f1fca.png align="center")
    
5. **Route Table Configuration:** Create a route table named "prod-rt" associated with "prod-vpc." This table will define the traffic flow within the production VPC.
    
6. **Internet Gateway Setup:** Introduce an internet gateway named "prod-igw" and attach it to "prod-vpc."
    
7. **Routing to Internet:** Edit the routes in the "prod-rt" route table, allowing all access to the internet gateway "prod-igw."
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933742516/36da75ea-1c3c-47bb-8d9c-da5104726d5a.png align="center")
    
9. **Subnet Association:** Add the created subnet "prod-public-subnet" to the route table associations.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933772634/8c14bfe6-083a-46aa-873f-7abebd8387f2.png align="center")
    
11. **EC2 Instance Launch:** Launch an EC2 instance named "prod-ec2-instance" within "prod-vpc." Ensure to add an inbound rule for HTTP traffic and select CIDR 172.16.0.0/16.
    
12. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933794408/e2e82ad4-29f4-458c-9c50-0090195009cc.png align="center")
    

---

### **Testing Isolation:**

*Title: Verifying VPC Isolation*

Now that both environments are set up, try to ping one EC2 instance from another. As expected, the attempt will fail, highlighting the isolated nature of these VPCs.

---

### **Setting Up VPC Peering**

*Title: Bridging the Gap with VPC Peering*

1. **Create Peering Connection:** Navigate to the VPC dashboard and select "Peering Connections." Create a peering connection, providing names for identification, and select both VPCs.
    
2. **Accept Peering Connection:** Once the peering connection is created, accept the connection request. This step establishes a direct link between the two VPCs.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933881845/45fcb252-f82d-4826-b14e-37097444afa6.png align="center")
    

---

### **Security Group Configuration**

*Title: Ensuring Secure Communication*

1. **Test EC2 Security Group:** Go to the security group of "test-ec2-instance" and edit inbound rules. Add rules for All ICMP IPv4, specifying CIDR blocks 10.0.0.0/16 and 172.16.0.0/16.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933929633/7fcd61ae-4643-4c0d-8aa9-80f5c759a381.png align="center")
    
3. **Prod EC2 Security Group:** Similarly, edit the inbound rules for the security group of "prod-ec2-instance." Add rules for All ICMP IPv4 with CIDR blocks 10.0.0.0/16 and 172.16.0.0/16.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701933975268/55ab499c-6039-4328-bf82-a546bbfcfeac.png align="center")
    

---

### **Route Table Adjustments**

*Title: Directing Traffic Across VPCs*

1. **Test Route Table:** In the "test-rt" route table, edit routes and add a route for the peering connection to "prod-vpc" with CIDR 172.16.0.0/16. This enables traffic from "test-vpc" to reach "prod-vpc."
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701934017442/326bd426-7f16-433a-a97f-258928fa243d.png align="center")
    
3. **Prod Route Table:** Similarly, in the "prod-rt" route table, add a route for the peering connection to "test-vpc" with CIDR 10.0.0.0/16. This allows traffic from "prod-vpc" to reach "test-vpc."
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701934040175/d1654488-b7f2-4606-881f-f85b5cefb4e9.png align="center")
    

---

### **Testing Communication**

*Title: Ensuring VPC Peering Success*

With VPC peering established and configurations in place, attempt to ping the EC2 instances across VPCs. This time, the ping should succeed, demonstrating the successful communication between instances in different VPCs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701934220362/fd389e24-0a4b-4566-8d1b-7327a46a664d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701934266162/b4df1548-c7a4-426b-abd1-5e2020cf233d.png align="center")

---

### **Conclusion**

In conclusion, this tutorial has walked you through the process of setting up VPC peering in AWS, connecting instances across different virtual networks. By following these steps, you've bridged the gap between isolated environments, enabling seamless communication. This fundamental skill is essential for building complex and interconnected architectures on the AWS cloud.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.