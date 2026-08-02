# File Permissions in Linux

## Introduction

Linux is a **multi-user operating system**, which means multiple users can access the same system at the same time.

To keep the system secure, Linux uses **file permissions** to control:

- Who can read a file
- Who can modify a file
- Who can execute a file

Every file and directory in Linux has a set of permissions.

---

# Why Do We Need File Permissions?

Imagine a company server.

- Developers store source code.
- HR stores employee records.
- Finance stores salary information.

Without file permissions:

- Anyone could modify important files.
- Anyone could delete data.
- Anyone could access confidential information.

Linux prevents this by assigning permissions to every file and directory.

---

# Understanding Linux Permissions

Run the following command:

```bash
ls -l
```

Example output:

```text
-rwxr-xr-- 1 haseeb developers 245 Aug 2 12:30 script.sh
```

Let's understand each part.

```
-rwxr-xr--
││ │ │
││ │ └── Others
││ └──── Group
│└────── Owner
└──────── File Type
```

---

# File Types

The first character indicates the file type.

| Symbol | Meaning |
|---------|---------|
| `-` | Regular File |
| `d` | Directory |
| `l` | Symbolic Link |
| `c` | Character Device |
| `b` | Block Device |

Example:

```text
-rw-r--r--
```

Regular file.

```text
drwxr-xr-x
```

Directory.

---

# Permission Categories

Linux divides permissions into three categories.

## Owner (User)

The person who owns the file.

Example:

```text
-rwx------
```

The first three characters belong to the owner.

---

## Group

Users belonging to the same group.

```text
---r-x---
```

The middle three characters belong to the group.

---

## Others

Everyone else.

```text
------r--
```

The last three characters belong to others.

---

# Types of Permissions

Linux has three basic permissions.

## Read (r)

Value:

```
4
```

Allows you to:

- Open a file
- Read its contents

Example:

```bash
cat notes.txt
```

Without read permission:

```
Permission denied
```

---

## Write (w)

Value:

```
2
```

Allows you to:

- Edit a file
- Save changes
- Delete or rename the file (if directory permissions allow)

Example:

```bash
nano notes.txt
```

---

## Execute (x)

Value:

```
1
```

Execution means Linux is allowed to run the file as a program or script.

Example:

```bash
./script.sh
```

Without execute permission:

```
Permission denied
```

---

# Permission Values

| Permission | Value |
|------------|-------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

---

# Numeric Permissions

Linux combines these values.

| Number | Permission |
|---------|------------|
| 0 | --- |
| 1 | --x |
| 2 | -w- |
| 3 | -wx |
| 4 | r-- |
| 5 | r-x |
| 6 | rw- |
| 7 | rwx |

---

# Common Permission Sets

## 755

```
rwxr-xr-x
```

Owner

- Read
- Write
- Execute

Group

- Read
- Execute

Others

- Read
- Execute

Used for:

- Shell scripts
- Directories
- Web applications

---

## 644

```
rw-r--r--
```

Owner

- Read
- Write

Group

- Read

Others

- Read

Used for:

- Text files
- Configuration files
- Source code

---

## 700

```
rwx------
```

Only the owner has access.

Used for:

- Private directories
- SSH folders

---

## 600

```
rw-------
```

Only the owner can read and write.

Used for:

- Private keys
- Password files
- Sensitive configuration files

---

## 777

```
rwxrwxrwx
```

Everyone has full access.

⚠️ This is **not recommended** because it is a security risk.

---

# Viewing Permissions

```bash
ls -l
```

Human-readable file sizes:

```bash
ls -lh
```

Show hidden files:

```bash
ls -la
```

---

# Changing Permissions

Use the `chmod` command.

Syntax:

```bash
chmod permissions filename
```

Example:

```bash
chmod 755 script.sh
```

---

# Common chmod Examples

```bash
chmod 755 script.sh
```

```bash
chmod 644 notes.txt
```

```bash
chmod 700 project
```

```bash
chmod 600 id_rsa
```

---

# Changing Permissions Recursively

```bash
chmod -R 755 project/
```

`-R` means recursive.

Linux changes the permissions of:

- Directory
- Files
- Subdirectories

---

# Changing File Ownership

Use:

```bash
chown owner filename
```

Example:

```bash
chown haseeb notes.txt
```

Change owner and group:

```bash
chown haseeb:developers notes.txt
```

---

# Changing Group

```bash
chgrp developers notes.txt
```

---

# Real-World Examples

## Shell Script

```bash
chmod +x deploy.sh
```

Now it can be executed.

---

## SSH Private Key

```bash
chmod 600 ~/.ssh/id_rsa
```

Only the owner can access the key.

---

## Website Files

```bash
sudo chown -R www-data:www-data /var/www/html
```

Apache or Nginx can now manage website files.

---

## Application Directory

```bash
chmod -R 755 project/
```

Allows users to access the project while protecting write access.

---

# Best Practices

✅ Give the minimum permissions required.

✅ Avoid using `777`.

✅ Use `600` for private keys.

✅ Use `644` for text files.

✅ Use `755` for executable scripts and directories.

✅ Verify permissions using:

```bash
ls -l
```

---

# Common Beginner Mistakes

❌ Using `777` for every file.

❌ Forgetting execute permission on scripts.

❌ Confusing `chmod` and `chown`.

❌ Running a script without execute permission.

---

# Summary

| Command | Purpose |
|---------|---------|
| `ls -l` | View file permissions |
| `chmod` | Change file permissions |
| `chown` | Change file owner |
| `chgrp` | Change file group |
| `ls -lh` | Human-readable file sizes |
| `ls -la` | Show hidden files |

---

# Key Takeaways

- Linux protects files using permissions.
- Every file has an **Owner**, **Group**, and **Others**.
- The three permission types are **Read**, **Write**, and **Execute**.
- Numeric permissions are calculated using **4 (Read)**, **2 (Write)**, and **1 (Execute)**.
- `chmod` changes permissions.
- `chown` changes the owner.
- `chgrp` changes the group.
- Always follow the principle of **least privilege** by giving only the permissions that are required.