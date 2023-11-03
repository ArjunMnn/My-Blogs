---
title: "Day 11: Advance Git & GitHub for DevOps Engineers: Part-2"
datePublished: Fri Nov 03 2023 06:21:32 GMT+0000 (Coordinated Universal Time)
cuid: cloi89hng00040ajx1g492yaw
slug: day-11-advance-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698992329218/e7bdfff7-987b-4882-b2e8-1c9b8cd08243.png
tags: software-development, linux, github, git, devops

---

## Introduction

Git and GitHub are indispensable tools for DevOps engineers, enabling them to manage code repositories efficiently and collaborate seamlessly. In this blog post, we'll delve into some advanced Git concepts that are particularly relevant for DevOps professionals: `git stash`, `cherry-pick`, and resolving conflicts. These techniques will help you streamline your workflow, resolve tricky situations, and maintain a clean codebase.

## Git Stash: Managing Temporary Changes

**Overview**

`git stash` is a powerful feature that allows you to save your current working directory and index, creating a clean slate to switch branches or work on a different task. This is especially handy when you need to switch contexts quickly without committing incomplete or experimental changes.

**Basic Usage**

To stash your changes, use the following command:

```plaintext
git stash save "your_message_here"
```

To apply the stashed changes later, use:

```plaintext
git stash pop
```

**Best Practices**

* Give descriptive messages when stashing changes for clarity.
    
* Use `git stash list` to view a list of stashes and manage them effectively.
    

## Cherry Pick: Selectively Applying Commits

**Overview**

`cherry pick` allows you to pick specific commits from one branch and apply them to another. This is useful when you want to apply a specific bug fix or feature to a different branch without merging the entire branch.

**Basic Usage**

```plaintext
git cherry-pick <commit-hash>
```

**Best Practices**

* Always test cherry-picked commits to ensure they integrate seamlessly with the target branch.
    
* Remember to commit the cherry-picked changes after they are applied.
    

## Resolving Conflicts: Navigating Merge Conflicts

**Overview**

Merge conflicts occur when Git is unable to automatically merge changes from different branches. As a DevOps engineer, it's crucial to know how to resolve these conflicts to maintain a healthy codebase.

**Basic Steps**

1. **Identify Conflicts**: Git will mark the conflicting sections in your files. Open the file(s) and locate the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
    
2. **Resolve Conflicts Manually**: Edit the files to remove the conflict markers and choose the desired changes.
    
3. **Add and Commit**: After resolving the conflicts, add the modified files and commit the changes.
    

**Best Practices**

* Use visual tools like GitKraken, SourceTree, or your IDE's built-in merge conflict resolution tools to simplify the process.
    
* Communicate with team members to ensure everyone is aware of and on board with conflict resolutions.
    

## Hands-On Practice

### Task-01: Branching, Stashing, and Applying Changes

**Step 1: Creating a New Branch and Making Changes**

```plaintext
# Create a new branch named 'new-feature'
git checkout -b new-feature

# Make necessary changes to your files
# For example, edit or add files in your working directory
```

**Step 2: Using Git Stash for Temporary Storage**

```plaintext
# Suppose you need to switch branches without committing changes
# Use git stash to temporarily save your changes
git stash
```

Now you can safely switch branches.

**Step 3: Switching Branches and Making Additional Changes**

```plaintext
# Switch to another branch (e.g., 'dev')
git checkout dev

# Make some changes and commit them
# For example, edit or add files in your working directory
git add .
git commit -m "Made changes in dev branch"
```

**Step 4: Bringing Stashed Changes Back**

```plaintext
# Return to your original branch ('new-feature')
git checkout new-feature

# Apply the stashed changes on top of your new commits
git stash pop
```

Now, your original changes are applied on top of the new commits made in the 'dev' branch.

# Task-02: Working with Commits and Branches

**Step 1: Adding New Features in Development Branch**

```plaintext
# Assuming you're in the 'development' branch
# Add new lines to version01.txt
echo "Line2>> After bug fixing, this is the new feature with minor alteration”" >> version01.txt
git add version01.txt
git commit -m "Added feature2.1 in development branch"

echo "Line3>> This is the advancement of previous feature" >> version01.txt
git add version01.txt
git commit -m "Added feature2.2 in development branch"

echo "Line4>> Feature 2 is completed and ready for release" >> version01.txt
git add version01.txt
git commit -m "Feature2 completed"
```

These commits will be reflected in the 'development' branch.

**Step 2: Rebasing in Production Branch**

```plaintext
# Create a new branch from 'master' called 'production'
git checkout -b production

# Use 'git rebase' to bring in the latest changes from 'development'
git rebase development
```

Now, the 'production' branch will have the latest features from 'development'.

### Task-03: Cherry Picking and Modifying Commits

**Step 1: Cherry Picking a Commit**

```plaintext
# Assuming you're in the 'production' branch
# Cherry pick the commit from 'development'
git cherry-pick <commit-hash-of-"Added feature2.2 in development branch">
```

**Step 2: Adding Lines and Creating a New Commit**

* Open `version01.txt` and make the required additions.
    
* Save the file.
    

```plaintext
# Add the modified file
git add version01.txt

# Commit the changes with an appropriate message
git commit -m "Optimized the feature"
```

Now, the 'production' branch has cherry-picked the commit from 'development' and applied additional changes. This optimized feature is now part of the 'production' branch.

## Conclusion

Mastering advanced Git concepts like `git stash`, `cherry pick`, and conflict resolution is essential for any DevOps engineer looking to optimize their workflow. These techniques empower you to manage your codebase efficiently, apply specific changes selectively, and navigate through the challenges of collaboration. By incorporating these practices into your toolkit, you'll be better equipped to handle complex scenarios and maintain a smooth development pipeline. Happy coding!

[https://www.linkedin.com/in/arjunmenon-devops/](https://www.linkedin.com/in/arjunmenon-devops/)