---
title: "Deploying a Django To-do App Using Jenkins Freestyle Project"
datePublished: Fri Nov 17 2023 16:45:55 GMT+0000 (Coordinated Universal Time)
cuid: clp2uqdio000b08ju0x755woc
slug: deploying-a-django-to-do-app-using-jenkins-freestyle-project
canonical: https://arjunmenon.hashnode.dev/day-23-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700234907919/7970ffe9-604c-4281-bbba-dd6b895fc584.png
tags: cloud, docker, aws, devops, jenkins

---

In the thrilling realm of DevOps, automation is the hero we all need to streamline our development and deployment adventures. Today, we embark on a quest to automate the deployment of a Docker container, using the epic Django-based Todo application as our quest item, with Jenkins Freestyle Project as our trusty sidekick. 🌐🐍🕹️

# **Prerequisites**🛠️

1. Docker installed on your machine.
    
2. An AWS EC2 instance configured with Docker and your Django Todo application (as outlined in [this project](https://arjunmenon.hashnode.dev/dockerizing-and-deploying-a-django-to-do-app-on-aws)).
    

# **Project Overview**📝

In our previous escapade, we manually set up and deployed a Django Todo application within a Docker container on an AWS EC2 instance.

We will now automate this process using Jenkins Freestyle Project. 🔄

**Step 1: Create a Jenkins Agent for Your App** 🕵️‍♂️

1. Open Jenkins and navigate to "Manage Jenkins" &gt; "Manage Nodes and Clouds."
    
2. Click "New Node" to create a new agent. Provide a name and configure necessary settings.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700239206386/7530e47a-4cd5-40cf-bee6-7249cb802008.png align="center")

**Step 2: Configure a Freestyle Project** ⚙️

1. Click on "New Item" on the Jenkins dashboard.
    
2. Enter a project name and choose "Freestyle project."
    
3. Under the "General" section, check "Restrict where this project can be run" and select your created agent.
    

**Step 3: Add Build Steps** 🚧

1. In the project configuration, navigate to the "Build" section.
    
2. Click on "Add build step" and choose "Execute shell" (for Unix-based systems) or "Execute Windows batch command" (for Windows).
    
3. Enter the following commands:
    
    * `docker build -t todo-app .` to forge your Docker image.
        
    * `docker run -d -p 8001:8001 todo-app` to summon your Docker container.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700239257280/002ebf91-d2ff-4021-bf21-12538646a3d0.png align="center")

**Step 4: Save and Build** 💾

1. Save your project configuration.
    
2. Trigger a build by clicking "Build Now" on the project dashboard.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700239272483/cd21d439-138f-458e-b7a8-8e760443c589.png align="center")

Jenkins, our loyal companion, will now execute the specified build steps, automating the creation of your Docker image and the deployment of your Todo application.

**Step 5: Manual Browser Testing** 🌐👩‍💻

1. Open your preferred web browser.
    
2. Navigate to [http://localhost:8080](http://localhost:8080) to access your Todo App manually.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700239281251/28441d05-23a3-42eb-b2e2-766fd78fee2c.jpeg align="center")

# **Conclusion**🎉

In this tutorial, we automated the deployment of a Docker container for our Django Todo application using Jenkins Freestyle Project. This streamlined approach enhances efficiency and ensures consistency in your deployment process. Remember, this automation is built upon the manual setup explained in Project 1.

Feel the power of automation, adapt this tutorial to fit your specific project needs, and share your automated Docker deployment success with Jenkins! 🤖✨