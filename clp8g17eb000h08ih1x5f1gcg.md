---
title: "Day 28: Jenkins Agents"
datePublished: Tue Nov 21 2023 14:41:03 GMT+0000 (Coordinated Universal Time)
cuid: clp8g17eb000h08ih1x5f1gcg
slug: day-28-jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700577623312/275e8618-5c9c-4483-9a8c-293e553d3cba.png
tags: software-development, docker, devops, jenkins, ci-cd

---

Jenkins, a powerful automation server, offers a distributed architecture to handle complex CI/CD workflows efficiently. This capability is realized through the use of Jenkins agents, also known as nodes. Agents are responsible for executing tasks delegated by the Jenkins master, allowing for parallel execution and workload distribution. In this section, let's delve into the concept of Jenkins agents and how they contribute to enhancing the scalability and distribution of your CI/CD pipelines.

## What are Jenkins Agents?

Jenkins agents are independent machines or processes that work in conjunction with the Jenkins master to execute tasks in a distributed manner. The Jenkins master delegates jobs to agents, and each agent runs its assigned tasks independently. This distributed approach is particularly valuable for managing large-scale projects with diverse requirements.

### Key Features of Jenkins Agents:

1. **Parallel Execution:** Agents enable parallel execution of tasks, significantly reducing the overall build and deployment time.
    
2. **Workload Distribution:** Agents distribute the workload across multiple machines, preventing bottlenecks and optimizing resource utilization.
    
3. **Platform Diversity:** Agents can run on different operating systems and environments, allowing Jenkins to accommodate a variety of project requirements.
    
4. **Scalability:** Adding more agents to your Jenkins setup is a straightforward way to scale your CI/CD pipelines and accommodate growing workloads.
    
5. **Isolation:** Agents operate independently, providing a level of isolation for tasks. Failures on one agent do not affect others.
    

## Types of Jenkins Agents:

1. **Permanent Agents:** These agents are configured to be always online, waiting for tasks from the master. Permanent agents are suitable for stable and consistent workloads.
    
2. **Cloud Agents:** Cloud agents are created dynamically based on demand. Jenkins can spawn agents in cloud environments (such as AWS, Azure, or Google Cloud) and terminate them when the workload decreases.
    
3. **Docker Agents:** Jenkins can utilize Docker containers as agents, providing a lightweight and reproducible environment for executing tasks.
    

## Setting Up Jenkins Master and Agent

### Step 1: Install Jenkins

If you haven't installed Jenkins yet, follow the official documentation for your operating system: [Jenkins Installation](https://www.jenkins.io/doc/book/installing/)

### Step 2: Launch AWS EC2 Instances

Launch EC2 instances with the names 'Jenkins-Master' & 'Jenkins-Agent'. Install Jenkins in the master server.

### Step 3: Connect to Jenkins Master Instance

1. Copy the public IP address of your Jenkins master instance.
    
2. Open a terminal and navigate to the directory where your Jenkins master private key file is located.
    
3. Use the following command to connect to the master instance:
    
4. ```dockerfile
    ssh -i your-master-key-file.pem ec2-user@your-master-instance-ip
    ```
    

### Step 4: Set Up Jenkins on Master Instance

1. Once connected to the master instance, install Java and Jenkins by following the commands below:
    
    ```dockerfile
    sudo apt update
    sudo apt install fontconfig openjdk-17-jre
    sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
      https://pkg.jenkins.io/debian/jenkins.io-2023.key
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian binary/ | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update
    sudo apt-get install jenkins
    ```
    
2. Follow the on-screen instructions to complete the Jenkins setup.
    

### Step 5: Configure SSH for Master-Agent Communication

1. On the Jenkins master, generate an SSH key pair:
    
    ```dockerfile
    ssh-keygen
    ```
    
2. Copy the public key (`~/.ssh/id_`[`rsa.pub`](https://www.jenkins.io/doc/book/installing/)).
    
3. On the Jenkins agent, open the `authorized_keys` file and paste the public key.
    

### Step 6: Configure Jenkins Agent on Agent Instance

1. Once Jenkins is running on the master, navigate to "Manage Jenkins" &gt; "Manage Nodes and Clouds."
    
2. Click on "New Node" and enter a name for your agent.
    
3. Select "Permanent Agent" and click "OK."
    
4. Configure the following:
    
    * **Remote root directory:** Leave it as is or specify a custom directory.
        
    * **Labels:** Add any labels you want for this agent.
        
    * **Launch method:** Choose "Launch agent via Java Web Start."
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577086022/e52142a5-e139-4f49-ad17-abb2c597daec.png align="center")
    
5. Add credentials.
    
6. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577156133/ff4e29bb-9e65-4b34-9edf-3a1d2640e9cf.png align="center")
    
    In 'Key', give the private key you generated in the master server.
    
7. Click "Save" and then "Launch Agent" to start the connection.
    
8. Check the status of your new agent under "Manage Nodes and Clouds."
    

### Step 7: Use this agent to run your pipeline

1. We'll use a simple 'Hello-World' example. Use the below pipeline script.
    
    ```dockerfile
    pipeline {
        agent { label 'dev-server'}
        stages{
            stage('Build') {
                steps{
                    echo 'Hello World'
                }            
            }
        }
        
    }
    ```
    
2. Save and Run.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700577364216/8124c02b-bc58-4249-9e20-dfe73ec95ece.png align="center")
    

# Conclusion

Congratulations! You've successfully set up a Jenkins master and agent on separate AWS EC2 instances, creating a distributed CI/CD environment. This architecture allows you to efficiently scale your Jenkins pipelines, enhancing your overall development and deployment processes.

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)

Checkout my [GitHub](https://github.com/ArjunMnn) profile.