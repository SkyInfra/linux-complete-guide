# Process Management in Linux

## What is a Process?

A **process** is an instance of a running program.

Whenever you execute a command or start an application, Linux creates a process to perform that task.

Examples:

- Running `sleep 300`
- Opening `vim`
- Running a Python application
- Starting an Nginx web server

Each process has its own:

- Process ID (PID)
- Parent Process ID (PPID)
- Priority
- Owner
- Memory allocation
- CPU usage

---

# Why is Process Management Important?

Linux systems often run hundreds of processes simultaneously.

Process management helps administrators:

- Monitor system performance
- Identify high CPU or memory usage
- Stop unresponsive programs
- Run long tasks in the background
- Change process priority
- Keep services running

---

# Process Lifecycle

```text
Program
   │
   ▼
Process Created
   │
   ▼
Running
   │
   ├── Running in Foreground
   ├── Running in Background
   ├── Paused
   ├── Resumed
   └── Terminated
```

---

# Viewing Processes

## View Running Processes

```bash
ps
```

Displays processes running in the current terminal.

---

## View All Running Processes

```bash
ps aux
```

Shows every running process on the system.

---

## View Processes for a Specific User

```bash
ps -u username
```

Example:

```bash
ps -u root
```

---

## Find a Process by Name

```bash
ps -C process_name
```

Example:

```bash
ps -C nginx
```

---

# Finding Process IDs

## pgrep

Searches for a process by name and returns its PID.

```bash
pgrep nginx
```

Useful options:

```bash
pgrep -l nginx
```

Shows PID and process name.

```bash
pgrep -u root
```

Search processes owned by a specific user.

```bash
pgrep -f python
```

Search using the complete command line.

---

## pidof

Returns the PID of a running program.

```bash
pidof nginx
```

---

### pgrep vs pidof

| pgrep | pidof |
|--------|--------|
| More flexible | Simpler |
| Search by user | Search only by executable name |
| Search full command line | No |
| Preferred for scripting | Mostly used for quick PID lookup |

---

# Monitoring Processes

## top

Interactive process monitoring tool.

```bash
top
```

Displays:

- CPU usage
- Memory usage
- Running processes
- Process priorities
- Process IDs

Useful keys inside `top`:

| Key | Action |
|------|--------|
| q | Quit |
| P | Sort by CPU usage |
| M | Sort by Memory usage |
| k | Kill a process |
| r | Renice a process |

---

# Terminating Processes

## kill

Gracefully terminates a process.

```bash
kill PID
```

Example:

```bash
kill 2450
```

Sends the **SIGTERM** signal.

---

## Force Kill

```bash
kill -9 PID
```

Example:

```bash
kill -9 2450
```

Sends **SIGKILL**.

Use only when a process does not terminate normally.

---

## pkill

Kill processes using their name.

```bash
pkill nginx
```

Force kill:

```bash
pkill -9 nginx
```

---

# Process Signals

Linux communicates with processes using signals.

| Signal | Number | Purpose |
|----------|---------|----------|
| SIGINT | 2 | Interrupt (Ctrl + C) |
| SIGTERM | 15 | Graceful termination |
| SIGKILL | 9 | Force kill |
| SIGSTOP | 19 | Stop process |
| SIGCONT | 18 | Continue process |

---

# Foreground and Background Jobs

## Run in Background

```bash
sleep 300 &
```

The terminal becomes free while the process continues running.

---

## List Background Jobs

```bash
jobs
```

Example:

```text
[1]+ Running sleep 300 &
```

---

## Bring Job to Foreground

```bash
fg %1
```

`%1` refers to **Job Number 1**, not the PID.

---

## Pause a Process

Press:

```text
Ctrl + Z
```

The process is paused (stopped), not terminated.

---

## Resume in Background

```bash
bg %1
```

Resumes a paused job in the background.

---

# Keeping Processes Running

## nohup

Runs a command so it continues even after the terminal is closed.

```bash
nohup python app.py &
```

Output is written to:

```text
nohup.out
```

View the output:

```bash
cat nohup.out
```

---

# Process Priority

Linux assigns each process a **Nice Value (NI)**.

Range:

```text
-20 ............... 19
```

| Nice Value | Priority |
|-------------|----------|
| -20 | Highest |
| 0 | Default |
| 19 | Lowest |

Lower Nice Value = Higher Priority

---

## nice

Start a process with a specific priority.

```bash
nice -n 10 sleep 300
```

Starts the process with Nice Value **10**.

---

## renice

Change the priority of a running process.

```bash
renice -n 10 -p PID
```

Example:

```bash
renice -n 10 -p 2450
```

Verify using:

```bash
top
```

Look at the **NI** column.

---

# Daemon Processes

A **daemon** is a background process that provides a service continuously.

Examples:

- sshd
- nginx
- docker
- cron
- mysql

On a full Linux system managed by **systemd**, common commands include:

```bash
systemctl status ssh
```

```bash
systemctl start nginx
```

```bash
systemctl stop nginx
```

```bash
systemctl restart nginx
```

```bash
systemctl enable nginx
```

```bash
systemctl list-units --type=service
```

> **Note:** These commands usually do **not** work inside a standard Docker container because Docker containers typically do not run `systemd`.

---

# Common Commands Summary

| Command | Description |
|-----------|-------------|
| ps | Show running processes |
| ps aux | Show all processes |
| ps -u user | Show user processes |
| ps -C name | Find process by name |
| pgrep | Find PID by process name |
| pidof | Get PID of a program |
| top | Monitor system processes |
| kill PID | Gracefully terminate a process |
| kill -9 PID | Force kill a process |
| pkill name | Kill process by name |
| nice | Start process with custom priority |
| renice | Change running process priority |
| command & | Run command in background |
| jobs | Show background jobs |
| fg | Bring job to foreground |
| bg | Resume paused job in background |
| Ctrl + Z | Pause a running process |
| nohup | Keep process running after logout |

---

# Key Takeaways

- A process is a running instance of a program.
- Every process has a unique Process ID (PID).
- Use `ps` and `top` to monitor processes.
- Use `pgrep` or `pidof` to locate process IDs.
- Use `kill` or `pkill` to terminate processes.
- Use `&`, `jobs`, `fg`, `bg`, and `Ctrl + Z` for job control.
- Use `nohup` to keep processes running after closing the terminal.
- Use `nice` and `renice` to control process scheduling priority.
- Daemons are long-running background services that provide system functionality.