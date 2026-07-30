# 📄 File Viewing and Editing in Linux

## 📌 Learning Objectives

In this chapter, you will learn:

- How to view file contents
- Different ways to read large files
- How to edit files using Nano and Vim
- How to write and append text to files
- The difference between `>` and `>>`

---

# 🤔 Why Do We Need File Viewing Commands?

Files in Linux can contain:

- Configuration settings
- Source code
- Application logs
- User data
- Scripts

Before modifying a file, we usually need to **view its contents**.

Linux provides multiple commands depending on the size and purpose of the file.

---

# 📖 Viewing Files

## 1. `cat`

The `cat` command displays the **entire contents** of a file.

### Syntax

```bash
cat filename
```

### Example

```bash
cat notes.txt
```

### Example Output

```text
Linux
Docker
Kubernetes
```

### When to Use

- Small files
- Quick viewing
- Displaying file contents in the terminal

---

## 2. `tac`

The `tac` command displays the file **from the last line to the first line**.

### Syntax

```bash
tac filename
```

### Example

```bash
tac notes.txt
```

### Example Output

```text
Kubernetes
Docker
Linux
```

### When to Use

Useful when the latest information is stored at the bottom of a file.

---

## 3. `less`

The `less` command allows you to **view large files page by page**.

### Syntax

```bash
less filename
```

### Example

```bash
less system.log
```

### Useful Keys

| Key | Action |
|------|--------|
| ↑ ↓ | Scroll Up/Down |
| Space | Next Page |
| b | Previous Page |
| /word | Search Text |
| q | Quit |

### When to Use

Large log files or configuration files.

---

## 4. `more`

The `more` command also displays files page by page.

### Syntax

```bash
more filename
```

### Example

```bash
more notes.txt
```

### Difference from `less`

- Can only move forward.
- Less powerful than `less`.

---

## 5. `head`

Displays the **first 10 lines** of a file.

### Syntax

```bash
head filename
```

### Example

```bash
head notes.txt
```

Display only the first 5 lines:

```bash
head -n 5 notes.txt
```

### When to Use

Checking the beginning of a large file.

---

## 6. `tail`

Displays the **last 10 lines** of a file.

### Syntax

```bash
tail filename
```

### Example

```bash
tail notes.txt
```

Display the last 5 lines:

```bash
tail -n 5 notes.txt
```

### Monitor a File in Real Time

```bash
tail -f application.log
```

Press **Ctrl + C** to stop monitoring.

### When to Use

Monitoring application or server log files.

---

# ✏️ Editing Files

## 7. Nano Editor

Nano is a simple text editor suitable for beginners.

### Open a File

```bash
nano notes.txt
```

### Common Shortcuts

| Shortcut | Action |
|-----------|--------|
| Ctrl + O | Save |
| Ctrl + X | Exit |
| Ctrl + K | Cut Line |
| Ctrl + U | Paste Line |

---

## 8. Vim Editor

Vim is a powerful text editor widely used by Linux administrators and DevOps engineers.

### Open a File

```bash
vim notes.txt
```

### Basic Commands

| Command | Action |
|----------|--------|
| i | Enter Insert Mode |
| Esc | Exit Insert Mode |
| :w | Save |
| :q | Quit |
| :wq | Save and Quit |
| :q! | Quit Without Saving |

---

# 📝 Writing Text to a File

## 9. `echo`

The `echo` command prints text to the terminal or writes it to a file.

### Display Text

```bash
echo "Hello Linux"
```

Output

```text
Hello Linux
```

---

## Overwrite a File (`>`)

The `>` operator **replaces** the existing contents of a file.

### Example

```bash
echo "Linux" > notes.txt
```

Contents of `notes.txt`

```text
Linux
```

If the file already contained data, it is **deleted** and replaced.

---

## Append to a File (`>>`)

The `>>` operator adds new text **without deleting** existing content.

### Example

```bash
echo "Docker" >> notes.txt
```

Contents of `notes.txt`

```text
Linux
Docker
```

---

# 🔄 Difference Between `>` and `>>`

| Operator | Description |
|-----------|-------------|
| `>` | Overwrites the file |
| `>>` | Appends text to the file |

---

# 📊 Command Summary

| Command | Description |
|----------|-------------|
| `cat file` | Display the entire file |
| `tac file` | Display the file in reverse |
| `less file` | View a file page by page |
| `more file` | View a file page by page (forward only) |
| `head file` | Display the first 10 lines |
| `head -n 5 file` | Display the first 5 lines |
| `tail file` | Display the last 10 lines |
| `tail -n 5 file` | Display the last 5 lines |
| `tail -f file` | Monitor a file in real time |
| `nano file` | Open Nano editor |
| `vim file` | Open Vim editor |
| `echo "text"` | Display text |
| `echo "text" > file` | Write text (overwrite) |
| `echo "text" >> file` | Append text |

---

# 💻 Practice Lab

## Create a File

```bash
touch notes.txt
```

## Open the File

```bash
nano notes.txt
```

Write a few lines and save the file.

---

## Practice Commands

```bash
cat notes.txt

tac notes.txt

head notes.txt

head -n 3 notes.txt

tail notes.txt

tail -n 3 notes.txt

less notes.txt

more notes.txt

echo "Linux" > test.txt

cat test.txt

echo "Docker" >> test.txt

cat test.txt
```

---

# 🎯 Interview Questions

### 1. What is the difference between `cat` and `less`?

- `cat` displays the entire file at once.
- `less` allows scrolling through large files.

---

### 2. What is the difference between `head` and `tail`?

- `head` displays the beginning of a file.
- `tail` displays the end of a file.

---

### 3. What is the difference between `>` and `>>`?

- `>` overwrites the existing file.
- `>>` appends data to the end of the file.

---

### 4. Which editor is recommended for beginners?

**Nano** is recommended because it is simple and easy to use.

---

### 5. Which editor is commonly used by Linux administrators?

**Vim** is the most commonly used editor for Linux administration and DevOps.

---

# 📝 Key Takeaways

- Use `cat` for small files.
- Use `less` for large files.
- Use `head` and `tail` to view specific parts of a file.
- Use `tail -f` to monitor log files in real time.
- Use Nano for simple editing.
- Learn Vim for professional Linux administration.
- `>` overwrites a file, while `>>` appends data.