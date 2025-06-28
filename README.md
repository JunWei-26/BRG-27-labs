# BRG-27-labs
**#Install Ubuntu using VirtualBox.** 28/6/25
Configuring VM setting - OS: Ubuntu, RAM: 14GB, Storage: 20GB #Observation > Higher RAM allocated == smoother the VM will run 

**#Familiarity with Ubuntu Linux – Basic command line navigation and utilities.** 28/6/25
Practice using `pwd`, `ls`, `cd`, `mkdir`, and `touch`
| Command     | Purpose                                      |
|-------------|----------------------------------------------|
| `pwd`       | Show current working directory               |
| `ls`        | List files and directories                   |
| `cd`        | Change directory                             |
| `mkdir`     | Create a new directory                       |
| `touch`     | Create a new empty file                      |
| `cat`       | Command that shows what inside a file        |

#What I Observed: 
'pwd' : /home/ubuntu
'ls' : Desktop, Download, Pictures, Snap, Videos, Documents, Music, Public, Template
'cd' (Desktop) : ~/Desktop$
'mkdir' : mkdir *foldername* > cd *foldername* 
'touch' : touch *foldername* > ls *foldername* 
'cat' : (echo "This is a testfile" > testfile.txt) > cat testfile.txt : This is a testfile

**Understand directory structure (`/etc`, `/var`, `/home`).**
** Use SUDO (Admin priviledge) 
/etc - Stores system settings and configuration files (files in /etc controls how your system behave)
/var - stores data that changes while system is running 
/home - personal folder for all users on the system
/man stands for manual, it shows you detailed information about the command

**Linux Services – Understanding and managing background services.**
'systemctl list-units --type=service' - This command is used in Linux (systemd-based) systems like Ubuntu to list all active services running on your system.
'sudo systemctl start|stop [service]' - 
