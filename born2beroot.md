### UFW - Uncomplicated Fire Wall
- ufw enable => enable firewall
- ufw status verbose => checking rule
- ufw default deny incoming
- ufw default allow outgoing => setting up defaults
- ufw allow ssh
- ufw allow 4242
- ufw status numbered
- ufw delete <number>
- ssh <user>@127.0.0.1 -p 4242

### SSH
- sudo systemctl status ssh
=> Check SSH server status

- service ssh restart
- sudo systemctl restart ssh
=> restart ssh

- ss -tunlp => check connection

- /etc/ssh/sshd_config
=> ssh config file

### Password Management
- man pwquality.conf

- sudo apt install libpam-pwquality
=> install password quality checking quality

- /etc/login.defs => pwd config def file
- chage -<flag> <number> <user-login> => manually change pwd expiry info for existing users
- chage -l <user-name> => check pwd policy for that user

-/etc/security/pwquality.conf or /etc/pam.d/common-password
=> conf pwd requirements

### Group
- sudo groupadd <group-name> => create a new group
- sudo useradd <user-name> => create new user
- sudo usermod -aG <group-name> <user-name> => assign user to a group. man usermod for more flags
- getent group => list all the group (getent <option>)
- getent group <group-name> => list entries of that particular group
- groups => check what group the current user belong to
- su / su <user-name> => switch to root, switch to chosen user

### Visudo
Visudo is a safe way to edit the sudoers file: /etc/sudoers. Visudo prevent multiple simultaneous edits, provides basic sanity checks. If the sudoers file is currently being edited, a message to try again later will appear.

- sudo visudo => to access it
- requiretty => activate TTY flag. If this flag is set, sudo can only be run from a login session and not via other means such as cron or cgi-bin scripts. This help preventing exploit. The flag is off by default.

### Hostname
- hostnamectl => checking hostname and other info
- hostnamectl set-hostname <new-hostname> => change host name
- Also change host name in /etc/hosts

###Defense
VDI location: /Users/ktang/sgoinfre/students/ktang/born2beroot

##How a virtual machine works:
Host hardware => Host operating system => Hypervisor => Virtual Machine
Host hardware => Hypervisor => Virtual Machine
##Choice of operating system: Debian
##Difference between Debian and CentOS:
- CentOS more suitable for big enterprise. It's not very user-friendly in term of GUI. Using SELlinux instead of APParmor for Debian. More stable with longer update cycle. Using YUM instead of APT.
- Debian: better for personal use. Support multiple architecture -> better for developer. Large user base that provide support. 
##Purpose of virtual machine:
- For you to experiment with things without the fear of breaking your real machien

##aptitude and apt/ what is APPArmor:
+aptitude: high-level package manager, possess more functionality than APT, with option for GUI
+APT: lower-level package manager, which can be used by other higher-level package managers
Instead of typing apt-get, apt-cache, apt-config etc... we can just simply use apt now (https://phoenixnap.com/kb/apt-vs-apt-get)
- apt vs apt-get: https://phoenixnap.com/kb/apt-vs-apt-get
	> apt is a new command, aim to merge apt-get and apt-cache together. Most user recommend to use apt instead of the other two.

APParmor: Is the default security system on Debian. APParmor security model is to bind access control attributes to programs rather than to users. Differences between Apparmor and other Mandatory Access Control system on Linus: 
- It is path based
- User friendly with integrated GUI
Once an application is compromised, a APParmor will isolate the attacker from the rest of the system.
Check if APParmor is working: aa-status

- Check UFW: ufw status 
- Check SSH: systemctl status ssh
- Check operation system: uname -a

- dpkq -l | grep sudo => check to see if sudo has been install

## Cron:
https://devhints.io/cron
- crontab -e - to edit the cron script
- crontab -l - show the cron script
- What is a Daemon? => Utility program that run silently in the background to monitor and take care of certain tasks, ensuring the operating system runs properly.
- cron => Daemon to execute scheduled commands
- /usr/local/bin/monitoring.sh

### Misc command
- grep = global regulator expression search
- lsblk => show the partition
- chage => change user pwd expiry info; -M: max | -m: min | -W: warningi | -l: list password rule, follow with <user_name> to check rule for that particular user
- ctl = control temporal logic
- bash script cheatsheet: https://devhints.io/bash
https://devhints.io/bash



