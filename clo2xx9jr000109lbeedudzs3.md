---
title: "Day 3: Basic Linux Commands"
datePublished: Mon Oct 23 2023 13:35:33 GMT+0000 (Coordinated Universal Time)
cuid: clo2xx9jr000109lbeedudzs3
slug: day-3-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698067850122/f64601fd-e6d7-4e9c-a73f-9b913b900555.png
tags: linux, devops, 90daysofdevops

---

### To View the contents of a file

`Cat` - This Linux command allows you to view the contents of a file

> **Simply type** `cat filename` **& Press** `Enter`
> 
> **Replace "filename" with the name of the file you want to view.**

### Change access permissions of files

`chmod` -To modify the access permissions of a file, use the `chmod` command followed by the permission code and the file name.

The permission code consists of three digits representing `read (4)`, `write (2),` and `execute (1)`permissions for the owner, group, and others, respectively.

> **Simply type** `chmod 644 filename`**& Press** `Enter`
> 
> **For example - To give read and write permissions to the owner (4 for read + 2 for write = 6) and read-only permissions to the group (4) and others (also 4):**
> 
> **Here's a breakdown of the numeric representation as per the command**
> 
> **The first digit (6) represents the permissions for the owner (read + write). The second digit (4) represents the permissions for the group (read). The third digit (also 4) represents the permissions for others (read). Replace "filename" with the name of the file you want to modify. After running this command, the owner will have read and write permissions, while the group and others will have read-only permissions.**

### Check your command history

`history` -To view the list of commands you have run in the terminal session history.

> **Simply type** `history`**& Press** `Enter`
> 
> **This will display a numbered list of commands you executed during the current session.**

### Remove a directory/folder

`rm` - To remove a directory/ Folder.

> **Simply type** `rm filename/directoryname` **& Press** `Enter`

### Create a fruits.txt file and view its content

`touch` - To create an empty file named "fruits.txt,"

`cat` -To view the contents of the file (we discussed earlier)

> **Simply type** `touch filename` **& Press** `Enter`
> 
> **then ,type** `cat filename` **& Press** `Enter`

### Add content in fruits.txt (One in each line)

`Vim` - To open a file to add content

> **Simply type** `vim filename` **Press** `Enter`
> 
> **Inserting Text: To start inserting or editing text within the file, press** `i` **for insert mode. You can then type or modify text as needed.**
> 
> **Saving and Exiting: To save the changes and exit vim, press** `Esc` **to ensure you are in normal mode, and then type** `:wq` **or** `ZZ (Shift + zz)` **Press** `Enter`

### To Show only the top three fruits from the file

`head` - To display the top lines of the file

> **Simply type** `head -3 filename` **Press** `Enter`
> 
> **you can also use the** `head` **command with the** `-n` **option**

### To Show only the bottom three fruits from the file

`tail` -To display the last lines of the file,

> **Simply type** `tail -3 filename` **Press** `Enter`
> 
> **you can also use the** `tail` **command with the** `-n` **option**

### To create another file with content in Colors.txt (One in each line) and to view the content.

> **We already discussed this earlier** `touch` **,**`vim` **&** `cat` **command**

### To find the difference between fruits.txt and Colors.txt file

`diff` - To compare the contents of two files and find the differences

> **Simply type** `diff filename1 filename2` **Press** `Enter`
> 
> **The** `diff` **command will display the lines that are different between the two files, if any.**

I hope you found this blog helpful!

Happy learning!