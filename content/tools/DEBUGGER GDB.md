---
title: DEBUGGER GDB
summary: The GNU Project Debugger.
description: The GNU Project Debugger.
---

**https://www.sourceware.org/gdb/**

## GDB Launch

Supported languages: Ada / Assembly / C / C++ / D / Fortran / Go / Objective-C / OpenCL / Modula-2 / Pascal / Rust

 > 
 > **<font color=red>gdb</font> myFile**</br>
 > Open myFile in gdb.

 > 
 > **<font color=red>gdb -p 'pidof</font> myFile<font color=red>'</font>**
 > Attach GDB to the process id of myFile (running program).

## GDB Basis


 > 
 > **<font color=red>set disassembly-flavor intel</font>**</br>
 > Make disassemble more readable.

 > 
 > **<font color=red>disassemble main</font>**</br>
 > Display all assembler instructions from main.
 > 
 > **<font color=red>print</font> myFunction**</br>
 > Display the address of myFunction.

 > 
 > **<font color=red>vmmap</font>**</br>
 > Show Virtual Memory Map.

## GDB Memory Content


 > 
 > **<font color=red>info registers</font>**</br>
 > Give info about registers.
 > 
 > **<font color=red>info proc mappings</font>**</br>
 > Give info about memory.

 > 
 > **<font color=red>set</font> $eax=0**</br>
 > Set the value (here set eax to 0).

## GDB Move in Program Execution


 > 
 > **<font color=red>x/s </font>address**
 > Go to a specific address.

 > 
 > **<font color=red>run</font>**</br>
 > Start the program.
 > 
 > **<font color=red>continue</font>**</br>
 > Run the program until next breakpoint.

 > 
 > **<font color=red>si</font>**</br>
 > Step one instruction (step into function calls).
 > 
 > **<font color=red>ni</font>**</br>
 > Step one instruction (no step into function calls).

## GDB Breakpoint


 > 
 > **<font color=red>break \*main</font>**</br>
 > Add a breakpoint to main function.
 > 
 > \**<font color=red>break *</font>address**</br>
 > Add a breakpoint to an address.

 > 
 > **<font color=red>del</font>**</br>
 > Delete a breakpoint.

## GDB Hook

A Hook execute GDB commands when hitting a breakpoint.

 > 
 > **<font color=red>define hook-stop</font>**</br>
 > Switches to Hook creation mode (enter commands and end with **<font color=red>end</font>**).
