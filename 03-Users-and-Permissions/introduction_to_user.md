# Types of Users in Linux

## What is a User?

A **user** is an identity that Linux uses to determine **who is performing an action** on the system. Every action in Linux, such as creating files, installing software, or running commands, is performed by a user.

Linux uses users to provide security and control access to system resources.

---

# Why Does Linux Need Users?

Without users, anyone could:

- Delete important system files
- Install malicious software
- Access private data
- Modify system settings

Linux checks the identity of the user before allowing any operation.

---

# Types of Users

## 1. Root User

The **Root User** is the administrator of the Linux system.

### Permissions

- Install or remove software
- Create or delete users
- Change system settings
- Access all files and directories
- Shutdown or restart the system

### Home Directory

```text
/root
```

Example:

```bash
whoami
```

Output:

```text
root
```

---

## 2. Normal User

A **Normal User** is created for everyday work.

### Permissions

- Create files
- Delete personal files
- Run applications

### Restrictions

- Cannot modify system files
- Cannot create users
- Cannot install system software without `sudo`

### Home Directory

```text
/home/username
```

Example:

```text
/home/haseeb
```

---

## 3. System User

A **System User** is created automatically for applications and services.

These users are not intended for human login.

Examples:

- `www-data`
- `mysql`
- `postgres`
- `daemon`
- `nobody`

System users allow applications to run securely with limited permissions instead of using the root account.

---

# Comparison

| User Type | Purpose | Home Directory |
|-----------|---------|----------------|
| Root User | System Administrator | `/root` |
| Normal User | Daily Work | `/home/username` |
| System User | Run Services & Applications | Usually none |

---

# Practice Commands

```bash
# Display current user
whoami

# Display user ID information
id

# Display all users
cat /etc/passwd

# Display only usernames
cut -d: -f1 /etc/passwd
```

---

# Key Takeaways

- Every action in Linux is performed by a user.
- Root user has complete control over the system.
- Normal users have limited permissions for daily work.
- System users are created for applications and services.
- Linux uses users to improve security and control access.