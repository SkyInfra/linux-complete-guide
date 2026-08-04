# 📁 File and Directory Management in Linux

## 📌 Learning Objectives

In this chapter, you will learn:

- How to navigate the Linux file system
- Create and remove directories
- Create, copy, move, rename, and delete files
- Understand the most commonly used file management commands

---

# 🤔 What is File Management?

Everything in Linux is stored as a **file**.

Examples:

- Documents
- Images
- Videos
- Programs
- Configuration files
- Directories (folders)

Linux provides commands to manage these files efficiently.

---

# 🌍 Real-World Example

Imagine your laptop.

You have folders like:

```text
Documents/
Downloads/
Pictures/
Projects/
```

Inside these folders, you create, copy, rename, move, and delete files.

Linux works exactly the same way.

---

# 📂 Understanding Files and Directories

A **File** stores data.

Examples:

```text
resume.pdf
notes.txt
photo.png
program.cpp
```

A **Directory (Folder)** stores files and other directories.

Example:

```text
Projects/
├── Linux
├── Docker
└── DevOps
```

---

# 📋 List Files and Directories

## ls

Displays files and directories in the current location.

```bash
ls
```

Example Output:

```text
Documents
Downloads
Pictures
file.txt
```

---

## ls -l

Displays detailed information.

```bash
ls -l
```

Example Output:

```text
-rw-r--r-- 1 root root 120 Jul 31 notes.txt
```

---

## ls -a

Displays hidden files.

```bash
ls -a
```

Example:

```text
.
..
.bashrc
.profile
notes.txt
```

---

## ls -ltr

Displays files in long format sorted by modification time.

```bash
ls -ltr
```

---

# 📍 Print Current Directory

## pwd

Displays your current location.

```bash
pwd
```

Example Output:

```text
/home/haseeb
```

---

# 📁 Change Directory

## cd

Move into another directory.

```bash
cd Documents
```

Move to the home directory:

```bash
cd
```

Move one level back:

```bash
cd ..
```

Move to the previous directory:

```bash
cd -
```

Move to the root directory:

```bash
cd /
```

---

# 📂 Create Directories

## mkdir

Create a directory.

```bash
mkdir Projects
```

Create multiple directories.

```bash
mkdir Docker Linux Kubernetes
```

Create nested directories.

```bash
mkdir -p DevOps/Linux/Bash
```

---

# 🗑️ Remove Directories

## rmdir

Deletes an empty directory.

```bash
rmdir Projects
```

---

## rm -r

Deletes a directory and all its contents.

```bash
rm -r Projects
```

⚠️ Be careful.

This permanently deletes everything inside the directory.

---

# 📄 Copy Files

## cp

Copy one file.

```bash
cp notes.txt backup.txt
```

Now both files exist.

---

# 📂 Copy Directories

Use the recursive option.

```bash
cp -r Projects Backup
```

---

# 🚚 Move or Rename Files

## mv

Move a file.

```bash
mv notes.txt Documents/
```

Rename a file.

```bash
mv old.txt new.txt
```

Rename a directory.

```bash
mv Project Linux-Project
```

---

# ❌ Delete Files

Delete a file.

```bash
rm notes.txt
```

Delete multiple files.

```bash
rm file1.txt file2.txt
```

Delete everything inside a directory.

```bash
rm -r folder
```

---

# 📊 Command Summary

| Command | Description |
|----------|-------------|
| `ls` | List files and directories |
| `ls -l` | Long listing format |
| `ls -a` | Show hidden files |
| `ls -ltr` | Long listing sorted by modification time |
| `pwd` | Display current directory |
| `cd folder` | Change directory |
| `cd ..` | Move to parent directory |
| `cd /` | Move to root directory |
| `mkdir folder` | Create a directory |
| `mkdir -p path` | Create nested directories |
| `rmdir folder` | Remove an empty directory |
| `rm file` | Delete a file |
| `rm -r folder` | Delete a directory and its contents |
| `cp source destination` | Copy a file |
| `cp -r source destination` | Copy a directory |
| `mv source destination` | Move or rename a file/directory |

---

# 💻 Practice Lab

Run the following commands one by one.

```bash
# Check current location
pwd

# List files
ls

# Create directories
mkdir Linux
mkdir Docker

# List files
ls

# Enter Linux directory
cd Linux

# Verify location
pwd

# Create a file
touch notes.txt

# List files
ls

# Copy the file
cp notes.txt backup.txt

# Rename the file
mv backup.txt linux-notes.txt

# Go back
cd ..

# Delete directory
rm -r Docker

# Display final structure
ls -ltr
```

---

# 🎯 Interview Questions

### Q1. What is the difference between a file and a directory?

A file stores data, while a directory stores files and other directories.

---

### Q2. What is the difference between `rm` and `rmdir`?

- `rm` deletes files.
- `rmdir` deletes only empty directories.
- `rm -r` deletes directories along with their contents.

---

### Q3. What is the difference between `cp` and `mv`?

- `cp` creates a copy.
- `mv` moves or renames the original file.

---

# 📝 Key Takeaways

- Everything in Linux is organized as files and directories.
- `ls` displays files and directories.
- `pwd` shows your current location.
- `cd` changes directories.
- `mkdir` creates directories.
- `rm` deletes files.
- `cp` copies files.
- `mv` moves or renames files.

