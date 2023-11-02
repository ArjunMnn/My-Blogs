---
title: "Day 10: Advanced Git & GitHub for DevOps Engineers"
datePublished: Thu Nov 02 2023 06:17:00 GMT+0000 (Coordinated Universal Time)
cuid: clogsnste000g09jo0x104vao
slug: day-10-advanced-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698905685463/f0a4d32a-4aeb-4a4f-a19e-d53d03ce84e1.png
tags: software-development, linux, github, git, devops

---

## Introduction

Git is a powerful version control system that plays a crucial role in the DevOps workflow. Understanding advanced Git concepts like branching, reverting, resetting, rebasing, and merging is essential for DevOps engineers to effectively manage code repositories. In this blog post, we will dive into these topics with detailed solutions to common tasks.

## Git Branching: Diverging Paths

One of the most powerful features of Git is its branching system. Branching allows multiple lines of development to coexist in parallel. Each branch represents a different version of the code, enabling teams to work on separate features or fixes simultaneously without interfering with each other's work.

**Creating a Branch**

To create a new branch, simply use the command `git branch branch_name`. This creates a new pointer to the same commit as the branch you're currently on.

**Switching Between Branches**

You can switch between branches using `git checkout branch_name`. This updates your working directory to reflect the selected branch's state.

## Git Revert and Reset: Correcting Mistakes

Git provides tools like `revert` and `reset` for undoing changes. They serve different purposes and should be used based on the specific requirements of your workflow.

**Git Revert**

`git revert` creates a new commit that undoes the changes made in a previous commit. This is a safe way to correct mistakes without altering the commit history.

**Git Reset**

`git reset` allows you to reset your branch to a specific commit, effectively erasing any commits made after it. This can be useful in situations where you want to rework or discard a series of commits.

## Git Rebase and Merge: Integrating Changes

Integrating changes from one branch into another is a crucial part of collaborative development. Two common methods for this are `rebase` and `merge`.

### Git Rebase

`git rebase` allows you to incorporate the changes from one branch onto another by moving, combining, or omitting commits. This creates a linear history, making it easier to follow the progression of the codebase.

### Git Merge

`git merge` combines the changes from one branch into another, creating a new commit that represents the integration. This maintains a more branching history, showing the distinct lines of development.

## Hands-On Practice

### Task 1: Adding a Text File and Making Commits

**Step 1: Create a New Branch and Add version01.txt**

Open your terminal and navigate to the Devops/Git directory. Then, execute the following commands:

```plaintext
cd Devops/Git/
git checkout -b dev
echo "This is first feature of our application" > version01.txt
```

**Step 2: Committing Changes in dev Branch**

```plaintext
git add version01.txt
git commit -m "Added new feature"
```

**Step 3: Pushing Changes to Remote Repository**

```plaintext
git push origin dev
```

**Step 4: Adding Additional Commits in dev Branch**

```plaintext
echo "This is the bug fix in development branch" >> version01.txt
git add version01.txt
git commit -m "Added feature2 in development branch"

echo "This is gadbad code" >> version01.txt
git add version01.txt
git commit -m "Added feature3 in development branch"

echo "This feature will gadbad everything from now." >> version01.txt
git add version01.txt
git commit -m "Added feature4 in development branch"
```

**Step 5: Restoring version01.txt to a Previous Version**

You can use either `git revert` or `git reset` to achieve this. Let's use `git reset` in this example.

```plaintext
git log
# Note down the commit hash of the version you want to restore to

git reset --hard <commit-hash>
git push -f origin dev
```

### Task 2: Branching, Merging, and Rebase

**Step 1: Creating Additional Branches**

```plaintext
git checkout -b feature1
# Make changes and commit

git checkout -b feature2
# Make changes and commit
```

**Step 2: Merging dev Branch into master**

```plaintext
git checkout master
git merge dev
git push origin master
```

**Step 3: Using Git Rebase**

```plaintext
git checkout feature1
git rebase dev
# Resolve any conflicts, if there are any

git checkout feature2
git rebase dev
# Resolve any conflicts, if there are any
```

## Conclusion

Understanding these Git commands empowers developers to efficiently manage their codebase. Branching enables parallel development, revert and reset correct mistakes, and rebase and merge to facilitate integration. By knowing when and how to use these tools, you can ensure a smooth and collaborative development process. Happy coding!

Let's connect on LinkedIn - [https://www.linkedin.com/in/arjunmenon-devops/](https://www.linkedin.com/in/arjunmenon-devops/)