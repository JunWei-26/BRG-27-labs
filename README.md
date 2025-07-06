# BRG-27-labs
**#Install Ubuntu using VirtualBox.** 28/6/25
Configuring VM setting - OS: Ubuntu, RAM: 14GB, Storage: 20GB #Observation > Higher RAM allocated == smoother the VM will run 

**#Familiarity with Ubuntu Linux – Basic command line navigation and utilities.** 28/6/25
Practice using pwd, ls, cd, mkdir, and touch
| Command     | Purpose                                      |
|-------------|----------------------------------------------|
| pwd       | Show current working directory               |
| ls        | List files and directories                   |
| cd        | Change directory                             |
| mkdir     | Create a new directory                       |
| touch     | Create a new empty file                      |
| cat       | Command that shows what inside a file        |

#What I Observed: 
'pwd' : /home/ubuntu
'ls' : Desktop, Download, Pictures, Snap, Videos, Documents, Music, Public, Template
'cd' (Desktop) : ~/Desktop$
'mkdir' : mkdir *foldername* > cd *foldername* 
'touch' : touch *foldername* > ls *foldername* 
'cat' : (echo "This is a testfile" > testfile.txt) > cat testfile.txt : This is a testfile

**Understand directory structure (/etc, /var, /home).**
** Use SUDO (Admin priviledge) 
/etc - Stores system settings and configuration files (files in /etc controls how your system behave)
/var - stores data that changes while system is running 
/home - personal folder for all users on the system
/man stands for manual, it shows you detailed information about the command

**Linux Services – Understanding and managing background services.**
'systemctl list-units --type=service' - This command is used in Linux (systemd-based) systems like Ubuntu to list all active services running on your system.
'sudo systemctl start|stop [service]' - 


To begin the course, I created a GitHub account by signing up at https://github.com. I then created a new repository named JunWei26-BRG-27-labs, which I will use to document all my lab work throughout the course.



I added a “README.md” file to begin documenting each lab, including brief summaries, key commands used. This practice helped me stay organized and also improved my familiarity with Ubuntu OS and for upcoming lessons.

Installing Ubuntu OS on Oracle VirtualBox Manager (What I use initially)

https://ubuntu.com/download/desktop
https://www.virtualbox.org/wiki/Downloads






I downloaded the latest Ubuntu ISO from the official Ubuntu website and installed Oracle VirtualBox on my Windows laptop. I created a new virtual machine with the following settings:
RAM: 10 GB 



Disk space: 20 GB
I followed the guided installer in Ubuntu to complete the setup. The installation was mostly straightforward, but I had to allocate more RAM for my VM, as I was experiencing performance issues. Allocating 10 GB of RAM helps to resolve the issue.
Familiarising myself with Ubuntu Desktop Environment
 Trying out commands using terminal
Ps - e : This command lists all currently running processes on the system.

PID – Process ID
TTY (Teletypewriter) – Refers to terminal devices that users interact with
TIME – Amount of CPU time used
CMD – The command that launched the process

Then “Top”

This command launches a real-time interactive view of your system’s resource usage.

It’s like Task Manager in Windows, but in the terminal.
Then “1” 
Toggle the display of individual CPU cores.

When you press 1 inside the top command, it shows the usage of each CPU core separately.
This helps you:
See if one core is doing more work than the others


Check if your system is using all CPU cores properly


Find out if a process is putting too much load on a single core



Command “ls” and “ls -la”

The command “ls” shows files and folders name whereas the command “ls -la” shows more detailed info and files that are hidden.
	Breakdown:
-l: Long listing format (shows permissions, owner, size, date, etc.)


-a: Includes hidden files 



“touch testfile”
Creates an empty file called testfile








“gedit testfile” 
Opens a file in a graphical editor 



What's the difference between “gedit” and “nano”
gedit is a graphical text editor — it opens in a window, so it only works if your system has a desktop interface.


nano is a text-based editor — it works inside the terminal, so it's perfect for remote access or command-line only systems.
What's the difference between “cat testfile” and “less testfile”

 
Use cat when the file is small and you just want to quickly see everything. (Not scrollable)


Use less when the file is big and you want to read it comfortably. (Scrollable)

Difference between “cp” and “mv”



Use cp when you want to keep the original file and create a copy.


Use mv when you want to move or rename the file without keeping the original in the old place.






7) Command “ls-lah” 


Same as ls -la but with an extra -h:


-h: Human-readable file sizes — file sizes are shown with units like KB, MB, or GB, making them easier to understand.

“ls -lah” : 

“ls -la” : 



8) SuperUser (Root)

Adding a user as a non-root user. Results : Error


As a sudo user : Successful



What is NSLookup? 
nslookup (short for Name Server Lookup) is a command-line tool used to query DNS (Domain Name System) to find the IP address of a domain name or the domain name of an IP address.


