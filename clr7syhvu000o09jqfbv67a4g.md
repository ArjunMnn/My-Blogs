---
title: "Day 71: Terraform Interview Questions"
datePublished: Wed Jan 10 2024 13:14:31 GMT+0000 (Coordinated Universal Time)
cuid: clr7syhvu000o09jqfbv67a4g
slug: day-71-terraform-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704892398068/d7d92bca-8cc0-4b78-ad71-6907ea2bc4c2.png
tags: cloud, aws, devops, terraform, 90daysofdevops

---

## Question 1:

### What is Terraform and how is it different from other IaaC tools?

**Answer:** Terraform is an open-source Infrastructure as Code (IaaC) tool developed by HashiCorp. It allows users to define and provision infrastructure using a declarative configuration language. Unlike other IaaC tools, Terraform is cloud-agnostic, supporting various cloud providers, on-premises environments, and services. Its key differentiator lies in its ability to create a unified workflow for managing multi-cloud infrastructure.

## Question 2:

### How do you call a [main.tf](http://main.tf) module?

**Answer:** The [`main.tf`](http://main.tf) module in Terraform is automatically loaded without explicit invocation. Terraform expects to find and load a file named [`main.tf`](http://main.tf) in the working directory, making it the default entry point for configuration.

## Question 3:

### What exactly is Sentinel? Can you provide a few examples where we can use Sentinel policies?

**Answer:** Sentinel is a policy as code framework embedded in Terraform Enterprise. It helps enforce and automate governance policies in the deployment pipeline. Examples of Sentinel policies include ensuring specific resource tag conventions, restricting the use of certain cloud resources, and enforcing naming conventions.

## Question 4:

### You have a Terraform configuration file that defines an infrastructure deployment. However, there are multiple instances of the same resource that need to be created. How would you modify the configuration file to achieve this?

**Answer:** To create multiple instances of the same resource, you can use a `count` parameter within the resource block. This parameter specifies the number of instances to create. For example:

```bash
resource "example_resource" {
  count = 3
  # other configurations...
}
```

## Question 5:

### You want to know from which paths Terraform is loading providers referenced in your Terraform configuration (\*.tf files). You need to enable debug messages to find this out. Which of the following would achieve this?

**Answer:** A. Set the environment variable `TF_LOG=TRACE` enables debug messages and helps identify the paths from which Terraform is loading providers.

## Question 6:

### Below command will destroy everything that is being created in the infrastructure. Tell us how would you save any particular resource while destroying the complete infrastructure.

**Answer:** While running `terraform destroy`, you can target a specific resource for preservation using the `-target` flag. For example:

```bash
terraform destroy -target=aws_instance.example
```

## Question 7:

### Which module is used to store .tfstate file in S3?

**Answer:** The `terraform_backend_s3` module is used to store the `.tfstate` file in an S3 bucket.

## Question 8:

### How do you manage sensitive data in Terraform, such as API keys or passwords?

**Answer:** Sensitive data like API keys or passwords should be managed using Terraform's sensitive input variables. These values are marked as sensitive, preventing them from being displayed in the console output or stored in the state file.

## Question 9:

### You are working on a Terraform project that needs to provision an S3 bucket, and a user with read and write access to the bucket. What resources would you use to accomplish this, and how would you configure them?

**Answer:** To achieve this, you would use the `aws_s3_bucket` resource to create the S3 bucket and the `aws_iam_user` and `aws_iam_user_policy` resources to create a user with the necessary permissions. The policies should be attached to the user to grant read and write access to the S3 bucket.

## Question 10:

### Who maintains Terraform providers?

**Answer:** Terraform providers are maintained by the respective cloud service providers or third-party contributors. HashiCorp, the creator of Terraform, maintains some core providers, while others are developed and maintained by the community or specific organizations.

## Question 11:

### How can we export data from one module to another?

**Answer:** Data can be exported from one module to another using Terraform outputs. In the exporting module, define the data as an output variable, and in the importing module, reference the exported data using the `module` syntax.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.