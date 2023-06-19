---
title: MONA
summary: A python script that can be used to automate and speed up specific searches on Immunity Debugger and WinDBG.
description: A python script that can be used to automate and speed up specific searches on Immunity Debugger and WinDBG.
---

**[https://github.com/corelan/mona](https://github.com/corelan/mona)**

## MONA Basis


 > 
 > **<font color=red>!mona config -set workingfolder </font>c:\mona**</br>
 > Set where mona will save data.

 > 
 > **<font color=red>!mona bytearray -cpb "</font>\\x00<font color=red>"</br></font>**
 > Generate byte array.

 > 
 > **<font color=red>!mona jmp -r ESP m "essfunc.dll"</font>**</br>
 > Find jump address.

## MONA Use it in IMMUNITY

Put the followig script in `C:\Program Files (x86)\Immunity Inc\Immunity Debugger\PyCommands`

https://github.com/corelan/mona

![tool-mona-immunity.png](../attachments/tool-mona-immunity.png)
