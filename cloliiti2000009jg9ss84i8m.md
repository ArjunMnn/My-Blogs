---
title: "Day 12: The Ultimate Cheat Sheet with Linux, Git, and GitHub Commands"
datePublished: Sun Nov 05 2023 13:32:02 GMT+0000 (Coordinated Universal Time)
cuid: cloliiti2000009jg9ss84i8m
slug: day-12-the-ultimate-cheat-sheet-with-linux-git-and-github-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699191085678/243cd673-490d-4c31-8e56-6ef4d80090a8.png
tags: cloud, linux, github, git, devops

---

### **🚀Introduction**

Mastering the command line is a fundamental skill for developers and IT professionals. This cheat sheet offers a consolidated list of vital Linux, Git, and GitHub commands that cover a wide range of categories, from basic operations to networking and version control. Organized for quick reference, this resource will empower you to navigate the command line with confidence and efficiency.

### **💻Linux Commands with Description & Usage**

1. `ls`: List all the directories and files.
    
2. `mkdir`: Makes a new directory.
    
3. `rmdir`: Remove a directory (only if it's empty).
    
4. `cd`: Change directory.
    
5. `cd ..`: Go back to the previous directory.
    
6. `pwd`: Print the current working directory.
    
7. `ls -l`: List files with more details.
    
8. `cat`: Show the content of a file.
    
9. `echo`: Shows the desired string and value.
    
10. `man`: Tells about all commands.
    
11. `touch`: Create a file.
    
12. `cp`: Copy files.
    
13. `mv`: Move files.
    
14. `rm`: Remove the file permanently.
    
15. `sudo`: Administrative commands (password).
    
16. `head`: Display the first 10 lines.
    
17. `tail`: Display the last 10 lines.
    
18. `zip`: Zip files in Linux.
    
19. `unzip`: Unzip files in Linux.
    
20. `ssh`: Secure Shell command in Linux.
    
21. `service`: Linux command to start and stop services.
    
22. `ps`: Display active processes.
    
23. `wget`: Download files from the internet.
    
24. `whoami`: Show the current user.
    
25. `grep`: Search for a string within an output.
    
26. `sort`: Sort the file content.
    
27. `cal`: View Calendar in the terminal.
    
28. `whereis`: View the exact location of any command types after this command.
    
29. `kill` and `killall`: Kill active processes by process ID or name.
    
30. `chmod`: Change file permissions.
    
31. `chown`: Change file ownership.
    
32. `history`: Shows history of command usage.
    
33. `useradd` and `usermod`: Add a new user or change the existing user's data.
    
34. `passwd`: Create or update passwords for existing users.
    
35. `df`: Display disk space usage of file systems.
    
36. `du`: Estimate file and directory space usage.
    
37. `tar`: Archive files and directories into a single file.
    
38. `find`: Search for files and directories.
    
39. `grep`: Search for a pattern in files.
    
40. `chmod`: Change file permissions.
    
41. `chown`: Change file ownership.
    
42. `ln`: Create links between files.
    
43. `uptime`: Show system uptime and load averages.
    
44. `top`: Display system processes and resource usage.
    
45. `free`: Display memory usage statistics.
    
46. `ifconfig`: Display or configure network interfaces.
    
47. `netstat`: Display network statistics.
    
48. `ssh-keygen`: Generate SSH key pairs.
    
49. `scp`: Securely copy files between hosts.
    
50. `rsync`: Synchronize files and directories between two locations.
    
51. `cron`: Schedule tasks to run at specific intervals.
    
52. `crontab`: Manage user-specific cron jobs.
    
53. `history`: View and manage command history.
    
54. `sed`: Stream editor for text manipulation.
    
55. `awk`: Text processing and pattern matching.
    
56. `nano` or `vi`: Text editors for file editing.
    
57. `ping`: Send network ICMP echo requests to a host.
    
58. `traceroute`: Trace the route packets take to a destination.
    
59. `shutdown`: Shutdown or reboot the system.
    
60. `kill`: Terminate processes by ID or name.
    
61. `ps aux`: Display detailed information about active processes.
    
62. `uptime`: Show system uptime and load averages.
    
63. `nc`: Netcat - network utility for reading/writing network connections.
    

> Note: You can explore further by referring to their respective `man` pages or online Linux documentation.

### **🐙Git-GitHub Commands with Description & Usage**

1. `git init`: Initialize a new Git repository in the current directory.
    
2. `git clone <repository-url>`: Clone a remote repository to your local machine.
    
3. `git status`: Show the current status of the repository.
    
4. `git add <file>`: Add a file to the staging area.
    
5. `git commit -m "commit message"`: Create a new commit with a message.
    
6. `git diff`: View the differences between the working directory and the staging area.
    
7. `git log`: Display the commit history.
    
8. `git branch`: List all branches in the repository.
    
9. `git checkout <branch>`: Switch to a different branch.
    
10. `git merge <branch>`: Merge changes from a branch into the current branch.
    
11. `git pull`: Fetch and merge changes from a remote repository.
    
12. `git push`: Push local commits to a remote repository.
    
13. `git remote add origin <repository-url>`: Add a remote repository as the origin.
    
14. `git remote -v`: View a list of remote repositories and their URLs.
    
15. `git reset <file>`: Unstage changes for a file.
    
16. `git rm <file>`: Remove a file from the repository and staging area.
    
17. `git stash`: Temporarily store changes not ready for a commit.
    
18. `git cherry-pick <commit>`: Apply changes from a specific commit.
    
19. `git fetch`: Download objects and refs from another repository.
    
20. `git revert <commit>`: Create a new commit that undoes changes from a specific commit.
    
21. `git push origin <branch>`: Push local commits to a remote branch on GitHub.
    
22. `git pull origin <branch>`: Fetch and merge changes from a remote branch on GitHub.
    
23. `git fork`: Create a copy of a repository on your GitHub account.
    
24. `git pull-request`: Create a pull request to propose changes from your fork.
    
25. `git pull upstream <branch>`: Pull changes from the original repository after forking (upstream).
    
26. `git remote add upstream <original-repo-url>`: Add the original repository as the upstream remote for your fork.
    
27. `git branch -d <branch>`: Delete a local branch after it's merged and no longer needed.
    
28. `git push origin --delete <branch>`: Delete a remote branch on GitHub.
    
29. `git stash pop`: Apply and remove the most recently stashed changes.
    
30. `git stash list`: List all stashed changes.
    
31. `git stash apply`: Apply the changes from a specific stash.
    
32. `git stash drop`: Delete a specific stash.
    
33. `git stash clear`: Remove all stashes.
    
34. `git remote show <remote>`: Show detailed information about a remote.
    
35. `git tag`: Create, list, or delete tags.
    
36. `git blame <file>`: Show who changed each line in a file.
    
37. `git config`: Set or get repository or global configuration options.
    
38. `git log --graph`: Display the commit history in a graph view.
    
39. `git reflog`: Show a log of changes to branch references.
    
40. `git rebase`: Reapply commits on top of another base tip.
    
41. `git reset --hard <commit>`: Reset the repository to a specific commit.
    
42. `git clean`: Remove untracked files and directories.
    
43. `git bisect`: Find the commit that introduced a bug using binary search.
    
44. `git show`: Show the details and changes of a commit.
    
45. `git grep`: Search for a pattern in tracked files.
    
46. `git remote set-url <remote> <url>`: Update the URL of a remote repository.
    
47. `git submodule`: Manage submodules within a repository.
    
48. `git rebase -i`: Interactively rebase commits.
    
49. `git cherry-pick --continue` / `--abort`: Continue or abort a cherry-pick sequence.
    
50. `git commit --amend`: Modify the most recent commit.
    
51. `git log --author=<author>`: Show commit history by a specific author.
    
52. `git log --since=<date>`: Show commit history since a specific date.
    
53. `git log --grep=<pattern>`: Show commits with messages matching a pattern.
    

### **🎉Conclusion**

This cheat sheet of essential Linux, Git, and GitHub commands serves as a valuable resource for developers and IT enthusiasts at all levels. Whether you're managing files, working with networks, or handling version control, these commands provide the building blocks for efficient and effective command-line usage. By referring to this cheat sheet, you'll streamline your workflow, troubleshoot more effectively, and become a more proficient command-line user🚀💻.

Let's connect on LinkedIn - [https://www.linkedin.com/in/arjunmenon-devops/](https://www.linkedin.com/in/arjunmenon-devops/)