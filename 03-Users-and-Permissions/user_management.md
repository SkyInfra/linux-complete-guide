# 👤 User Management in Linux

## 📌 Learning Objectives

In this chapter, you will learn:

- What is user management?
- Why user management is important
- Create users
- Modify users
- Delete users
- Manage passwords
- Manage groups
- Grant administrator (sudo) access

---

# 🤔 What is User Management?

Linux is a **multi-user operating system**, meaning multiple users can use the same system simultaneously.

Each user has their own:

- Username
- Password
- Home directory
- Permissions

User management is the process of creating, modifying, securing, and removing user accounts.

---

# 🌍 Real-World Example

Imagine a company.

When a new employee joins:

- Create an employee account.
- Assign a password.
- Place them in the correct department.
- Give the required permissions.

When the employee leaves:

- Disable or delete the account.

Linux manages users in exactly the same way.

---

# 📂 Important User Management Files

Linux stores user information inside the `/etc` directory.

| File | Purpose |
|------|---------|
| `/etc/passwd` | Stores user account information |
| `/etc/shadow` | Stores encrypted user passwords |
| `/etc/group` | Stores group information |
| `/etc/gshadow` | Stores secure group information |

---

# 👤 Creating Users

## Using `adduser` (Recommended)

```bash
adduser haseeb
```

This command:

- Creates the user
- Creates a home directory
- Creates a user group
- Prompts for a password
- Asks for optional user information

Example:

```bash
adduser haseeb
```

---

## Using `useradd`

```bash
useradd haseeb
```

This is a lower-level command.

It only creates the user account.

Usually, you must create the home directory and configure other settings yourself.

---

## Create a Home Directory

```bash
useradd -m haseeb
```

The `-m` option creates:

```text
/home/haseeb
```

---

## Specify the Default Shell

```bash
useradd -s /bin/bash haseeb
```

This sets Bash as the user's default shell.

---

# 🔑 Managing Passwords

## Set or Change Password

```bash
passwd haseeb
```

Linux prompts for a new password.

---

## Lock a User Account

```bash
passwd -l haseeb
```

The user cannot log in until the account is unlocked.

---

## Unlock a User Account

```bash
passwd -u haseeb
```

This enables the account again.

---

## Set Password Expiration

Force the user to change the password every 90 days.

```bash
chage -M 90 haseeb
```

---

# ✏️ Modifying Users

## Rename a User

```bash
usermod -l hassan haseeb
```

Changes:

```
haseeb
```

to

```
hassan
```

---

## Change Home Directory

```bash
usermod -d /home/hassan -m hassan
```

Moves the user's files to the new home directory.

---

## Change Default Shell

```bash
usermod -s /bin/zsh hassan
```

Now the user will use Zsh instead of Bash.

---

# 🗑️ Deleting Users

## Delete User Only

```bash
userdel haseeb
```

The account is deleted.

The home directory remains.

---

## Delete User and Home Directory

```bash
userdel -r haseeb
```

Deletes:

- User account
- Home directory
- Mail files

---

# 👥 Working with Groups

Groups make permission management easier.

Instead of giving permissions to each user individually, Linux assigns permissions to a group.

---

## Create a Group

```bash
groupadd developers
```

---

## Add User to a Group

```bash
usermod -aG developers haseeb
```

The user **haseeb** becomes a member of the **developers** group.

---

## View User Groups

```bash
groups haseeb
```

Example Output:

```text
haseeb : haseeb developers sudo
```

---

## Change Primary Group

```bash
usermod -g developers haseeb
```

---

# 🔐 Sudo Access

Normally, a normal user cannot perform administrative tasks.

Linux provides **sudo (Super User Do)** for temporary administrator privileges.

---

## Add User to the Sudo Group (Ubuntu/Debian)

```bash
usermod -aG sudo haseeb
```

Now the user can run commands like:

```bash
sudo apt update
```

---

## Add User to the Wheel Group (RHEL/CentOS)

```bash
usermod -aG wheel haseeb
```

---

# ⚙️ Configure Sudo Permissions

Edit the sudoers file safely.

```bash
visudo
```

Example:

```text
haseeb ALL=(ALL) NOPASSWD: /usr/bin/systemctl
```

This allows the user to execute the specified command without entering a password.

---

# 💻 Practice Commands

```bash
# Create a new user
adduser haseeb

# Display current user
whoami

# Display user information
id haseeb

# Set a password
passwd haseeb

# Display all users
cat /etc/passwd

# Display all groups
cat /etc/group

# Create a group
groupadd developers

# Add user to a group
usermod -aG developers haseeb

# View user's groups
groups haseeb

# Lock a user
passwd -l haseeb

# Unlock a user
passwd -u haseeb

# Delete a user
userdel -r haseeb
```

---

# 📊 Command Summary

| Command | Description |
|----------|-------------|
| `adduser username` | Create a new user (recommended) |
| `useradd username` | Create a user (basic command) |
| `useradd -m username` | Create a user with a home directory |
| `passwd username` | Set or change a password |
| `passwd -l username` | Lock a user account |
| `passwd -u username` | Unlock a user account |
| `chage -M 90 username` | Set password expiration |
| `usermod -l new old` | Rename a user |
| `usermod -d /home/user -m username` | Change the home directory |
| `usermod -s /bin/bash username` | Change the default shell |
| `userdel username` | Delete a user |
| `userdel -r username` | Delete a user and home directory |
| `groupadd groupname` | Create a group |
| `usermod -aG group user` | Add a user to a group |
| `groups username` | View user groups |
| `usermod -g group username` | Change the primary group |
| `visudo` | Edit the sudoers file safely |

---

# 📝 Key Takeaways

- Linux is a multi-user operating system.
- Every user has a unique account and permissions.
- `adduser` is recommended for beginners because it is interactive.
- `useradd` is a lower-level command used for advanced user creation.
- Passwords are managed using the `passwd` command.
- Groups simplify permission management.
- `sudo` allows trusted users to perform administrative tasks without logging in as the root user.