---
title: "Day 5: Advanced Linux Shell Scripting for DevOps Engineers with User management"
datePublished: Wed Oct 25 2023 14:20:51 GMT+0000 (Coordinated Universal Time)
cuid: clo5uf7ms000109i67vczh7j2
slug: day-5-advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698243618163/5e132f40-9944-4b08-ae6b-4218323a35f7.png
tags: linux, devops, software-engineering, shell-scripting, 90daysofdevops

---

### Introduction

Welcome to Day 5 of the #90DaysOfDevOps challenge!

Today, we will cover several topics related to Linux system administration and shell scripting. We'll start with creating dynamic directories using the command line, followed by an automated backup script, and then we'll learn how to schedule the backup script with the help of Cron. Additionally, we'll explore user management in Linux, including creating and displaying usernames. Finally, we'll conclude our blog with a script to create multiple directories with dynamic names based on user input.

### **Creating Dynamic Directories using Shell Scripting**

Let's now develop a bash script that allows users to create multiple directories with dynamic names based on their inputs. The script will use a **for loop** and command-line arguments to achieve this.

Create a new file named `createDirectories.sh` and open it in a text editor `vim`

Below is the script.

```plaintext
#!/bin/bash

directory_name=$1 
start_num=$2 
end_num=$3

for ((i=start_num; i<end_num; i++)); do 
    mkdir -p "${directory_name}${i}" 
done
```

Script Breakdown:

1. **Command-line Arguments**:
    
    * `directory_name`: This variable holds the base name for the directories to be created. It is the first argument provided when executing the script.
        
    * `start_num`: The second argument specifies the starting index for the loop, determining the first directory's name.
        
    * `end_num`: This argument sets the upper limit for the loop, determining when the directories creation will stop.
        
2. **For Loop**:
    
    * The `for` loop initializes `i` with the value of `start_num`. It continues until `i` reaches `end_num`, incrementing `i` by 1 in each iteration.
        
    * `((i=start_num; i<end_num; i++))` is the loop declaration, where `i` starts at `start_num`, checks if `i` is less than `end_num`, and increments `i` by 1 in each iteration.
        
3. **mkdir Command**:
    
    * `mkdir -p "${directory_name}${i}"` is the command responsible for creating directories.
        
    * `-p` flag ensures that if the directories already exist, it doesn't throw an error, and it creates the parent directories if they don't exist.
        
    * `"${directory_name}${i}"` concatenates `directory_name` with the current value of `i`, creating a unique directory name for each iteration.
        

Now, make the script executable & run the script with three arguments: the desired directory name and the range of directories they want to create.

### **Automated Backup Script**

Having a reliable backup solution is crucial for safeguarding important files and data from accidental loss.

To create a script that backs up all your work done till now in Linux and creates an archive, we'll use the `tar` command, which is commonly used for archiving files. So, Follow the steps below to create the backup script:

**Step 1:** Create a new file named `backup.sh` and open it in a text editor.

**Step 2:** Add the Script Content Add the following content to the `backup.sh` script:

```plaintext
#!/bin/bash

src_dir=/home/ubuntu/scripts
trg_dir=/home/ubuntu/backups

timestamp=$(date "+%Y-%m-%d-%H-%M-%S")
backup_file=$trg_dir/$timestamp.tgz

echo "taking backup on $timestamp"

tar czf $backup_file --absolute-names $src_dir

echo "backup complete"
```

**Step 3:** Make the script executable with the following command:

**Step 4:** Run the Backup Script Now

The script will create a backup archive with the current date and time in the filename and store it in the specified backup directory.

### **Automating the Backup Script with Cron**

Automation is a boon for system administrators, and Cron provides an excellent way to schedule tasks to run at specified intervals. To automate our backup script, we'll schedule it to run at a designated time using Cron.

To edit the Cron table, run the following command:

```plaintext
crontab -e
```

Add the following line to the Cron table to schedule the backup script to run daily at 3:00 AM:

```plaintext
0 3 * * * /home/ubuntu/backup.sh
```

### **User Management in Linux**

User management is an integral part of Linux system administration. It involves creating, modifying, and managing user accounts on the system. Let's explore how to create a new user account and display a list of all existing users.

To create a new user in Linux, use the `useradd` command.

> **Note: To create new users, you will need root or administrative privileges on the system.**

**Step 1:** Create the first user To create a user named "user1".

```plaintext
sudo useradd user1
```

Step 2: Create the second user To create a user named "user2".

```plaintext
sudo useradd user2
```

Use the below command to display the names of the users we just created

```plaintext
awk -F':' '{ print $1}' /etc/passwd
```