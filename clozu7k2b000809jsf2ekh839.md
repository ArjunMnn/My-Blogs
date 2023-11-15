---
title: "Day 22: Getting Started with Jenkins"
datePublished: Wed Nov 15 2023 14:07:59 GMT+0000 (Coordinated Universal Time)
cuid: clozu7k2b000809jsf2ekh839
slug: day-22-getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700056239084/eef145a8-eded-42c9-8441-b1dd1ce4cfcb.png
tags: software-development, automation, devops, jenkins, ci-cd

---

Greetings, fellow tech enthusiasts! Today, let's embark on a journey through the magical realm of Jenkins, where automation dreams come true, and coding adventures unfold. 🌟

## What in the World is Jenkins? 🤔🏰

Imagine you're a wizard with a magical spellbook, making life easier one incantation at a time. Now, substitute that spellbook with Jenkins, and voila! You've entered the kingdom of continuous integration and automation. Jenkins is your trusty sidekick in the quest for efficiency, automating tasks that make mere mortals weep.

In the land of Jenkins, everything revolves around pipelines – not the kind you find in plumbing, mind you. Jenkins pipelines are a series of steps that transform your code from a fledgling apprentice into a grand sorcerer, ready to conquer the software realm.

But hold on to your wizard hats because Jenkins isn't just for the Gandalfs of the programming world. Whether you're a seasoned code mage or a curious newcomer, Jenkins welcomes you with open arms (or should we say open source?). 🤗

## Understanding CI/CD and the Magic of Jenkins

Before we dive into the enchanting world of Jenkins, let's unravel the mysteries of CI/CD. CI (Continuous Integration) and CD (Continuous Delivery/Deployment) are the magical spells that streamline the software development process. CI ensures that your code is regularly integrated, while CD takes it a step further by automating the delivery or deployment of that code. Picture it as a conveyor belt of wizardry, turning your code into real-world enchantments seamlessly. ✨🔗

### Pipelines: The Magical Conduits of Jenkins

At the heart of Jenkins lies the concept of pipelines – the invisible threads that weave automation into your code's journey. Pipelines are a series of steps that transform your code from a mere apprentice into a grand sorcerer. Here, we'll briefly introduce you to the main types of pipelines:

1. **Declarative Pipelines:** Think of these as the friendly guides, providing a simplified syntax for straightforward tasks. Ideal for those who prefer a more straightforward approach. 📜🧙‍♂️
    
2. **Scripted Pipelines:** For the bold adventurers who seek flexibility, scripted pipelines allow you to script every nuance of your automation saga. A realm for those who wish to wield the coding wand freely. 🚀💻
    

## Freestyle Fun: Creating a Pipeline to Say "Hello World" 🌍🚀

Now that you've grasped the essence of CI/CD and the magic of pipelines, let's dip our toes into the magical waters of Jenkins with a simple yet charming task – creating a freestyle pipeline to print "Hello World."

1. **Open Sesame – Using the Jenkins Docker Container:** Instead of the manual installation wizard, consider the swift alternative of using the Jenkins Docker container. Run the following command, and behold, Jenkins is at your service:
    
    ```dockerfile
    docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
    ```
    
    This conjures Jenkins into existence, ready to work its magic. 🌐🐳
    
2. **Meet the Court Jester – Create a Freestyle Project:** Once inside your Jenkins kingdom, navigate to the dashboard and click on "New Item." Give your project a quirky name – maybe "Project Enchant-o-Matic" – and choose the "Freestyle Project" option. 🏰🎨
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700056899230/5b0d1d56-a681-4135-9e2d-f655dadbcdae.png align="center")
    
3. **Conjure the Magic Words – Adding a Build Step:** In the project configuration, look for the "Build Steps" section and add a build step. Here, you'll unleash the incantation that makes your code shout "Hello World" to the world. You can use a simple shell command like `echo "Hello World"`. 🧙‍♂️🗣️
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700057027684/b2f0d1f7-c8aa-4f01-bd31-49b972fe170c.png align="center")
    
4. **Sprinkle Some Jenkins Magic Dust – Save and Build:** Save your project configuration, and with a wave of your virtual wand, initiate a build. Watch in awe as Jenkins works its magic, running your commands and creating a world where every line of code is a pixel in the grand tapestry of automation. 🎉✨
    
5. **Behold – The Grand Finale:** Once the build is complete, navigate to the project page and witness the glory of your "Hello World" masterpiece. Congratulations, you've just created your first Jenkins freestyle pipeline! 🎉🚀
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700057128495/f989a02d-044e-414f-a428-ce746de093a9.png align="center")
    

## Your Jenkins Adventure Awaits! 🌈🚀

And there you have it, brave adventurers – a whimsical introduction to the world of CI/CD, pipelines, and a glimpse into the vast and mystical world of Jenkins. As you continue your journey, remember that Jenkins is more than a tool; it's a companion, a guide, and a powerful ally in the ever-evolving landscape of automation. So, delve into the depths of Jenkins, explore its nooks and crannies, and may your pipelines be as robust as the spells in a wizard's spellbook. Happy automating! 🧙‍♂️✨

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)