What is whois command?
It is a command that tells you who owns a website or domain name.


It shows information like:


The company or person who registered the domain


When the domain was created and when it expires




Private and Public IP analogy: 
Private IP address (e.g., 192.168.x.x) is used inside your local network only. It’s not unique globally.
Public IP address is assigned to your home or office router by your ISP and is unique on the internet.
Your router uses a process called Network Address Translation (NAT) to allow multiple devices with private IPs to share one public IP.
Your private IP is like your house’s room number inside your home.
Your public IP is like your home’s street address on the entire planet.
Mail (internet data) goes to the street address (public IP), and your router delivers it to the right room (private IP).
127.0.0.1 = "this computer"
It’s a built-in address that always points to your own system — used for testing and self-communication.
Accessing 127.0.0.1 after installing Apache



UFW (Ubuntu Firewall)

“sudo ufw status verbose” - To show Ubuntu Firewall status , verbose means to show more information.



Testing out SSH to another user in the same VM


 by pressing exit , i will close the connection towards localhost.


Chmod - stands for "change mode" and is a Linux command used to change the permissions of files and directories.

Every file or directory in Linux has permissions that control:
Who can read it (r)


Who can write to it (w)


Who can execute it (x)


There are 3 types of users:
Owner (u) – the user who owns the file


Group (g) – users in the file's group


Others (o) – everyone else

Digit
Binary
Meaning
Permissions
0
000
---
No access
1
001
--x
Execute
2
010
-w-
Write
3
011
-wx
Write + Exec
4
100
r--
Read
5
101
r-x
Read + Exec
6
110
rw-
Read + Write
7
111
rwx
All perms








Each digit in a 3-digit number refers to:
[Owner][Group][Others]


chmod 755 script.sh   # Owner: rwx, Group: r-x, Others: r-x
chmod 644 document.txt  # Owner: rw-, Group: r--, Others: r--
chmod 777 file     # Everyone can read, write, and execute (not safe for sensitive files!)
chmod 700 file     # Only owner has full access
chmod 600 file     # Only owner can read/write (no execute)


Total ownership used in IT (Printer cost)





Cloud-based virtual machine - Using AWS Cloud Service EC2


Instance type
T2.micro (Free but however some settings are limited)



Key pair (login) for SSH use















SSH to EC2 instances using SSH Key and GitBash



Problems I faced initially are networking problems, such as blocking HTTP port 80 and SSH port 22 in the security rule


Initially I was using VirtualBox however I ran into some configuration problems, such as GuestOS wasn't installed correctly. After troubleshooting, I decided to improvise and use GitBash instead to SSH into my AWS EC2 Domain.

I will now proceed to create my own website with the tools that I have and what I have learned throughout the lessons. 



