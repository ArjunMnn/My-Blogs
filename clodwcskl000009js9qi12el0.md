---
title: "Day 9: Deep Dive in Git & GitHub for DevOps Engineers"
datePublished: Tue Oct 31 2023 05:37:06 GMT+0000 (Coordinated Universal Time)
cuid: clodwcskl000009js9qi12el0
slug: day-9-deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698730264340/8e1b631f-cccf-43b3-bc0a-76b9a6bbbb52.png
tags: software-development, linux, github, git, devops

---

### Introduction

Git and GitHub are foundational tools for DevOps engineers. They play a crucial role in version control and collaboration, allowing teams to work efficiently and effectively. In this blog post, we'll take a comprehensive look at Git, GitHub, and how they are used in the DevOps workflow.

### What is Git and Why is it Important?

Git is a distributed version control system that allows developers to track changes in their codebase. It enables collaboration among multiple contributors, facilitates branching and merging, and ensures a reliable history of code changes. Git is essential for managing code in any software development project.

### Main Branch vs. Master Branch: Understanding the Difference

Historically, Git repositories commonly used the term "master" to refer to the default branch. In recent years, the industry has been moving towards using the term "main" instead. Both terms essentially serve the same purpose - they are the default branch where all changes are integrated. It's important to be aware of this terminology to stay in sync with best practices.

### Git vs. GitHub: Exploring the Differences

Git and GitHub are often used in conjunction, but they serve different purposes. Git is the version control system itself, while GitHub is a web-based platform that provides hosting for Git repositories. GitHub adds a layer of functionality for collaboration, such as issue tracking, pull requests, and more.

### Creating a New Repository on GitHub

**Task 1: Set your user name and email address**

Before we dive into creating a repository on GitHub, make sure you have configured your Git with the appropriate user name and email address. This information will be associated with your commits.

**Task 2: Creating the "Devops" Repository**

1. Log in to your GitHub account.
    
2. Click on the "+" icon in the top-right corner of the page and select "New repository".
    
3. Provide a name for your repository (e.g., "Devops") and optionally add a description.
    
4. Choose the visibility (public or private) and any other settings you prefer.
    
5. Click on "Create repository".
    

### Local vs. Remote Repository: Understanding the Difference and Connecting Them

A local repository is a copy of the Git repository that resides on your local machine. A remote repository, on the other hand, is hosted on a remote server (like GitHub). To connect your local repository to the remote one you've just created:

1. In your local terminal, navigate to the project directory: `cd path/to/Devops`.
    
2. Add the remote repository as a remote named "origin":
    
    ```plaintext
    git remote add origin https://github.com/yourusername/Devops.git
    ```
    
    Make sure to replace `yourusername` with your actual GitHub username.
    
3. Verify the remote has been added:
    
    ```plaintext
    git remote -v
    ```
    
    You should see the remote URL.
    
4. Push your local commits to the remote repository:
    
    ```plaintext
    git push -u origin main
    ```
    

### Adding Content to the Repository

Create a new file `Day-02.txt` inside the `Git` directory:

```plaintext
touch Git/Day-02.txt
```

Add some content to the file using a text editor of your choice.

### Pushing Your Local Commits

Once you've added content to your local repository, you can push it to the remote repository:

```plaintext
git add .
git commit -m "Added Day-02.txt"
git push origin main
```

This will upload your changes to the GitHub repository.

### Conclusion

Understanding Git and GitHub is crucial for any DevOps engineer. They form the backbone of version control and collaboration in modern software development. By following the tasks outlined in this blog, you'll have hands-on experience with creating repositories, connecting them, and pushing changes - skills that are fundamental in the DevOps world. Happy coding!

Let's connect on LinkedIn - [https://www.linkedin.com/in/arjunmenon-devops/](https://www.linkedin.com/in/arjunmenon-devops/)