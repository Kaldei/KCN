---
title: FUFF
summary: "A fast web fuzzer, written in Go."
description: "A fast web fuzzer, written in Go."
---

[https://github.com/ffuf/ffuf](https://github.com/ffuf/ffuf)

## FUFF Web Paths


 > 
 > **<font color=red>fuff -w</font> /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt<font color=red>:FUZZ -u</font> http://\[TARGET_DOMAIN\]/<font color=red>FUZZ</font></br>**
 > Web Path FUZZ

## FUFF Virtual Host Fuzz


 > 
 > **<font color=red>ffuf -w</font> <font color=lightblue>/usr/share/wordlists/seclists/Discovery/DNS/namelist.txt</font> <font color=red>-H "Host: FUZZ.</font>\[TARGET_DOMAIN\]<font color=red>" -u</font> http://\[TARGET_DOMAIN\] <font color=red>-fs</font> 2395</br>**
 > Virtual Host FUZZ

## FUFF User Enumeration


 > 
 > **<font color=red>ffuf -w</font> <font color=lightblue>/usr/share/wordlists/seclists/Usernames/Names/names.txt</font> <font color=red>-X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u</font> http://\[TARGET_DOMAIN\]/signup <font color=red>-mr </font>"username already exists"</br>**
 > User Enumeration

## FUFF HTTP POST Form Brute Force

WPSCAN> **<font color=red>ffuf -w </font>myUsersFile.txt<font color=red>:W1,</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font><font color=red>:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u</font> http://\[TARGET_IP\]/login <font color=red>-fc 200</font>**</br>

 > 
 > Brute Force HTTP POST form with valid username.

## FUFF Flags


 > 
 > **<font color=red>-fs</font></br>**
 > Size to filter (do not show response with this size).
 > 
 > **<font color=red>-mr</font></br>**
 > Text on the page we are looking for to validate.

 > 
 > **<font color=red>-w</font></br>**
 > Wordlist location.
 > 
 > **<font color=red>-u </font></br>**
 > Specifies the URL.
 > 
 > **<font color=red>-d</font></br>**
 > Data (fields) that we send.
 > 
 > **<font color=red>-H</font></br>**
 > Add additional headers to the request.
