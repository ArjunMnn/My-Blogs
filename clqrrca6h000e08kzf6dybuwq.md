---
title: "Day 55 & 56: Configuration Management with Ansible"
datePublished: Sat Dec 30 2023 07:44:56 GMT+0000 (Coordinated Universal Time)
cuid: clqrrca6h000e08kzf6dybuwq
slug: day-55-56-configuration-management-with-ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703921778642/f1fd7402-05cc-4f55-bf65-587c4d1068e8.png
tags: cloud, aws, ansible, devops, 90daysofdevops

---

## Introduction

Ansible is a powerful open-source automation tool that simplifies IT infrastructure management and application deployment. In this tutorial, we will guide you through the process of setting up Ansible on a master EC2 instance and using it to ping two host instances. Additionally, we will cover some essential Ansible ad-hoc commands.

## Prerequisites

1. **EC2 Instances:**
    
    * Create three EC2 instances on Amazon AWS: one as the Ansible master and two as hosts.
        
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703921146388/11331802-9b67-4e6f-858a-2eaee6180efc.png align="center")
        
2. **SSH to Master Instance:**
    
    * Connect to the Ansible master instance using SSH.
        

```bash
ssh -i "your-key.pem" ubuntu@your-master-ip
```

## Installing Ansible

1. **Install Ansible:**
    
    * Add the Ansible repository and install Ansible.
        

```bash
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
```

1. **Verify Installation:**
    
    * Confirm that Ansible is installed successfully.
        

```bash
ansible --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703921167963/0affe71c-1b14-4301-8941-0982aad62425.png align="center")

## Setting Up Ansible Configuration

1. **Transfer PEM File:**
    
    * Copy the PEM file from your local machine to the master instance.
        

```bash
scp -i "your-key.pem" your-key.pem ubuntu@your-master-ip:/home/ubuntu/keys
```

1. **Edit Ansible Hosts File:**
    
    * Open the Ansible hosts file for editing.
        

```bash
sudo vim /etc/ansible/hosts
```

1. **Configure Hosts:**
    
    * Add the following lines to the hosts file to define the hosts in a group named 'servers.'
        

```bash
[servers]
host_1 ansible_host=your-host-1-ip
host_2 ansible_host=your-host-2-ip

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/keys/your-key.pem
ansible_python_interpreter=/usr/bin/python3
```

1. **Change PEM File Permissions:**
    
    * Restrict permissions on the PEM file.
        

```bash
chmod 400 your-key.pem
```

1. **Ping Hosts:**
    
    * Verify connectivity by pinging the hosts in the 'servers' group.
        

```bash
ansible -m ping servers
```

* The ping should be successful.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703921198489/4f2da9cd-711f-4da4-a0c0-93651964e60c.png align="center")

## Ansible Ad-hoc Commands

### Ping Multiple Servers

1. **Ad-hoc Ping Command:**
    
    * Use the following Ansible ad-hoc command to ping three servers from the inventory file.
        

```bash
ansible -m ping -i /etc/ansible/hosts host_1 host_2 another_host
```

### Check Uptime

1. **Ad-hoc Uptime Command:**
    
    * Check the uptime of the servers using the ad-hoc command.
        

```bash
ansible -m command -a "uptime" -i /etc/ansible/hosts servers
```

## Conclusion

Congratulations! You have successfully configured Ansible on a master EC2 instance and pinged two host instances. Additionally, you've learned how to execute Ansible ad-hoc commands to perform tasks on multiple servers. Ansible's simplicity and power make it an invaluable tool for automating infrastructure management tasks. Explore further to harness its full potential in your environment.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.