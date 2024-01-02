---
title: "Day 62: Docker Provider in Terraform"
datePublished: Tue Jan 02 2024 15:11:11 GMT+0000 (Coordinated Universal Time)
cuid: clqwhlqgq000808jxggnx7p4a
slug: day-62-docker-provider-in-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704208368031/92bcd9ed-3fea-4d5b-9973-36d6311243b1.png
tags: cloud, docker, devops, terraform, 90daysofdevops

---

## Introduction

Modern infrastructure management involves the use of Infrastructure as Code (IaC) tools, providing a streamlined and automated approach to deploying and managing resources. Terraform, one such tool, enables users to define and provision infrastructure using a declarative configuration language. In this guide, we'll walk through the process of using Terraform to pull an NGINX Docker image and run a container, showcasing how Terraform simplifies the deployment of Dockerized applications.

## Task-01: Create a Terraform Script with Blocks and Resources

### 1.1. Install Terraform

Begin by ensuring that Terraform is installed on your machine. You can download the latest version from the official Terraform website.

### 1.2. Create a Directory

Set up a new directory for your Terraform project.

```bash
mkdir nginx-terraform
cd nginx-terraform
```

### 1.3. Create Terraform Script

Create a new file named [`main.tf`](http://main.tf) within the directory and add the following content:

```bash
# main.tf

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.21.0"
    }
  }
}

provider "docker" {}
```

This script sets up the Terraform configuration with the necessary Docker provider.

## Task-02: Create Resource Blocks for NGINX Docker Image and Container

### 2.1. NGINX Docker Image Resource Block

Add the following code to [`main.tf`](http://main.tf) to define the Docker image resource block:

```bash
# main.tf

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.21.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}
```

This resource block specifies the NGINX Docker image with the latest tag.

### 2.2. NGINX Docker Container Resource Block

Now, add the resource block for running the NGINX Docker container:

```bash
# main.tf

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 2.21.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "tutorial"

  ports {
    internal = 80
    external = 80
  }
}
```

This resource block defines a Docker container based on the NGINX image, named "tutorial," with port mapping from internal (container) port 80 to external (host) port 80.

## Execution

### 3.1. Initialize Terraform

Run the following command to initialize Terraform within your project directory:

```bash
terraform init
```

### 3.2. Apply Changes

Apply the changes to create the NGINX Docker image and container:

```bash
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704208173990/dbb98f18-2a90-4288-8af1-b79e89ed4e87.png align="center")

Terraform will prompt for confirmation; type `yes` and press Enter.

### 3.3. Verify

Verify that the NGINX Docker container is running by accessing it through a web browser or using the following command:

```bash
docker ps
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704208146481/2f9952e0-ef82-4c00-8443-4e71b4bb4bc6.png align="center")

You should see a running container named "tutorial" with NGINX.

## Conclusion

Congratulations! You have successfully created a Terraform script to pull the NGINX Docker image and run a container. This automation simplifies the deployment and management of Dockerized applications, showcasing the power and flexibility of Terraform.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.