---
title: WFUZZ
summary: A web application fuzzer.
description: A web application fuzzer.
---

[https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)

## WFUZZ Folder Fuzz


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList http://\[TARGET_IP\]:\[TARGET_PORT\]/<font color=red>FUZZ</font></br>**
 > Fuzz Folders

## WFUZZ GET Fuzz


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList http://\[TARGET_IP\]:\[TARGET_PORT\]/api/file?parameter=<font color=red>FUZZ</font></br>**
 > Fuzz GET Parameter (ex: API).

## WFUZZ POST Login Brute Force


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList -u http://\[TARGET_IP\]:\[TARGET_PORT\]/login.php -d “username=<font color=red>FUZZ</font>&password=<font color=red>FUZZ</font>”</br>**
 > Fuzz POST Login.

## WFUZZ Flags


 > 
 > **<font color=red>-z</font></br>**
 > Word File to replace FUZZ in the request. For example -z file,big.txt.

 > 
 > **<font color=red>-d</font></br>**
 > Specifies POST parameters.
 > 
 > **<font color=red>-s</font></br>**
 > Timing for requests.
 > 
 > **<font color=red>-c</font></br>**
 > Shows the output in color.

 > 
 > **<font color=red>--hc</font></br>**
 > Don't show certain http response codes.
 > 
 > **<font color=red>--hl</font></br>**
 > Don't show a certain amount of lines in the response.
 > 
 > **<font color=red>--hh</font></br>**
 > Don't show a certain amount of words.
