---
title: HYDRA
---

## HYDRA Base


 > 
 > **<font color=red>hydra -l </font>username <font color=red>-P</font> wordlist.txt \[TARGET_IP\] service**

## HYDRA Flags


 > 
 > **<font color=red>-V</font>**</br>
 > Verbose.
 > 
 > **<font color=red>-vV</font>**</br>
 > Very Verbose.

 > 
 > **<font color=red>-L</font> myUsersFile**</br>
 > Specify usernames file list.
 > 
 > **<font color=red>-l </font> myUser**</br>
 > Specify username.

 > 
 > **<font color=red>-P </font>myPassFile**</br>
 > Specify password file list.
 > 
 > **<font color=red>-p</font> myPass**</br>
 > Specify password.

 > 
 > **<font color=red>-t</font> 4**</br>
 > Number of parallel connections per target.

## SSH


 > 
 > **<font color=red>hydra -L</font> myUsersFile <font color=red>-P</font> myPassFile \[TARGET_IP\]<font color=red>ssh</font>**</br>
 > Brute Force SSH.

## HTTP POST


 > 
 > **<font color=red>hydra -vV -L</font> myUsersFile.txt  <font color=red>-P</font> /usr/share/wordlists/rockyou.txt  \[TARGET_IP\] <font color=red>http-post-form ‘</font>/path/to/form.php<font color=red>:</font>username<font color=red>=^USER^&</font>password<font color=red>=^PASS^&</font>login=Login:<font color=red>F=</font>ChainNotOK<font color=red>’</font>**</br>
 > Brute Force HTTP POST form with valid username.

## HTTP Basic Access Auth


 > 
 > **<font color=red>hydra -vV -l </font>myUser <font color=red>-P</font> /usr/share/wordlists/rockyou.txt \[TARGET_IP\]<font color=red>http-get</font> /path/**</br>
 > Brute Force HTTP Basic Access Authentication.

## FTP


 > 
 > **<font color=red>hydra -vV -l </font>myUser <font color=red>-P </font>/usr/share/wordlists/rockyou.txt  \[TARGET_IP\] <font color=red>ftp</font>**</br>
 > Brute Force FTP Login.
