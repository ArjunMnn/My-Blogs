---
title: "Day 7: Understanding package managers and systemctl"
datePublished: Fri Oct 27 2023 14:25:37 GMT+0000 (Coordinated Universal Time)
cuid: clo8ph1p0000309mk1ly5cmk4
slug: day-7-understanding-package-managers-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698416663809/1742fe32-769e-4830-898b-6d267cab0a85.png
tags: linux, devops, package-manager, systemctl, 90daysofdevops

---

### **Introduction**

In the world of DevOps, smoothly handling software installations and dependencies is a game-changer. Linux package managers step up as indispensable allies, making the whole process a breeze. They automate the tasks of installing, configuring, and removing software packages, ensuring a hassle-free experience.

In this blog, we'll dive into the world of package managers, exploring what they are, the different types of packages they handle, and even show you how to install Docker and Jenkins using package managers on both Ubuntu and CentOS. But that's not all! We'll also demystify systemctl and systemd, essential tools for managing services and checking Docker's status. So, let's get started!

### **What is a Package Manager in Linux?**

A package manager is like a helpful wizard for your computer. It makes handling software on Linux super easy. It can install, update, and remove software without any fuss. Plus, it's really good at making sure all the necessary parts are in place.

It also knows where to find all the software, which it gets from special storage places called repositories. When you want to install something, it goes and gets it for you from these repositories.

So, thanks to the package manager, managing software on Linux becomes a walk in the park!

### **What is a Package?**

In the world of Linux, think of a package as a special gift box. Inside, you'll find all the important stuff like files, details, and instructions needed to set up a specific computer program.

These packages have names like .deb for Ubuntu and .rpm for CentOS. They're like secret codes that tell the computer how to handle them.

Now, let's talk about some cool package managers! They're like superheroes for managing software.

* APT for Debian and Ubuntu: It's super speedy and loved by millions for being easy to use.
    
* YUM for CentOS and Red Hat: This one is reliable and makes managing packages a breeze for system experts.
    
* DNF for modern Fedora systems: It's like the fancy new version of YUM, offering faster performance and smart problem-solving.
    

Now that you know this, let's jump into the fun part of our blog! 🛠️💻 Just remember to pick the right package manager for your Linux system, and you'll have a blast exploring all sorts of software!

### **Installing Docker and Jenkins Using Package Managers**

**Installing Docker on Ubuntu: To install Docker on Ubuntu**

Open your terminal. Execute the following commands:

```plaintext
sudo apt update
sudo apt install docker
```

**Installing Docker on CentOS: To install Docker on CentOS**

Open your terminal. Execute the following commands:

```plaintext
sudo yum update
sudo yum install docker
```

### **Installing Jenkins on Ubuntu and CentOS**

Both Ubuntu and CentOS use Java to run Jenkins, so we need to install the Java Development Kit (JDK) first.

**For Ubuntu:** To install Jenkins on Ubuntu, execute the following steps:

Install the Java Development Kit (JDK):

```plaintext
sudo apt update
sudo apt install default-jdk
```

Proceed to install Jenkins:

```plaintext
sudo apt install jenkins
```

**For CentOS:** To install Jenkins on CentOS, execute the following steps:

Install the Java Development Kit (JDK):

```plaintext
sudo yum update
sudo yum install java-devel
```

Proceed to install Jenkins:

```plaintext
sudo yum install jenkins
```

### **Difference between systemctl and service**

Both systemctl and service are commands used in Linux-based operating systems to manage system services.

However, **systemctl** is a more modern and advanced command, while **service** is a legacy command used in older Linux distributions.

Let's take a closer look at the differences between systemctl and service, along with their respective usage examples.

**systemctl**: It is the primary service management tool in systems that use the systemd init system. **systemd** is a system and service manager that has replaced the traditional SysV init system in many modern Linux distributions. **systemctl** allows you to control the system and service state, enable or disable services to start at boot and query the status of services.

**To check the status of the Docker service:**

```plaintext
systemctl status docker
```

**To start the Docker service:**

```plaintext
sudo systemctl start docker
```

**To stop the Docker service:**

```plaintext
sudo systemctl stop docker
```

**To enable the Docker service to start at boot:**

```plaintext
sudo systemctl enable docker
```

**To disable the Docker service from starting at boot:**

```plaintext
sudo systemctl disable docker
```

**service**: `service` is a command used to interact with SysV init scripts, the traditional initialization system used in older Linux distributions. While service can still be found in many systems, it is considered a legacy command, and newer systems that use systemd tend to favor systemctl.

**To check the status of the Docker service using the service:**

```plaintext
service docker status
```

**To start the Docker service using the service:**

```plaintext
sudo service docker start
```

**To stop the Docker service using service:**

```plaintext
sudo service docker stop
```

**To restart the Docker service using the service:**

```plaintext
sudo service docker restart
```

### **Conclusion**

In this blog, we've delved into the significance of package managers in Linux, understanding various types of packages, and mastering the installation of Docker and Jenkins through package managers on both Ubuntu and CentOS.

Furthermore, we've gained insight into systemctl and systemd, powerful tools for service management and monitoring Docker's status.

By harnessing the power of package managers, DevOps experts can seamlessly handle software installations, allowing them to concentrate on creating sturdy and dependable applications.