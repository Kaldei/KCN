---
title: Radare2
summary: UNIX-like reverse engineering framework and command-line toolset.
description: UNIX-like reverse engineering framework and command-line toolset.
---

**https://github.com/radareorg/radare2**

## RADARE2 Launch


 > 
 > **<font color=red>r2</font> myFile**</br>
 > Open myFile in Radare2.

## RADARE2 Basis


 > 
 > **<font color=red>aaa</font>**</br>
 > Analyze and autoname functions.
 > 
 > **<font color=red>afl</font>**</br>
 > Print all functions autodetected.

 > 
 > **<font color=red>pdf @main</font>**</br>
 > Print disassembly of main.
 > 
 > **<font color=red>pdf</font>**</br>
 > Print disassembly of the current function.

 > 
 > **<font color=red>s</font> myFunction**</br>
 > Change location.

## RADARE2 Memory Content


 > 
 > **<font color=red>px</font> @rbp-0xc**</br>
 > Print content of the variable at rbp-0xc. 

 > 
 > **<font color=red>dr</font>**</br>
 > Print registers.
 > 
 > **<font color=red>dr</font> <font color=red>rip=</font>address**</br>
 > Set the instruction that we want to execute next.

## RADARE2 Move in Program Execution


 > 
 > **<font color=red>ood</font>**</br>
 > Run (& re-run) the program.

 > 
 > **<font color=red>dc</font>**</br>
 > Run the program until it hits the breakpoint.
 > 
 > **<font color=red>ds</font>**</br>
 > Step to the next instruction.

## RADARE2 Breakpoint


 > 
 > **<font color=red>db</font> address**</br>
 > Place a breakpoint.

## RADARE2 Visual Mode


 > 
 > **<font color=red>V!</font>**</br>
 > Enter fancy mode.
 > 
 > **<font color=red>VV</font>**</br>
 > Enter visual mode (with blocks).
 > 
 > **<font color=red>P</font>**</br>
 > Change display mode.

 > 
 > **<font color=red>TAB</font>**</br>
 > Change selected box.

 > 
 > **<font color=red>:dc</font>**</br>
 > Run program.
 > 
 > **<font color=red>S</font>**</br>
 > Step instructions.
 > 
 > **<font color=red>SHIFT + S</font>**</br>
 > Step further.
