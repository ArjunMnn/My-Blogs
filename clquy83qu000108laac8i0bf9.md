---
title: "Day 60 & 61: Terraform"
datePublished: Mon Jan 01 2024 13:20:57 GMT+0000 (Coordinated Universal Time)
cuid: clquy83qu000108laac8i0bf9
slug: day-60-61-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704115172570/ba492345-8b4b-45cc-978b-60aa5e5c8d02.png
tags: cloud, software-development, devops, terraform, 90daysofdevops

---

## Introduction to Terraform

Welcome to the world of Terraform, a game-changer in the realm of Infrastructure as Code (IaC). In this comprehensive guide, we'll take you on a journey from installation to mastering essential commands, ensuring you harness the full potential of Terraform.

### **Task 1: Installing Terraform**

Follow the official documentation [here](https://developer.hashicorp.com/terraform/install#Linux), or simply use the below 3 commands to install terraform:

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```

### **Task 2: Unveiling Terraform Concepts**

#### **1\. Why do we use Terraform?**

Terraform is essential for its ability to provide a standardized, version-controlled approach to managing infrastructure. It ensures repeatability, scalability, and automation, making it a cornerstone in modern DevOps practices.

#### **2\. What is Infrastructure as Code (IaC)?**

IaC involves managing and provisioning infrastructure through machine-readable script files rather than traditional hardware configuration. Terraform embraces this paradigm, allowing users to declare and manage infrastructure as code.

#### **3\. What is Resource?**

In Terraform, a resource is a fundamental unit representing an infrastructure component. It can be a virtual machine, network, or storage. Resources are defined in Terraform configuration files, specifying their attributes and configurations.

#### **4\. What is Provider?**

A provider in Terraform acts as a bridge between Terraform and different infrastructure or cloud services. Providers are responsible for managing and manipulating resources using their respective APIs.

#### **5\. What is the State file in Terraform? What's its importance?**

The Terraform state file keeps track of the current state of your infrastructure. It records resource relationships and dependencies, ensuring Terraform understands which resources are deployed and their configurations. This file is crucial for maintaining consistency between declared and actual infrastructure.

#### **6\. What is Desired and Current State?**

The desired state is the configuration specified in Terraform files, indicating how the infrastructure should be. The current state is the actual state recorded in the Terraform state file. Terraform continuously works to converge the current state towards the desired state.

### **Task 3: Mastering Essential Terraform Commands**

Now that you have a solid understanding of Terraform concepts, let's explore key commands that are instrumental in your Terraform workflow.

#### **1\. terraform init**

Use `terraform init` to initialize a Terraform working directory. This downloads necessary provider plugins and sets up the backend.

#### **2\. terraform init -upgrade**

Upgrade installed provider plugins with `terraform init -upgrade` to ensure you have the latest versions.

#### **3\. terraform plan**

Run `terraform plan` to generate an execution plan. It provides insights into the actions Terraform will take to achieve the desired state.

#### **4\. terraform apply**

Execute `terraform apply` to apply the changes proposed in the execution plan. Confirm before making any modifications to your infrastructure.

#### **5\. terraform validate**

Ensure configuration correctness with `terraform validate`. It checks for syntax errors and validates the configuration against Terraform's language constructs.

#### **6\. terraform fmt**

Maintain consistent code style using `terraform fmt`. It formats your code according to Terraform conventions.

#### **7\. terraform destroy**

When it's time to decommission your infrastructure, use `terraform destroy`. This command systematically tears down all resources defined in your Terraform configuration.

#### **terraform destroy**

When it's time to decommission your infrastructure, rely on `terraform destroy` to systematically tear down all resources defined in your Terraform configuration.

## Conclusion

Terraform is not just a tool; it's a paradigm shift in infrastructure management. Armed with the knowledge of its core concepts and essential commands, you're poised to navigate the complexities of modern infrastructure with confidence. Stay tuned for more in-depth guides and advanced tips as you embark on your Terraform journey.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.