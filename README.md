# Linux

### 📌 **What is Bandit?**
[**Bandit**](https://overthewire.org/wargames/bandit/) is a **war game** designed to teach **Linux command-line skills** through **level-based challenges**.

to read
<a href="https://linuxupskillchallenge.org/01/">Linux challenges to read</a>

to practice with lab labex

<a href="https://labex.io/linuxjourney">big cource with lab labex </a>

Search for a strange or complex command line:
<a href="https://www.commandlinefu.com/commands/browse">complex cammand line</a>

## **Command Manuals** <a name="command-manuals"></a>
Commands to access detailed documentation.
   Command               | Description                                                                 | Example                          |
 |-----------------------|-----------------------------------------------------------------------------|----------------------------------|
 | `man <command>`       | Displays the **manual page** (detailed documentation) for a command.       | `man ls`                         |
 | `info <command>`      | Provides **in-depth info** (often more detailed than `man`).                | `info coreutils`                 |
 | `<command> --help`    | Shows a **quick help summary** of options and usage.                       | `grep --help`                    |

---

## **System Information** <a name="system-information"></a>
Commands to inspect system details.
 | Command               | Description                                                                 | Example Output                   |
 |-----------------------|-----------------------------------------------------------------------------|----------------------------------|
 | `hostname`            | Displays the **system’s hostname**.                                         | `my-pc`                          |
 | `uname -a`            | Shows **kernel version**, OS, and hardware details.                         | `Linux my-pc 5.15.0-86-generic...` |
 | `whoami`              | Prints the **current logged-in username**.                                  | `zied`                           |

---

## **User & Process Management** <a name="user--process-management"></a>
Monitor users and processes.
 | Command | Description                                                                 | Example Output                   |
 |---------|-----------------------------------------------------------------------------|----------------------------------|
 | `w`     | Lists **logged-in users** and their active processes (CPU, memory, etc.).  | `USER TTY FROM LOGIN@ IDLE...`   |

---

## **Text Processing** <a name="text-processing"></a>
Tools for manipulating text files.
 | Command               | Description                                                                 | Example                          |
 |-----------------------|-----------------------------------------------------------------------------|----------------------------------|
 | `cut`                 | Extracts **specific columns** from files (e.g., CSV).                      | `cut -d',' -f1 file.csv`         |
 | `cat`                 | **Concatenates** and displays file content.                                | `cat file.txt`                   |
 | `grep`                | Searches for **patterns** in files (supports regex).                       | `grep "error" log.txt`           |

---

## **System Monitoring** <a name="system-monitoring"></a>
Check system uptime and performance.
 | Command   | Description                                                                 | Example Output                   |
 |-----------|-----------------------------------------------------------------------------|----------------------------------|
 | `uptime`  | Shows **how long the system has been running** and load averages.          | `12:34:56 up 2 days, 3 users...` |

---



# 🔍 **Linux `find` Command: Mastering File Search**

A **comprehensive guide** to the `find` command, from basic searches to advanced filtering, permissions, and actions.

---

## **Table of Contents**
1. [Basic Searches](#basic-searches)
2. [Intermediate: Time, Size, and Logical Operators](#intermediate)
3. [Advanced: Permissions, Actions, and Edge Cases](#advanced)
4. [Practical Use Cases](#use-cases)
5. [Performance Tips](#performance)

---

## **📂 Basic Searches** <a name="basic-searches"></a>
Fundamental `find` syntax and simple filters.

| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find [path] -name "filename"`   | Search by **exact name** (case-sensitive).   | `find /bin/ -name "file1.txt"`           |
| `find -name "filename"`          | Search in **current directory**.            | `find -name "file.txt"`                  |
| `find -iname "filename"`         | **Case-insensitive** search.                 | `find -iname "felix"`                    |
| `find -name "pattern"`           | Use **wildcards** (`*`, `?`).               | `find -name "f*"`                        |

---

## **⚙ Intermediate: Time, Size, and Logical Operators** <a name="intermediate"></a>
Filter by time, size, and combine conditions.

### **Time-Based Searches**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -mmin [-/+]n`              | Modified **`n` minutes ago** (`-` = within, `+` = older). | `find -mmin -5` (last 5 mins)            |
| `find -mtime n`                  | Modified **`n` days ago** (24-hour periods). | `find -mtime 2` (exactly 2 days ago)     |
| `find -cmin n`                   | Changed **status** `n` minutes ago.          | `find -cmin 5`                           |

### **Size-Based Searches**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -size n[c/k/M/G]`          | Files of **exact size** (`c`=bytes, `k`=KB). | `find -size 512k`                       |
| `find -size +n`                  | Files **larger than** `n`.                   | `find -size +512k`                      |
| `find -size -n`                  | Files **smaller than** `n`.                  | `find -size -512k`                      |

### **Logical Operators**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -name "A" -o -name "B"`    | **OR** operator (match either).              | `find -name "f*" -o -size 512k`         |
| `find -name "A" -a -name "B"`    | **AND** operator (default, match both).     | `find -name "f*" -size 512k`            |
| `find \! -name "A"`              | **NOT** operator (exclude).                  | `find \! -name "f*"`                     |

---

## **🔐 Advanced: Permissions, Actions, and Edge Cases** <a name="advanced"></a>
Deep dives into permissions, execution, and complex queries.

### **Permission-Based Searches**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -perm 664`                 | **Exact permissions** (e.g., `rw-rw-r--`).   | `find -perm 664`                         |
| `find -perm -664`                | **At least** these permissions (e.g., `777` matches). | `find -perm -664`          |
| `find -perm /664`                | **Any of** these permissions (e.g., `600` or `064`). | `find -perm /664`         |
| `find -perm -u=s`                | **SUID bit** set (executable as owner).      | `find -perm -4000`                        |
| `find \! -perm -o=r`             | Others **cannot read**.                      | `find \! -perm /o=r`                      |
| `find -perm -g=w \! -perm /o=rw` | Group **can write**, others **cannot read/write**. | `find /var/log/ -perm -g=w \! -perm /o=rw` |

### **Actions and Execution**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -exec cmd {} \;`           | **Execute command** on results (`{}` = filename, `\;` terminates). | `find -name "*.tmp" -exec rm {} \;` |
| `find -exec cmd {} +`            | **Batch process** (faster for many files).  | `find -name "*.log" -exec cat {} +`     |
| `find -delete`                   | **Delete** matched files (caution!).         | `find -name "*.bak" -delete`            |

### **Edge Cases**
| Command                          | Description                                  | Example                                  |
|----------------------------------|----------------------------------------------|------------------------------------------|
| `find -type f`                   | **Files only** (exclude directories).        | `find /opt/ -type f -size +1M`           |
| `find -type d`                   | **Directories only**.                        | `find -type d -name "temp*"`             |
| `find -regex "pattern"`          | **Regex matching** (full path).              | `find -regex ".*\.\(txt\|md\)$"`         |
| `find -path "*/cache/*"`         | **Path-based filtering**.                    | `find -path "*/tmp/*" -delete`          |

---

## **💡 Practical Use Cases** <a name="use-cases"></a>
Real-world scenarios with `find`.

| **Scenario**                     | **Command**                                  |
|----------------------------------|----------------------------------------------|
| Find and delete files >100MB.    | `find /home -type f -size +100M -delete`     |
| Locate SUID binaries (security). | `find / -perm -4000 -type f -exec ls -l {} \;` |
| Find modified files in last hour.| `find /var/log -mmin -60`                    |
| Count files >20MB in `/var`.    | `sudo find /var -type f -size +20M \| wc -l` |
| Copy files between 5MB–10MB.     | `find /usr -type f -size +5M -size -10M -exec cp {} /backup/ \;` |

---

## **⚡ Performance Tips** <a name="performance"></a>
Optimize `find` for speed and efficiency.

1. **Limit Search Depth**:
   ```bash
   find -maxdepth 2 -name "*.conf"  # Only search 2 subdirectories deep.

