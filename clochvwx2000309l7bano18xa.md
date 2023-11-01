---
title: "Day 8: Basics of Git & Github for DevOps Engineers"
datePublished: Mon Oct 30 2023 06:04:18 GMT+0000 (Coordinated Universal Time)
cuid: clochvwx2000309l7bano18xa
slug: day-8-basics-of-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698591975056/d671a550-a66a-4539-9867-e75d96982878.png
tags: software-development, linux, github, git, devops

---

### Introduction

In the fast-paced world of DevOps, efficient collaboration, version control, and automated workflows are crucial. Git and GitHub play pivotal roles in achieving these goals, enabling teams to work seamlessly on projects of any size. This article will introduce you to the basics of Git and GitHub, providing a foundation for DevOps engineers to streamline their development processes.

### Understanding Version Control

Version control is the practice of tracking and managing changes to code or any set of files over time. It allows multiple people to collaborate on a project simultaneously without overwriting each other's work. Git is one of the most popular version control systems used in the software industry.

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1. A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check-in" the updated files. Examples of CVCS include Subversion and Perforce.
    
2. A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.
    

### What are Git & GitHub?

Git is a distributed version control system that enables developers to track changes, revert to previous stages, work on different branches, and collaborate efficiently. It was created by Linus Torvalds, the founder of Linux, to facilitate collaborative software development.

GitHub is a web-based platform that provides Git repository hosting, collaborative tools, and features like pull requests and code reviews. It enhances the Git experience by adding a graphical interface, issue tracking, and extensive community features.

## Hands-On Practice: Using Git and GitHub

To solidify your understanding of Git and GitHub, let's walk through a practical example. We'll cover the steps to create a new repository on GitHub, clone it to your local machine, make changes, and push them back to the repository.

### Step 1: Create a New Repository on GitHub

1. Go to [GitHub](https://github.com) and log in to your account (or create one if you haven't already).
    
2. Click on the '+' sign in the top-right corner and select "New repository".
    
3. Give your repository a name, choose visibility (public or private), and add a brief description if needed.
    
4. Optionally, choose to initialize the repository with a README file, a .gitignore file, or a license.
    
5. Click "Create repository".
    

### Step 2: Clone the Repository to Your Local Machine

Now that you have a repository on GitHub, you'll want to bring it to your local environment.

1. Copy the URL of your newly created repository from the GitHub page.
    
2. Open a terminal or command prompt on your local machine.
    
3. Use the `git clone <repository_url>` command, replacing `<repository_url>` with the URL you copied.
    

```plaintext
git clone <repository_url>
```

### Step 3: Make Changes and Commit Them

1. Navigate to the directory where you cloned the repository.
    
2. Create a new file or make changes to an existing one.
    
3. Use the following Git commands to commit your changes:
    

```plaintext
git add .
git commit -m "Added/Modified file"
```

### Step 4: Push the Changes to GitHub

Once you've committed your changes locally, it's time to push them back to the GitHub repository.

```plaintext
git push origin main
```

This command pushes the changes from your local `main` branch to the remote repository on GitHub.

### Step 5: Verify Changes on GitHub

1. Visit your repository on GitHub in your web browser.
    
2. You should now see the file you added or modified.
    

Congratulations! You've successfully created a new repository on GitHub, cloned it to your local machine, made changes, and pushed them back to GitHub. This hands-on exercise illustrates the power and efficiency of using Git and GitHub for version control and collaborative development.

## Conclusion

Git and GitHub are essential tools for DevOps engineers looking to streamline their development processes. By understanding the basics of version control, Git commands, and collaborative workflows, you'll be well-equipped to work effectively in a team and contribute to projects with confidence. Keep exploring and experimenting with Git and GitHub to discover even more powerful features and techniques!