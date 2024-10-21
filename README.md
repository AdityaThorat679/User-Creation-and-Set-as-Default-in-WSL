# User Creation and Setting Default User in WSL

## Introduction
In Ubuntu, creating and managing users is important for controlling access to the system. This guide explains how to create a new user, assign them admin privileges, and set them as the default user when logging into WSL (Windows Subsystem for Linux). It outlines two methods for creating a user and provides instructions for setting the new user as the default account.

---

## Step 1: Creating a User in Ubuntu

There are two ways to add a user in Ubuntu:

### 1. `adduser` Command
The `adduser` command is used to create a user and add all necessary details.

**Syntax:**
```bash
sudo adduser username
```

**Example:**
```bash
root@LAPTOP-U5U0ADKN:~# sudo adduser adityathorat
info: Adding user `adityathorat' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `adityathorat' (1000) ...
info: Adding new user `adityathorat' (1000) with group `adityathorat (1000)' ...
info: Creating home directory `/home/adityathorat' ...
info: Copying files from `/etc/skel' ...
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for adityathorat
Enter the new value, or press ENTER for the default
    Full Name []: Aditya Thorat
    Room Number []: 01
    Work Phone []: 9797979797
    Home Phone []: 9111111111
    Other []: 0
Is the information correct? [Y/n] y
info: Adding new user `adityathorat' to supplemental / extra groups `users' ...
info: Adding user `adityathorat' to group `users' ...
```

### 2. `useradd` Command
The `useradd` command can also be used to create a user, but this only creates the user without setting up additional details (like password, home directory, etc.).

**Syntax:**
```bash
sudo useradd username
```

**Example:**
```bash
root@LAPTOP-U5U0ADKN:~# sudo useradd adi
```

---

## Step 2: Adding the User to a Group

After creating the user, you can add them to the `sudo` group to give them administrative privileges using the `usermod` command.

**Syntax:**
```bash
sudo usermod -aG sudo username
```
- `-aG`: This option appends the user to the specified group(s) without removing them from any other groups.
- `sudo`: This group grants the user administrative privileges.

**Example:**
```bash
root@LAPTOP-U5U0ADKN:~# sudo usermod -aG sudo adityathorat
```

---

## Step 3: Setting the New User as Default

To make the newly created user the default user in WSL, follow these steps:

### 1. Open the Ubuntu terminal.

### 2. Change the directory to `/etc` and edit the `wsl.conf` file.

```bash
nano /etc/wsl.conf
```

### 3. Add or Modify the `[user]` Section:
If the file exists, modify the user section. If it doesn’t exist, create it and add the following lines:

```bash
[user]
default = your_username
```
Replace `your_username` with the username you want to set as the default.

**Example:**
```bash
[user]
default = adityathorat
```

### 4. Restart WSL
After editing the file, restart WSL for the changes to take effect. In Command Prompt or PowerShell, run:

```bash
wsl --shutdown
```

After completing these steps, the newly created user will be the default user.

**Example Output:**
```bash
adityathorat@LAPTOP-U5U0ADKN:~$
```
