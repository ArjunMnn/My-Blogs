---
title: "Day 26: Jenkins Declarative Pipeline: An Overview"
datePublished: Sun Nov 19 2023 14:18:42 GMT+0000 (Coordinated Universal Time)
cuid: clp5kcqx100020al7g5lp8gkb
slug: day-26-jenkins-declarative-pipeline-an-overview
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700403452616/b48cc44d-72ab-49d4-ad53-ce1ceab5e905.png
tags: software-development, devops, software-engineering, jenkins, ci-cd

---

Jenkins, an open-source automation server, has become a pivotal tool in the world of continuous integration and continuous delivery (CI/CD). One of the powerful features Jenkins offers is the ability to define and build pipelines. In this blog post, we'll delve into Jenkins Declarative Pipeline, exploring what pipelines are and providing a detailed step-by-step solution for a specific task.

## Understanding Jenkins Pipelines

In Jenkins, a pipeline is a set of automated processes that allow you to model, orchestrate, and visualize the entire process of delivering software. It breaks down the software delivery process into stages, making it easier to understand, manage, and troubleshoot. 🔄

Pipelines can be written in two ways: Scripted Pipeline and Declarative Pipeline. In this post, we'll focus on the Declarative Pipeline, a more structured and concise way of defining pipelines. 📜

### Declarative Pipeline Syntax

The Declarative Pipeline syntax is designed to make writing and reading pipelines more accessible. It provides a set structure and predefined syntax elements for defining stages, steps, and other aspects of the build process.

Here's a basic example of a Declarative Pipeline:

```dockerfile
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build your code here
            }
        }
        stage('Test') {
            steps {
                // Run tests here
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application
            }
        }
    }
}
```

In this example:

* `agent`: Specifies where the pipeline will run.
    
* `stages`: Represents different phases of the build process.
    
* `steps`: Contains the specific actions to be performed within each stage.
    

## Task-01: Creating a Declarative Pipeline

Now, let's tackle the specific task outlined:

**Step 1: Create a New Job 🏗️**

1. Open your Jenkins instance and click on "New Item."
    
2. Enter a name for your job (e.g., "HelloWorldPipeline") and choose "Pipeline" as the type.
    
3. Click on "OK" to create the job.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700402929246/91c2e432-5e33-4889-8e4b-51bf0ed1ffa5.png align="center")

**Step 2: Follow the Official Jenkins Hello World Example 🌐**

1. In your pipeline job configuration, scroll down to the "Pipeline" section.
    
2. Choose "Pipeline script" in the Definition dropdown.
    
3. Save the configuration.
    

**Step 3: Complete the Example using Declarative Pipeline 🛠️**

Now, let's modify the pipeline script to use Declarative syntax.

```dockerfile
  pipeline {
      agent any
      stages {
          stage('Build') {
              steps {
                  echo 'Hello World'
              }
          }
      }
  }
```

**Step 4: Save and Run the Pipeline 💾**

1. Save the pipeline script.
    
2. Trigger a build manually or wait for any configured triggers.
    
3. Observe the pipeline progress in the Jenkins dashboard.
    

**Step 5: Check the Full Stage View for Execution Time**

1. Once the pipeline execution starts, we can navigate to the "Full Stage View" to see the different stages of our pipeline and the time it takes for each stage to complete.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700403205519/26c42f6e-9d62-47a2-bb44-758537e855ec.png align="center")

**Step 6: Verify Hello World Using Console Output**

1. After the pipeline has been completed, we can check the "Console Output" to see the detailed logs of each step's execution.
    
2. If everything went as expected, we should see a "Success" status in the console output, indicating that the "Hello World" pipeline was executed successfully.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700403252024/f453ed6b-1d31-4ea5-9131-fba38989cf16.png align="center")

# Conclusion

Jenkins Declarative Pipelines provide a clean and concise way to define and manage your CI/CD processes. By following the steps outlined above, you can create a basic Declarative Pipeline and gain valuable insights into the power of Jenkins automation. Happy coding! 🚀✨