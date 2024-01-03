---
title: "Day 63: Terraform Variables"
datePublished: Wed Jan 03 2024 13:53:42 GMT+0000 (Coordinated Universal Time)
cuid: clqxu9x86000008jv0sjrhlx0
slug: day-63-terraform-variables
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704289948914/64720920-5d33-49df-8ad1-65349edc2777.png
tags: cloud, software-development, devops, terraform, 90daysofdevops

---

## Introduction

Terraform, a powerful Infrastructure as Code (IaC) tool, allows you to define and provision infrastructure in a declarative manner. A key component of Terraform's flexibility is its support for variables. Variables enable you to make your infrastructure code adaptable, reusable, and easily configurable.

In this blog post, we'll delve into Terraform variables, exploring various data types such as Map, List, Set, and Object. We'll start by understanding the Map data type and then move on to practical examples that showcase the versatility of Terraform variables.

## Understanding Terraform Variables

In Terraform, variables act as parameters for your infrastructure code, providing a way to dynamically define values. Different data types allow you to structure your variables based on specific needs.

### Map: Mapping Values

Maps in Terraform are collections of key-value pairs, making them useful for variables with distinct names and associated values. In our exploration, we'll begin by focusing on the Map data type.

```bash
variable "file_contents" {
  type    = map
  default = {
    "statement1" = "this is cool"
    "statement2" = "this is cooler"
  }
}
```

## Task-01: Creating a Local File

Let's put our knowledge into practice by creating a local file using Terraform. We'll utilize the Map variable to dynamically set the content of the file.

```bash
resource "local_file" "devops" {
  filename = var.filename
  content  = var.file_contents["statement1"]
}

# Additional variable for filename
variable "filename" {
  type    = string
  default = "output.txt"
}
```

Now, the local file resource is configured with content from the Map variable.

## Task-02: List, Set, and Object Datatypes

Terraform supports various data types beyond Map. Let's explore List, Set, and Object in Terraform variables.

### List: Ordered Collections

```bash
variable "colors" {
  type    = list(string)
  default = ["red", "green", "blue"]
}
```

### Set: Unordered Collections

```bash
variable "unique_numbers" {
  type    = set(number)
  default = [1, 2, 3, 4, 5]
}
```

### Object: Complex Structures

```bash
variable "user" {
  type = object({
    name  = string
    age   = number
    email = string
  })

  default = {
    name  = "John Doe"
    age   = 30
    email = "john.doe@example.com"
  }
}
```

Experiment with these variable types to enhance the flexibility and scalability of your Terraform code.

## Conclusion

Understanding Terraform variables and their various data types is essential for building robust and adaptable infrastructure code. Whether you're managing simple key-value pairs or complex data structures, Terraform's flexibility empowers you to create dynamic and scalable infrastructure.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.