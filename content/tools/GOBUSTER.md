---
title: GOBUSTER
---

## GOBUSTER Files and Folders Fuzz


 > 
 > **<font color=red>gobuster dir -u</font> http://\[TARGET_IP\]:\[TARGET_PORT\] <font color=red>-w</font> myWordList <font color=red>-x</font> php,txt,html</br>**
 > Search files.
 > 
 > **<font color=red>gobuster dir -u</font> http://\[TARGET_IP\]:\[TARGET_PORT\] <font color=red>-w</font> myWordList</br>**
 > Search folders.

## GOBUSTER Flags


 > 
 > **<font color=red>-u </font>http://\[TARGET_IP\]:\[TARGET_PORT\]</br>**
 > Target folders.
 > 
 > **<font color=red>-x</font> php,txt,html</br>**
 > Target files.
 > 
 > **<font color=red>-w</font> myWordList</br>**
 > Wordlist.
 > 
 > **<font color=red>-b</font> 403<font color=red>,</font>302</br>**
 > Exclude some code from response.
 > 
 > **<font color=red>-U</font> myUser</br>**
 > Username. 
 > 
 > **<font color=red>-P</font> myPass</br>**
 > Password.

 > 
 > **<font color=red>-e</font></br>**
 > Print the full URLs in your console.
 > 
 > **<font color=red>-p</font> \[TARGET_IP\]</br>**
 > Proxy to use for requests.
 > 
 > **<font color=red>-c</font> \<http cookies\></br>**
 > Specify a cookie for simulating your auth.
