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
 > Switch from OpenSSL (default) to Schannel SSL Backend (Windows built-in). This is useful in an organization with enterprise-managed certificates.

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
 > 
 > **<font color=red>git log</font>**</br>
 > Show commit history.
 > 
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
 > **<font color=red>git tag</font> myTag**</br>
 > Create a tag.
 > 
 > **<font color=red>git push</font>**</br>
 > Push commits to remote repository.

## GIT Branch


 > 
 > **<font color=red>git branch</font>**</br>
 > Show local branches.
 > 
 > **<font color=red>git branch -r</font>**</br>
 > Show local branches.

 > 
 > **<font color=red>git branch myBranch</font>**</br>
 > Create new branch.

 > 
 > **<font color=red>git merge myBranch</font>**</br>
 > Merge myBranch to current branch.

## GIT Checkout


 > 
 > **<font color=red>git checkout</font> myBranch**</br>
 > Move HEAD to last commit of myBranch.

 > 
 > **<font color=red>git checkout</font> myBranch<font color=red>^</font>**
 > Move HEAD to penultimate commit of myBranch.

 > 
 > **<font color=red>git checkout HEAD^</font>**</br>
 > Moves HEAD 1 commit back from current HEAD.
 > 
 > **<font color=red>git checkout HEAD^^^</font>**</br>
 > Moves HEAD 3 commits back from current HEAD.
 > 
 > **<font color=red>git checkout HEAD~12</font>**</br>
 > Moves HEAD 12 commits back from current HEAD.

 > 
 > **<font color=red>git checkout HEAD^</font>**</br>
 > Moves HEAD 1 commit back from current HEAD in the 1st parent of a merge.
 > 
 > **<font color=red>git checkout HEAD^2</font>**</br>
 > Moves HEAD 1 commit back from current HEAD in the 2nd parent of a merge.
