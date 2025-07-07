# BRG-27 - Introduction to Server Environments and Architecture (ISEA)

# Overview

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


3. Linux Services, Permissions, and Bash Scripting
Service Configuration and User Permissions

•	Services installed. SSH
 
SSH is a secure protocol used to remotely access and manage your Linux server over an encrypted connection.
	I was able to SSH into my AWS EC2 using GitBash by inputting the command
 
Why is SSH service important? 
•	It allows you to securely access your server from anywhere using tools like GitBash. 
•	Use public-private key encryption which is safer compared to password login.

Problems I faced initially are networking problems, such as blocking HTTP port 80 and SSH port 22 in the security rule
 
 
Uncomplicated Firewall (UFW) a simplified command-line tool used to manage the Linux firewall

Why is UFW important? 
By default, it blocks unauthorized access and only allows specific ports like SSH (22), HTTP (80), and HTTPS (443). It works by blocking unwanted network traffic and only allowing connections that you approve. This helps prevent unauthorized access, hacking attempts, or malicious traffic from reaching your server or system.

 
 

Cron
 

What is crontab? It stands for cron table, and it’s a Linux feature that allows you to schedule tasks run automatically at specific times or intervals that you set. It is like a task scheduler.

Why is it good to automate your update in your system (Using crontabs)
•	It helps to protect your website/server from known vulnerabilities or zero-day exploits
•	Helps with bug fixes
•	Automation helps to save time hence lesser manpower is needed
•	Consistency, lesser human errors (XXX forgot to update servers due to XXX reasons)
•	Helps to detect unauthorized access, identify failed login attempts and useful to know about the user’s activity.


I added two cron schedulers as seen from the command below, first is to check for any system updates and upgrades everyday at 12:00 and second is the audit for login history at 12:30
 







•	Permission controls 
After creating 3 users: Alice, Bob and Mallory. 

sudo chmod 770 /home/shared/alice-folder      # Full access to group
sudo chmod 750 /home/shared/bob-folder        # Read & execute
sudo chmod 740 /home/shared/mallory-folder    # Read only
	
I logged in as Alice and tried to create a Text file into bob-folder however it is denied because due to the permission set chmod 750, it is only read and executable only.

 

Using Chown (Change Owner) for all 3 users to their respective folders
 
Configuring my MOTD, which reminds me what I need to check daily. 
It is useful for users in the sense that it provides immediate, useful context to users as soon as they log in
 
 



Using ACL service 
	 
Why is ACL better than chmod? It gives more control over who gets what kind of access
While chmod is useful for setting basic permissions, it only works for one user, one group, and everyone else. This becomes a problem when you need to give different access to multiple users. For example, you can't use chmod to let Alice have full access, Bob read-only, and Mallory no access, unless you change the group or ownership.
ACL (Access Control Lists) solves this by letting you give custom permissions to each user without changing file ownership. It’s more flexible and better for shared folders or team environments. ACL makes it easier to control who can read, write, or execute files, and helps improve security by giving each user only the access they need.









Apache2 Service
 
Apache2 service is the program that runs the Apache web server on your computer or server. It works in the background and listens for requests from web browsers. When someone visits a website hosted on your server, Apache2 sends the web pages or files they asked for.
This service is needed because without it, your server cannot show websites or web apps to users. 

4. Cloud Infrastructure and TCO Analysis
Cloud Deployment
For this lab, I used Amazon Web Services (AWS) to create and manage a virtual machine (EC2 instance). AWS was chosen because it is widely used and offers free-tier options for learning. Which helps beginners like me. Overall, AWS EC2 is easy to use, secure, and good value.
To secure my VM, I launched an Ubuntu Server instance and downloaded a key pair (.pem file) for SSH access. I set the key’s permissions to read-only using chmod 400 to ensure secure login. I also set up the security group to allow only SSH (port 22) from my IP address and later allowed web traffic (ports 80 or 443) if needed. Inside the VM, I kept the software updated and enabled the firewall (UFW) for extra protection.
This experience taught me how to securely set up and manage cloud servers, balancing ease of access with security. It also made me more aware of costs by choosing the right instance and monitoring usage, which is important for managing overall expenses.

Cost Analysis

I compared the pricing of AWS, Azure, and DigitalOcean for running a small virtual machine. AWS offers a 12-month free tier with 750 hours each month, and after that, it costs about $8.50 per month. DigitalOcean doesn't have a free tier, but its plans start at $4 per month, making it affordable for small projects. Azure also gives 12 months of free use for certain VMs and has low-cost plans starting around $2.88, though larger instances can be more expensive.
Overall, I chose AWS because its free plan is generous, and it offers the flexibility and scalability needed for future growth.

5. DNS Setup and SSL Configuration
Hosting my own DNS using DuckDNS (http://junweiec2website.duckdns.org/)
For this lab, I used DuckDNS, a free service that helps link a simple domain name to my server’s IP address. This made it easier to access my server using the domain instead of the IP
 


For security, I used Let’s Encrypt and Certbot to get a free SSL certificate so my website could use HTTPS. It was mostly easy to set up, but I needed to open some firewall ports and set up the server to use the certificate. I also made sure all visitors are sent to the secure HTTPS version of the site and added some extra safety settings.
This showed me why encrypted websites are important. HTTPS keeps information safe, helps people trust the site, and stops warning messages in browsers. Using DuckDNS and Let’s Encrypt taught me how to make a website easy to access and secure.
 
 
 
7. Consulting Simulation and Additional Server Service
In the simulation, I suggested using a basic LAMP stack (Linux, Apache, MySQL, PHP) on an Ubuntu server. I used AWS free tier to keep costs low and focused on security by setting up a firewall, using SSH keys, and enabling automatic updates.
After getting feedback, I improved the setup by adding stronger passwords, extra SSH protection with fail2ban, and monitoring tools to make the server safer.
               
8. Problems Encountered and Solutions
Problems Encountered and Solutions
•	SSL failure
Opened firewall and EC2 security group ports 80 and 443.
•	Could not SSH into EC2
Fixed key permissions using chmod 400 and adjusted inbound rules.
•	Apache not showing page
Restarted Apache and checked file permissions.
•	Cron job didn’t run
Added execute permission with chmod +x and checked logs.
•	DNS not resolving
Verified DNS records and waited for propagation.
•	MOTD message missing
Checked /etc/motd file and update scripts.

9. Industry Relevance
This lab is useful for jobs like System Administrator and DevOps Engineer. It helped me practice real skills like setting up (basic) servers, securing them, using automation, and working with cloud services. These skills are important in many IT careers.
I also learned about some important security guides. NIST (National Institute of Standards and Technology) is a set of rules that help keep computer systems safe. OWASP (Open Web Application Security Project) focuses on protecting websites from common attacks. Knowing these helps me understand how professionals keep systems secure.





10. Final Reflection
This lab series helped me develop important skills. I improved managing file permissions with commands like chmod and chown and learned to use ACL for more flexible access control. I set up cron jobs using crontab to automate routine tasks and save time.
I gained experience securing servers through SSH key authentication, configuring firewalls with UFW, and using Fail2ban to protect against attacks. Working with AWS taught me how to create and safely manage cloud servers. I also learned the importance of keeping software updated and using SSL certificates for secure communication.
In future projects, I plan to emphasize security from the start, apply ACLs for better permission management, and automate more processes to reduce errors. Overall, this experience has made me more confident in managing real-world servers.