Hosting my own DNS using DuckDNS (http://junweiec2website.duckdns.org/)

Adding crontab to check and update my system everyday at 00:00



What is crontab? It stands for cron table, and it’s a Linux feature that allows you to schedule tasks run automatically at specific times or intervals that you set. It is like a task scheduler.

Why is it good to automate your update in your system (Using crontabs)
It helps to protect your website/server from known vulnerabilities or zero-day exploits
Helps with bug fixes
Automation helps to save time hence lesser manpower is needed
Consistency, lesser human errors (XXX forgot to update servers due to XXX reasons)


Configuring Uncomplicated Firewall (UFW)


By configuring UFW, I only allow OpenSSH (Port 22), HTTP (Port 80) and HTTPS (Port 443)
It is a good security practice because it limits exposure to the website by blocking out other connections by default which reduces the attack surface for hackers to exploit. 

Without UFW any service running could be exposed to the internet and attackers are able to scan your IP for open ports and exploit them.

Testing my UFW rules (3.27.217.215 is my public facing IP for my EC2 website)



Scheduling crontab to check user login history for the past 24 hours



Helps to detect unauthorized access, identify failed login attempts and useful to know about the user’s activity.

can you make all this into a github readme format


ChatGPT said:
Sure! Here's a nicely formatted GitHub README.md based on your detailed notes. You can copy-paste this into your repository's README.md file:

markdown
Copy code
# BRG-27 Labs

## 1. Install Ubuntu using VirtualBox (28/6/25)
- Configuring VM settings:  
  - OS: Ubuntu  
  - RAM: 14GB  
  - Storage: 20GB  
- **Observation:** Higher RAM allocated = smoother VM performance.

---

## 2. Familiarity with Ubuntu Linux – Basic Command Line Navigation and Utilities (28/6/25)

| Command | Purpose |
|---------|---------|
| `pwd`   | Show current working directory |
| `ls`    | List files and directories |
| `cd`    | Change directory |
| `mkdir` | Create a new directory |
| `touch` | Create a new empty file |
| `cat`   | Display contents of a file |

### Observations:
- `pwd` outputs: `/home/ubuntu`  
- `ls` shows: Desktop, Downloads, Pictures, Snap, Videos, Documents, Music, Public, Templates  
- `cd Desktop` changes to `~/Desktop`  
- `mkdir foldername` creates a folder, then `cd foldername` to enter it  
- `touch testfile` creates an empty file  
- `cat testfile` outputs the file contents  

---

## 3. Understanding Directory Structure

| Directory | Purpose |
|-----------|---------|
| `/etc`    | System configuration files (controls system behavior) |
| `/var`    | Variable data files (logs, caches, spool files) |
| `/home`   | Personal directories for all users |

- `man` command shows detailed manual/help for commands.

---

## 4. Linux Services – Managing Background Services

- List active services:  
  ```bash
  systemctl list-units --type=service
Start/stop services:

bash
Copy code
sudo systemctl start|stop [service-name]
5. GitHub Setup
Created GitHub account at https://github.com

Created repository: JunWei26-BRG-27-labs for lab documentation

Added a README.md for lab summaries and commands

6. Installing Ubuntu on VirtualBox
Download Ubuntu ISO: https://ubuntu.com/download/desktop

Download VirtualBox: https://www.virtualbox.org/wiki/Downloads

VM Settings:

RAM: 10 GB (increased from 10GB to 14GB for better performance)

Disk space: 20 GB

Installation mostly straightforward, increased RAM improved performance.

7. Ubuntu Desktop Environment & Useful Commands
ps -e lists running processes:

PID = Process ID

TTY = Terminal

TIME = CPU time used

CMD = Command that launched process

top shows real-time system resource usage (like Windows Task Manager)

Press 1 inside top to view individual CPU core usage.

ls vs ls -la:

ls shows files/folders

ls -la shows hidden files and detailed info (permissions, size, owner, etc.)

ls -lah adds human-readable file sizes (KB, MB, GB)

touch testfile creates empty file

gedit testfile opens graphical editor (requires desktop environment)

nano testfile is a terminal text editor (works via SSH)

cat testfile shows entire file (not scrollable)

less testfile allows scrollable viewing (good for big files)

cp copies files (original kept)

mv moves/renames files (original removed)

8. SuperUser (Root) vs Sudo User
Adding users requires admin (root or sudo) privileges

Use sudo to run commands with admin rights

9. DNS and Network Basics
nslookup: Query DNS to find IP/domain info

whois: Shows domain ownership and registration info

Private IP: Internal network IP (e.g., 192.168.x.x)

Public IP: Globally unique IP assigned by ISP

NAT: Router translates private IPs to public IP

127.0.0.1: Loopback address (refers to local machine)

10. Apache & UFW (Uncomplicated Firewall)
Access 127.0.0.1 after installing Apache to test web server

sudo ufw status verbose shows firewall status (verbose = more details)

Allowed ports for security:

OpenSSH (22)

HTTP (80)

HTTPS (443)

This limits exposure and reduces attack surface.

11. SSH and Permissions
chmod changes file permissions. Permissions include:

Read (r), Write (w), Execute (x)

Users types:

Owner (u)

Group (g)

Others (o)

Digit	Binary	Permissions	Meaning
0	000	---	No access
1	001	--x	Execute only
2	010	-w-	Write only
3	011	-wx	Write + Execute
4	100	r--	Read only
5	101	r-x	Read + Execute
6	110	rw-	Read + Write
7	111	rwx	Read + Write + Execute

Example permissions:

chmod 755 script.sh → Owner: rwx, Group: r-x, Others: r-x

chmod 644 document.txt → Owner: rw-, Group: r--, Others: r--

chmod 700 file → Only owner full access

chmod 600 file → Only owner read/write

12. Cloud-based Virtual Machine: AWS EC2
Instance type: T2.micro (free tier but limited settings)

Use key pair for SSH login

Common issue: AWS security groups blocking port 80 and 22 (must allow them)

13. SSH to EC2 Instance
Use SSH key pair and Git Bash to login

VirtualBox Guest OS installation issues led to switching to Git Bash for SSH

14. Hosting Website and DNS with DuckDNS
Use DuckDNS for free dynamic DNS:
http://junweiec2website.duckdns.org/

15. Using Crontab to Automate Tasks
Crontab is Linux’s task scheduler for automated, timed tasks

Automate daily system update to patch vulnerabilities and save time

Example crontab to update system every day at midnight:

bash
Copy code
0 0 * * * sudo apt update && sudo apt upgrade -y
16. Importance of UFW Firewall Rules
Only allow essential ports: 22 (SSH), 80 (HTTP), 443 (HTTPS)

Blocks unwanted ports/services to reduce attack surface

Without UFW, exposed services can be exploited easily

17. Scheduling Login History Audit with Crontab
Script checks user login history for past 24 hours using:

bash
Copy code
last -F -s -1days
Helps detect unauthorized access and failed login attempts

Useful for monitoring and improving security
