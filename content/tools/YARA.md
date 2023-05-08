---
title: YARA
summary: A tool aimed to identify and classify malware samples.
description: A tool aimed to identify and classify malware samples.
---

**[https://github.com/VirusTotal/yara](https://github.com/VirusTotal/yara)**

## YARA Basis



## YARA Flag


 > 
 > **<font color=red>-m</font>**</br>
 > Prints metadata of the rules that were satisfied during the analysis.
 > 
 > **<font color=red>-c</font>**</br>
 > Prints the number of matches.

 > 
 > **<font color=red>-s</font>**</br>
 > Prints satisfied rules.
 > 
 > **<font color=red>-n</font>**</br>
 > Prints not satisfied rules.

## YARA Rules

**Cheat Sheet:** https://twitter.com/fr0gger\_/status/1516570364775907328/photo/1

**Keywords:** and, not, or, >, >=, !=, any of them

**Example:**

````
rule myRule {
	/* Infos */
	meta:
	      author = "myAuthor"
	      description = "myRule Description"
	      created = "12/12/2012 12:12"
	
	/* Match one string */
	strings:
			$myString = “Hello myString”
		condition:
			$myString
	
		
	/* Match multiple strings */
	strings:
			$myStringLow = “hello mystring”
			$myStringHigh = “HELLO MYSTRING”
		condition:
			any of them
}
````

**Valhalla Rules Database:** https://valhalla.nextron-systems.com/ 

## YARA YarGen

**[https://github.com/Neo23x0/yarGen](https://github.com/Neo23x0/yarGen)**

 > 
 > **<font color=orange>python3 yarGen.py --update</font>**</br>
 > Update.

 > 
 > **<font color=red>python3 yarGen.py -m</font> mySuspiciousFile <font color=red>--excludegood -o</font> myNewRule.yar**</br>
 > Create a Yara rule from mySuspiciousFile.

 > 
 > **<font color=red>-m</font>**</br>
 > Path to the files you want to generate rules for.
 > 
 > **<font color=red>--excludegood</font>**</br>
 > Force to exclude all goodware strings.
 > 
 > **<font color=red>-o</font>**</br>
 > Output Yara rule file.

## YARA with OSQUERY
