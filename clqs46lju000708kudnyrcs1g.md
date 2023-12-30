---
title: "Day 57 & 58: Ansible Playbooks"
datePublished: Sat Dec 30 2023 13:44:26 GMT+0000 (Coordinated Universal Time)
cuid: clqs46lju000708kudnyrcs1g
slug: day-57-58-ansible-playbooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703943807740/5806b47a-2688-4dd4-8dcf-cee48789e486.png
tags: cloud, software-development, automation, devops, 90daysofdevops

---

## Introduction

Ansible, an open-source automation tool, is widely used for configuration management, application deployment, and task automation. In this tutorial, we'll explore three common automation tasks using Ansible: creating a file on a different server, creating a new user, and installing Docker on a group of servers. Along the way, we'll also discuss best practices for writing Ansible playbooks.

## Prerequisites

Before diving into Ansible automation, ensure that you have Ansible installed on your control machine. You can follow the installation instructions on this [blog post](https://arjunmenon.hashnode.dev/day-55-56-configuration-management-with-ansible).

All the code used in this tutorial is available in [this repository](https://github.com/ArjunMnn/Ansible-playbooks).

## Task 1: Creating a File on a Different Server

### Ansible Playbook

```yaml
---
- name: Create a file on a different server
  hosts: all
  become: true
  tasks:
    - name: Ensure the file exists
      file:
        path: /home/ubuntu/file.txt
        state: touch
```

### Explanation

This playbook is designed to run on all servers specified in the inventory file. The `become: true` directive is used to execute tasks with elevated privileges. The single task, defined under `tasks`, utilizes the `file` module to ensure the existence of the specified file.

## Task 2: Creating a New User

### Ansible Playbook

```yaml
---
- name: Create a new user
  hosts: all
  become: true
  tasks:
    - name: Create a user with the name ansible-user
      user:
        name: ansible-user
```

### Explanation

This playbook targets all hosts (`all`) and utilizes the `user` module to create a new user named "ansible-user." The `become: true` directive is included to execute the task with elevated privileges.

## Task 3: Installing Docker on a Group of Servers

### Ansible Playbook

```bash
---
- name: Install Docker
  hosts: docker_servers
  become: true
  tasks:
    - name: Update apt cache
      apt:
        update_cache: yes
    - name: Install Docker
      apt:
        name: docker.io
        state: present
```

### Explanation

This playbook targets a group of servers (`docker_servers`) to install Docker. The tasks involve updating the APT cache and installing the [`docker.io`](http://docker.io) package using the `apt` module. As before, `become: true` is used to execute tasks with elevated privileges.

## Ansible Playbook Best Practices

1. **Descriptive Names**: Use meaningful names for your playbooks and tasks to enhance readability.
    
2. **Target Specific Hosts**: Clearly specify the target hosts using the `hosts` directive to avoid unintended changes.
    
3. **Privilege Escalation**: Use `become: true` judiciously for tasks requiring elevated privileges.
    
4. **Documentation**: Include comments and documentation within your playbooks to explain the purpose of each task.
    
5. **Modularity**: Break down playbooks into smaller, modular files for better organization and reuse.
    
6. **Idempotence**: Design tasks to be idempotent, ensuring that running them multiple times produces the same result.
    
7. **Variables**: Utilize variables to make playbooks flexible and easily adaptable to different environments.
    
8. **Error Handling**: Implement error handling and appropriate fail conditions for robust playbooks.
    
9. **Testing**: Test playbooks in a safe environment before applying them to production.
    
10. **Source Control**: Use version control systems like Git to manage and track changes in your Ansible code.
    

By following these best practices, you'll create maintainable, reliable, and efficient Ansible playbooks for automating your infrastructure.

## Conclusion

In this tutorial, we've explored the power of Ansible by creating playbooks for common automation tasks. Whether it's creating files, adding users, or installing software across multiple servers, Ansible provides a straightforward and declarative approach to configuration management.

Follow me on [**LinkedIn**](https://www.linkedin.com/in/arjunmenon-devops/).

Checkout my [**GitHub**](https://github.com/ArjunMnn) profile.