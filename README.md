# 🐧 **Linux Command Reference & Learning Guide**

*A structured collection of Linux commands, challenges, and concepts for beginners to advanced users.*

---

## **📌 Table of Contents**
1. [Learning Resources](#learning-resources)
2. [Command Manuals](#command-manuals)
3. [System Information](#system-information)
4. [User & Process Management](#user-process-management)
5. [Text Processing](#text-processing)
6. [System Monitoring](#system-monitoring)
7. [File Search with `find`](#file-search)
8. [Understanding Linux Links](#linux-links)

---

## **🎓 Learning Resources** <a name="learning-resources"></a>

### **Interactive Challenges**
| Resource | Description | Link |
|----------|-------------|------|
| **Bandit Wargame** | Level-based Linux command challenges | [overthewire.org/wargames/bandit](https://overthewire.org/wargames/bandit/) |
| **Linux Upskill** | Structured Linux learning path | [linuxupskillchallenge.org](https://linuxupskillchallenge.org/01/) |
| **LabEx** | Hands-on Linux labs with exercises | [labex.io/linuxjourney](https://labex.io/linuxjourney) |

### **Study Materials**
| Resource | Description | Link |
|----------|-------------|------|
| **CommandLineFu** | Complex command line examples | [commandlinefu.com](https://www.commandlinefu.com/commands/browse) |
| **LFCS Study Guide** | Medium article for certification prep | [medium.com/LFCS](https://medium.com/@wattsdave/linux-foundation-certified-systems-administrator-lfcs-navigating-the-study-journey-for-the-lfcs-06d9e2aa5165) |
| **GitLab Notes** | LFCS study notes repository | [gitlab.com/lfcs-notes](https://gitlab.com/daveopspublic/lfcs-study-notes) |
| **GitHub Docs** | LFCS examples and docs | [github.com/lfcs-docs](https://github.com/cloudchristina/lfcs/tree/main) |
| **Practice Tests** | LFCS exam questions | [theexamslab.com/LFCS](https://www.theexamslab.com/online/LFCS-practice-test) |

---

## **📚 Command Manuals** <a name="command-manuals"></a>

| Command | Description | Example |
|---------|-------------|---------|
| `man <command>` | Detailed manual pages | `man ls` |
| `info <command>` | In-depth documentation | `info coreutils` |
| `<command> --help` | Quick help summary | `grep --help` |

---

## **💻 System Information** <a name="system-information"></a>

| Command | Description | Example Output |
|---------|-------------|----------------|
| `hostname` | System's hostname | `my-pc` |
| `uname -a` | Kernel and system info | `Linux my-pc 5.15.0-86-generic...` |
| `whoami` | Current username | `zied` |

---

## **👤 User & Process Management** <a name="user-process-management"></a>

| Command | Description | Example Output |
|---------|-------------|----------------|
| `w` | Logged-in users and processes | `USER TTY FROM LOGIN@ IDLE...` |

---

## **📝 Text Processing** <a name="text-processing"></a>

| Command | Description | Example |
|---------|-------------|---------|
| `cut` | Extract specific columns | `cut -d',' -f1 file.csv` |
| `cat` | Display file content | `cat file.txt` |
| `grep` | Search for patterns | `grep "error" log.txt` |

---

## **📊 System Monitoring** <a name="system-monitoring"></a>

| Command | Description | Example Output |
|---------|-------------|----------------|
| `uptime` | System uptime and load | `12:34:56 up 2 days, 3 users...` |

---

## **🔍 File Search with `find`** <a name="file-search"></a>

### **Basic Searches**
| Command | Description | Example |
|---------|-------------|---------|
| `find [path] -name "filename"` | Case-sensitive search | `find /bin/ -name "file1.txt"` |
| `find -iname "filename"` | Case-insensitive search | `find -iname "felix"` |
| `find -name "pattern"` | Wildcard search | `find -name "f*"` |

### **Intermediate Searches**
| Type | Command | Example |
|------|---------|---------|
| **Time-based** | `find -mmin [-/+]n` | `find -mmin -5` (last 5 mins) |
| **Size-based** | `find -size [+-]n[c/k/M/G]` | `find -size +512k` |
| **Logical** | `find -name "A" -o -name "B"` | `find -name "f*" -o -size 512k` |

### **Advanced Searches**
| Type | Command | Example |
|------|---------|---------|
| **Permissions** | `find -perm 664` | `find -perm -4000` (SUID) |
| **Actions** | `find -exec cmd {} \;` | `find -name "*.tmp" -exec rm {} \;` |
| **Edge Cases** | `find -type f` | `find /opt/ -type f -size +1M` |

### **Practical Use Cases**
```bash
# Find and delete files >100MB
find /home -type f -size +100M -delete

# Locate SUID binaries
find / -perm -4000 -type f -exec ls -l {} \;

# Find modified files in last hour
find /var/log -mmin -60
