---
title: "Day 59: Ansible Project"
datePublished: Mon Jan 01 2024 07:46:15 GMT+0000 (Coordinated Universal Time)
cuid: clqum9oj4000408l32nij75eq
slug: day-59-ansible-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704095101674/a3682592-3949-4f9d-b038-c23415bc1cf1.png
tags: software-development, aws, automation, devops, 90daysofdevops

---

## Introduction

In this tutorial, we'll walk through the process of creating an Ansible playbook to install Nginx and deploy a custom webpage on multiple Ubuntu servers. This automation simplifies the deployment process, ensuring consistency across your infrastructure. We assume that you have already set up an Ansible master and two Ubuntu hosts on EC2 instances.

## Prerequisites

1. Ansible master and two Ubuntu hosts set up on EC2 instances.
    
2. Process to set up ansible is explained in this [blog post.](https://arjunmenon.hashnode.dev/day-55-56-configuration-management-with-ansible)
    
3. All the code used in this tutorial is available in this [github repository](https://github.com/ArjunMnn/ansible-deploy-webpage).
    

## Ansible Playbook Overview

```yaml
---
- name: Install Nginx and deploy a custom webpage
  hosts: your_ubuntu_servers  # Replace with your target server(s) or inventory group
  become: true  # Run tasks with elevated privileges

  tasks:
    - name: Update package cache
      apt:
        update_cache: yes

    - name: Install Nginx
      package:
        name: nginx
        state: present

    - name: Start Nginx service
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Copy custom webpage files
      copy:
        src: /path/to/your_webpage_files/
        dest: /var/www/html/
```

## Explanation

1. **Update package cache:**
    
    * Ansible task using the `apt` module to update the package cache on the target servers.
        
2. **Install Nginx:**
    
    * Ansible task utilizing the `package` module to install Nginx on the target servers.
        
3. **Start Nginx service:**
    
    * Ansible task with the `service` module to start the Nginx service on the target servers and enable it to start on boot.
        
4. **Copy custom webpage files:**
    
    * Ansible task using the `copy` module to copy the custom webpage files from your specified source directory to the destination directory on the target servers.
        

Running the Playbook: Execute the following command to run the playbook:

```bash
ansible-playbook -i /etc/ansible/hosts deploy_webpage.yml
```

## Verification

After the playbook execution is complete, visit the public IP of any host server in your web browser to verify if the webpage has been successfully deployed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704094679067/2166eb8a-33cc-4ffa-821b-9bc1715712b0.png align="center")

## Conclusion

Automating the deployment of web services with Ansible simplifies the management and ensures consistency across multiple servers. This tutorial provides a clear and concise guide to deploying Nginx and a custom webpage using Ansible playbooks.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.