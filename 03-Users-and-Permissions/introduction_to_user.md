# 👥 Types of Users in Linux

## 📌 Learning Objective

In this chapter, you will learn:

- What a user is in Linux
- Why Linux uses users
- Types of users in Linux
- The difference between Root, Normal, and System users
- Basic commands to inspect users

---

# 🤔 What is a User?

A **user** is an identity that Linux uses to determine **who is performing an action** on the system.

Every action in Linux—such as creating files, installing software, deleting files, or running commands—is performed by a user.

Linux uses users to provide **security**, **controlled access**, and **system integrity**.

---

# ❓ Why Does Linux Need Users?

Imagine everyone had complete access to a Linux server.

Anyone could:

- Delete important system files
- Install malicious software
- Read private data
- Modify system settings
- Shut down the server

To prevent this, Linux checks **who is performing an action** before allowing it.

If the user has permission, Linux allows the action.

Otherwise, it returns:

```text
Permission denied
```

---

# 👥 Types of Users

Linux has **three main types of users**.

## 1️⃣ Root User (Super User)

The **Root User** is the administrator of the Linux system.

It has **complete control** over the operating system.

### Responsibilities

- Install or remove software
- Create or delete users
- Change system settings
- Manage files and directories
- Access every file
- Shutdown or restart the system

### Home Directory

```text
/root
```

### Check Current User

```bash
whoami
```

Example Output

```text
root
```

---

## 2️⃣ Normal User

A **Normal User** is created for everyday work.

Normal users have limited permissions to keep the system secure.

### Can Do

- Create files
- Delete personal files
- Run applications
- Browse directories
- Write code

### Cannot Do

- Modify system files
- Install system software (without `sudo`)
- Create users
- Change system configuration

### Home Directory

```text
/home/username
```

Example

```text
/home/haseeb
```

---

## 3️⃣ System User

A **System User** is created automatically for applications and services.

These users are **not intended for human login**.

Instead, applications use them to run securely.

### Examples

- `www-data`
- `mysql`
- `postgres`
- `daemon`
- `nobody`

### Why Are System Users Needed?

Instead of running applications as **root**, Linux creates dedicated users with limited permissions.

For example:

- Nginx → `www-data`
- MySQL → `mysql`

This improves system security.

---

# 📊 User Comparison

| Feature | Root User | Normal User | System User |
|----------|-----------|-------------|-------------|
| Used By | Administrator | Human Users | Applications & Services |
| Full System Access | ✅ Yes | ❌ No | ❌ No |
| Install Software | ✅ Yes | ❌ (without sudo) | ❌ |
| Create Users | ✅ Yes | ❌ | ❌ |
| Home Directory | `/root` | `/home/username` | Usually none |
| Login Allowed | ✅ Yes | ✅ Yes | Usually No |

---

# 🌍 Real-World Analogy

Imagine a company.

👑 **CEO → Root User**

- Full control over the company.

👨‍💻 **Employees → Normal Users**

- Perform daily work with limited permissions.

🤖 **Machines / Security Cameras → System Users**

- Perform specific tasks automatically.

Linux follows the same model.

---

# 💻 Practice Commands

Display the current user:

```bash
whoami
```

Display user information:

```bash
id
```

Display all users:

```bash
cat /etc/passwd
```

Display only usernames:

```bash
cut -d: -f1 /etc/passwd
```

Find the root user:

```bash
grep root /etc/passwd
```

---

# ✅ Best Practices

- Do not use the **root** account for daily work.
- Create a normal user for regular tasks.
- Use **sudo** only when administrative privileges are required.
- Never share the root password.

---

# 🎯 Interview Questions

### Q1. What is a user in Linux?

A user is an identity that Linux uses to determine who is performing an action on the system.

---

### Q2. How many types of users are there in Linux?

There are three main types:

- Root User
- Normal User
- System User

---

### Q3. Why are system users created?

System users allow applications and services to run securely with limited permissions instead of using the root account.

---

### Q4. What is the home directory of the root user?

```text
/root
```

---

# 📝 Summary

- Linux is a multi-user operating system.
- Every action is performed by a user.
- Root User has complete administrative control.
- Normal Users are used for daily work.
- System Users run applications and services securely.
- Linux uses users to improve security and control access to system resources.
