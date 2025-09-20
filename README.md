# Linux

### 📌 **What is Bandit?**
[**Bandit**](https://overthewire.org/wargames/bandit/) is a **war game** designed to teach **Linux command-line skills** through **level-based challenges**.
Each level is a puzzle that requires using commands like `ssh`, `grep`, `find`, `cat`, and more to progress.


to read
<a href="https://linuxupskillchallenge.org/01/">Linux challenges to read</a>

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

## **Usage Examples**
### 1. Filter Logs with `grep`
```bash
grep "ERROR" /var/log/syslog  # Find all error entries in syslog.
