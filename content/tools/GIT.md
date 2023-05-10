---
title: GIT
summary: A free and open source distributed version control system.
description: A free and open source distributed version control system.
---

**[https://git-scm.com/](https://git-scm.com/)**

## GIT HEAD

`HEAD` is the location in the commit tree. It's a "pointer" to a commit. It is possible to move it with git checkout.

## GIT Config


 > 
 > **<font color=red>git config --list</font>**</br>
 > Parameters list.
 > 
 > **<font color=red>git config</font> user.name**</br>
 > Display a parameter (`user.name` here).
 > 
 > **<font color=red>git config --global</font> user.name myName**</br>
 > Change parameter value.

 > 
 > **<font color=red>git config --global http.sslBackend schannel</font>**</br>
 > Switch from OpenSSL (default) to Schannel SSL Backend (Windows buitl-in). This is usefull 

## GIT Basis


 > 
 > **<font color=red>git init</font>**</br>
 > Create git repository (local).
 > 
 > **<font color=red>git clone</font> \[REPO_URL\]**</br>
 > Clone remote repository to local machine.

 > 
 > **<font color=red>git status</font>**</br>
 > Show status files (modified, added, removed, staged, ...).
 > 
 > **<font color=red>git show</font> myCommit**</br>
 > Display commit info.
 > **<font color=red>git log</font>**</br>
 > Show commit history.
 > **<font color=red>git log -p</font>**</br>
 > Shows difference between commits.

 > 
 > **<font color=red>git add</font> myFile**</br>
 > Stage myFile (prepare for commit).
 > 
 > **<font color=red>git add -A</font>**</br>
 > Stage all files (including untracked/new ones).
 > 
 > **<font color=red>git stash</font>**</br>
 > Put changes in a side working directory.

 > 
 > **<font color=red>git commit -m "</font>Commit Message<font color=red>"</font>**</br>
 > Create a commit.
 > 
 > **<font color=red>git commit --amend</font>**</br>
 > Modify las commit.
 > 
 > **<font color=red>git push</font>**</br>
 > Push commits to remote repository.
