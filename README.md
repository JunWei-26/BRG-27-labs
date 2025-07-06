# BRG-27 - Introduction to Server Environments and Architecture (ISEA)

## 📌 Overview

This repository documents my learning journey in the BRG-27 course, focusing on server environments, Linux fundamentals, cloud deployment, system automation, and basic web hosting. The labs are performed using both VirtualBox and AWS EC2.
---

## Getting Started with GitHub

- Created GitHub account: https://github.com
- Created repository: `JunWei26-BRG-27-labs`
- Added `README.md` to document all lab activities
- Used Git to track changes and organize lab progress

---

## Ubuntu Setup in VirtualBox

**Steps:**
- Downloaded Ubuntu ISO from https://ubuntu.com/download/desktop
- Downloaded VirtualBox from https://www.virtualbox.org/wiki/Downloads
- VM Specs:
  - RAM: 10 GB
  - Disk Space: 20 GB

**Observations:**
- Allocating more RAM (10 GB) improved VM performance
- GUI interface makes it easier to explore Ubuntu features

---

## Basic Linux Command Practice

| Command        | Purpose                                 |
|----------------|------------------------------------------|
| `pwd`          | Show current directory                   |
| `ls`           | List files and directories               |
| `ls -la`       | List all files with details (including hidden) |
| `ls -lah`      | Human-readable sizes                     |
| `cd`           | Change directory                         |
| `mkdir`        | Create a new directory                   |
| `touch`        | Create a new empty file                  |
| `cat`          | Show content of a file                   |
| `nano`, `gedit`| Text editors (CLI/GUI)                   |
| `cp`, `mv`     | Copy and move files                      |
| `ps -e`, `top` | Monitor running processes                |

**System Monitoring Tools:**
- `top` for real-time performance
- `1` (inside `top`) shows per-CPU usage

---

## Understanding File Permissions with `chmod`

**Types of Users:**
- **u**: owner
- **g**: group
- **o**: others

**Permission Codes:**

| Digit | Binary | Symbol | Description           |
|-------|--------|--------|------------------------|
| 0     | 000    | ---    | No access              |
| 1     | 001    | --x    | Execute only           |
| 2     | 010    | -w-    | Write only             |
| 3     | 011    | -wx    | Write + Execute        |
| 4     | 100    | r--    | Read only              |
| 5     | 101    | r-x    | Read + Execute         |
| 6     | 110    | rw-    | Read + Write           |
| 7     | 111    | rwx    | Read + Write + Execute |

**Examples:**

```bash
chmod 755 script.sh     # Owner: rwx, Group: r-x, Others: r-x
chmod 644 document.txt  # Owner: rw-, Group: r--, Others: r--
chmod 777 file          # Full access (insecure)
chmod 700 file          # Owner full access only
Networking and DNS Tools
Useful Commands:
nslookup: Get IP/domain information

whois: Check domain ownership details

IP Addressing:
Private IP: Internal use only (e.g., 192.168.x.x)

Public IP: Globally reachable

127.0.0.1: Loopback (this machine)

Analogy:

Public IP = Street address

Private IP = Room number in house

NAT = Mail sorting

Cloud Deployment with AWS EC2
Instance Details:
EC2 Free Tier (t2.micro)

SSH Key Pair for secure login

SSH Access:
Used Git Bash with the following command:

bash
Copy
Edit
ssh -i key.pem ubuntu@<public-ip>
Challenges:
Initially blocked by incorrect security group rules

Solved by opening ports 22 (SSH) and 80 (HTTP)

Firewall Configuration with UFW
Commands:
bash
Copy
Edit
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose
Why it's important:

Reduces exposure to attacks

Only essential services are reachable

Prevents unnecessary open ports

Creating a Free Domain with DuckDNS
Registered free domain:
http://junweiec2website.duckdns.org/

Set up DuckDNS auto-update using cron to handle dynamic IP

Automation with Crontab
What is crontab?
Linux scheduler to run tasks at specified times.

Daily System Update Example:
bash
Copy
Edit
0 0 * * * sudo apt update && sudo apt upgrade -y
Benefits:

Automatic patching

Reduce manual effort

Avoid human errors

Improved security posture

System Auditing and Login History
Check Logins:
bash
Copy
Edit
last -F -s -1days
Audit Crontab Entry:
bash
Copy
Edit
0 1 * * * last -F -s -1days >> /var/log/login-audit.log
Why it's important:

Detect unauthorized access

Track user sessions

Spot suspicious activity

Final Reflection
Successfully migrated from VirtualBox to AWS EC2 for better cloud experience

Deployed a basic HTML website with styling and JavaScript

Secured the VM using UFW and SSH best practices

Practiced automation and monitoring using crontab

Learned how to manage users, file permissions, and network services in Linux
