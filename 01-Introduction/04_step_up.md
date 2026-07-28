# 🖥️ Setting Up a Linux Environment

## 📖 Introduction

Before learning Linux, you need a Linux environment where you can safely practice commands.

There are several ways to run Linux on your computer:

- ☁️ Cloud Virtual Machine (AWS, Azure, GCP)
- 🖥️ VirtualBox
- 💻 VMware
- 🪟 WSL2 (Windows only)
- 🐳 Docker (Recommended)
- 🍎 Multipass (macOS)

For this course, we will use **Docker** because it is lightweight, fast, easy to set up, and widely used in the DevOps industry.

---

# 🚀 Why Docker?

Docker allows you to run Linux inside an isolated environment called a **container**.

### Advantages

- ✅ Easy to install
- ✅ Lightweight
- ✅ Fast startup
- ✅ No dual boot required
- ✅ No virtual machine required
- ✅ Safe to experiment
- ✅ Industry standard for DevOps and Cloud

---

# 🛠️ Step 1: Install Docker Desktop

Download Docker Desktop from the official website.

### Windows & macOS

https://www.docker.com/products/docker-desktop/

After installation:

1. Open Docker Desktop.
2. Sign in to your Docker account (optional but recommended).
3. Wait until Docker Engine shows **Running**.

---

# 📂 Step 2: Create a Folder for Persistent Data

Docker containers are temporary.

To keep your files even after restarting the container, create a folder on your computer.

## macOS / Linux

```bash
mkdir -p ~/ubuntu-data
```

## Windows (PowerShell)

```powershell
mkdir C:\Users\YourUsername\Downloads\ubuntu-data
```

Replace **YourUsername** with your Windows username.

---

# 🐧 Step 3: Run Ubuntu Container

## macOS / Linux

```bash
docker run -dit \
  --name ubuntu-container \
  --hostname ubuntu-dev \
  --restart unless-stopped \
  --cpus="2" \
  --memory="4g" \
  --mount type=bind,source=$HOME/ubuntu-data,target=/data \
  -p 2222:22 \
  -p 8080:80 \
  --env TZ=Asia/Karachi \
  --env LANG=en_US.UTF-8 \
  ubuntu:24.04 \
  /bin/bash
```

---

## Windows (PowerShell)

```powershell
docker run -dit `
  --name ubuntu-container `
  --hostname ubuntu-dev `
  --restart unless-stopped `
  --cpus="2" `
  --memory="4g" `
  --mount type=bind,source="C:\Users\YourUsername\Downloads\ubuntu-data",target=/data `
  -p 2222:22 `
  -p 8080:80 `
  --env TZ=Asia/Karachi `
  --env LANG=en_US.UTF-8 `
  ubuntu:24.04 `
  /bin/bash
```

---

# 📖 Step 4: Understanding the Docker Command

| Option | Description |
|---------|-------------|
| `-dit` | Runs the container in detached, interactive, and terminal mode. |
| `--name ubuntu-container` | Gives the container a name. |
| `--hostname ubuntu-dev` | Sets the hostname inside Ubuntu. |
| `--restart unless-stopped` | Automatically restarts the container after system reboot. |
| `--cpus="2"` | Allocates 2 CPU cores. |
| `--memory="4g"` | Allocates 4 GB RAM. |
| `--mount` | Mounts a folder from your computer into the container. |
| `-p 2222:22` | Maps SSH port. |
| `-p 8080:80` | Maps HTTP port. |
| `--env TZ=Asia/Karachi` | Sets the timezone. |
| `--env LANG=en_US.UTF-8` | Sets the language. |
| `ubuntu:24.04` | Downloads and runs Ubuntu 24.04 LTS. |
| `/bin/bash` | Starts the Bash shell. |

---

# ▶️ Step 5: Enter the Ubuntu Container

Open a terminal and run:

```bash
docker exec -it ubuntu-container bash
```

You should now see:

```bash
root@ubuntu-dev:/#
```

Congratulations! 🎉

You are now inside Ubuntu Linux.

---

# ✅ Step 6: Verify Your Installation

Run the following commands:

```bash
pwd
whoami
hostname
cat /etc/os-release
uname -a
```

Example Output

```text
/

root

ubuntu-dev

Ubuntu 24.04.4 LTS

Linux ubuntu-dev ...
```

---

# 🚪 Step 7: Exit Ubuntu

To leave Ubuntu without stopping it:

```bash
exit
```

The container will continue running in the background.

---

# ▶️ Step 8: Open Ubuntu Again

Whenever you want to continue learning Linux:

```bash
docker exec -it ubuntu-container bash
```

---

# ⏹️ Step 9: Stop Ubuntu

If you're finished for the day:

```bash
docker stop ubuntu-container
```

---

# ▶️ Step 10: Start Ubuntu Again

```bash
docker start ubuntu-container
```

Then enter the container:

```bash
docker exec -it ubuntu-container bash
```

---

# 🗑️ Step 11: Delete the Container

If you no longer need it:

```bash
docker rm -f ubuntu-container
```

> **Warning:** This permanently deletes the container. Files stored outside the mounted folder will be lost.

---

# 📋 Docker Commands Cheat Sheet

| Command | Description |
|---------|-------------|
| `docker ps` | Show running containers |
| `docker ps -a` | Show all containers |
| `docker start ubuntu-container` | Start the container |
| `docker stop ubuntu-container` | Stop the container |
| `docker restart ubuntu-container` | Restart the container |
| `docker exec -it ubuntu-container bash` | Open Ubuntu terminal |
| `exit` | Exit Ubuntu |
| `docker rm -f ubuntu-container` | Delete the container |

---

# 💡 Best Practices

- Always stop the container when you finish your work.
- Use `exit` to leave Ubuntu.
- Store important files inside the mounted folder.
- Keep Docker Desktop running while using Ubuntu.
- Run `apt update` regularly to get the latest package information.

---

# 📝 Summary

In this chapter, you learned how to:

- Install Docker Desktop
- Create an Ubuntu Linux environment
- Understand the Docker run command
- Access the Ubuntu container
- Verify the Linux installation
- Start, stop, and remove the container
- Manage your Linux environment safely

You now have a fully functional Ubuntu environment ready for learning Linux, Cloud, and DevOps.
