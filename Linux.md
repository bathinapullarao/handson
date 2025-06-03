# 🐧 Linux Hands-On Task List

This document contains essential Linux hands-on tasks to develop core command-line, scripting, user management, networking, and system administration skills.

---

## 🔧 Basic Commands and Navigation

### 1. File and Directory Management
- Create, delete, move, rename, and list files:
  ```bash
  mkdir demo_dir
  cd demo_dir
  touch file1.txt
  mv file1.txt file2.txt
  rm file2.txt
  ```

### 2. Explore the File System
- Use the following commands:
  ```bash
  ls -l
  pwd
  cd ..
  find /etc -name "hosts"
  ```

---

## 🧑‍💻 User and Permission Management

### 3. User and Group Management
- Create users and groups:
  ```bash
  sudo adduser devuser
  sudo groupadd devgroup
  sudo usermod -aG devgroup devuser
  ```

### 4. File Permissions
- Change file permissions and ownership:
  ```bash
  chmod 755 script.sh
  chown devuser:devgroup script.sh
  ```

---

## 📁 File Editing and Search

### 5. Use Text Editors
- Edit files using `nano`, `vim`, or `vi`

### 6. Search Inside Files
- Use `grep` and `awk`:
  ```bash
  grep "search" file.txt
  awk '{print $1}' file.txt
  ```

---

## 🖥️ Process and Package Management

### 7. Monitor Processes
- Use:
  ```bash
  top
  ps aux | grep nginx
  kill -9 <PID>
  ```

### 8. Install and Remove Packages
- Debian-based (Ubuntu):
  ```bash
  sudo apt update
  sudo apt install nginx
  sudo apt remove nginx
  ```

- RHEL-based:
  ```bash
  sudo yum install httpd
  sudo yum remove httpd
  ```

---

## 📡 Networking Tasks

### 9. Networking Commands
- Use:
  ```bash
  ifconfig
  ip a
  ping google.com
  netstat -tuln
  ss -tuln
  ```

### 10. Firewall Management
- Ubuntu:
  ```bash
  sudo ufw enable
  sudo ufw allow 22
  sudo ufw status
  ```

- CentOS:
  ```bash
  sudo systemctl start firewalld
  sudo firewall-cmd --add-port=22/tcp --permanent
  sudo firewall-cmd --reload
  ```

---

## 📜 Bash Scripting

### 11. Write a Basic Shell Script
- Create and run a script:
  ```bash
  #!/bin/bash
  echo "Hello, World!"
  ```

### 12. Automate with Loops and Conditions
- Use if-else, loops:
  ```bash
  for i in 1 2 3; do
    echo "Loop $i"
  done
  ```

---

## 🗃️ Archive and Compression

### 13. Archive Files
- Use:
  ```bash
  tar -cvf archive.tar file1 file2
  gzip archive.tar
  ```

---

## 🧠 Advanced Topics

### 14. Cron Jobs
- Schedule jobs:
  ```bash
  crontab -e
  # Add: * * * * * echo "Hello from cron" >> /tmp/cronlog.txt
  ```

### 15. System Logs and Journal
- View logs:
  ```bash
  tail -f /var/log/syslog
  journalctl -xe
  ```

---

## ☁️ Linux in Cloud VMs

### 16. Connect to a Linux VM via SSH
- Use:
  ```bash
  ssh user@server_ip
  ```

### 17. Set Up a Web Server
- Install and start:
  ```bash
  sudo apt install apache2
  sudo systemctl start apache2
  ```

---
