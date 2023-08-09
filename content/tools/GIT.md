---
title: GIT
summary: A free and open source distributed version control system.
description: A free and open source distributed version control system.
---

**[https://git-scm.com/](https://git-scm.com/)**

## Resource

* [https://ohshitgit.com/en](https://ohshitgit.com/en)
* [https://learngitbranching.js.org/](https://learngitbranching.js.org/)

## HEAD

`HEAD` is the location in the commit tree. It's a "pointer" to a commit. It is possible to move it with git checkout.

## Config


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

## Basis


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
 > **<font color=red>git add</font> myFile**</br>
 > Stage myFile (prepare for commit).
 > 
 > **<font color=red>git add -A</font>**</br>
 > Stage all files (including untracked/new ones).

 > 
 > **<font color=red>git stash save</font> myStashName**</br>
 > Put changes in a side working directory for later use.
 > 
 > **<font color=red>git stash list</font>**</br>
 > List stashes.
 > 
 > **<font color=red>git stash apply</font> stashIndex**</br>
 > Add stashed code back into the code.

 > 
 > **<font color=red>git commit -m "</font>Commit Message<font color=red>"</font>**</br>
 > Create a commit.
 > 
 > **<font color=red>git commit -am "</font>Commit Message<font color=red>"</font>**</br>
 > Add files in current directory and create a commit.
 > 
 > **<font color=red>git commit --amend</font>**</br>
 > Modify last commit (only works if code is not pushed.
 > 
 > **<font color=red>git tag</font> myTag**</br>
 > Create a tag.
 > 
 > **<font color=red>git push</font>**</br>
 > Push commits to remote repository.

## History


 > 
 > **<font color=red>git show</font> myCommit**</br>
 > Display commit info.
 > 
 > **<font color=red>git reflog</font>**</br>
 > Show commit history (one line per commit, more readable).
 > 
 > **<font color=red>git log</font>**</br>
 > Show commit history.
 > 
 > **<font color=red>git log --oneline --graph --decorate</font>**</br>
 > Show commit history with graph.
 > 
 > **<font color=red>git log -p</font>**</br>
 > Shows difference between commits.

## Branch


 > 
 > **<font color=red>git branch</font>**</br>
 > Show local branches.
 > 
 > **<font color=red>git branch -r</font>**</br>
 > Show local branches.

 > 
 > **<font color=red>git branch</font> myBranch**</br>
 > Create new branch.

 > 
 > **<font color=red>git merge</font> myBranch**</br>
 > Merge myBranch to current branch.

## Checkout


 > 
 > **<font color=red>git checkout</font> myBranch**</br>
 > Move HEAD to last commit of myBranch.

 > 
 > **<font color=red>git checkout</font> myBranch<font color=red>^</font>**
 > Move HEAD to penultimate commit of myBranch.

 > 
 > **<font color=red>git checkout</font> HEAD^**</br>
 > Moves HEAD 1 commit back from current HEAD.
 > 
 > **<font color=red>git checkout</font> HEAD^^^**</br>
 > Moves HEAD 3 commits back from current HEAD.
 > 
 > **<font color=red>git checkout</font> HEAD~12**</br>
 > Moves HEAD 12 commits back from current HEAD.

 > 
 > **<font color=red>git checkout</font> HEAD^**</br>
 > Moves HEAD 1 commit back from current HEAD in the 1st parent of a merge.
 > 
 > **<font color=red>git checkout</font> HEAD^2**</br>
 > Moves HEAD 1 commit back from current HEAD in the 2nd parent of a merge.

## Advanced Commands


 > 
 > **<font color=red>git reset</font> HEAD^**</br>
 > Moves HEAD 1 commit back as if it had never happened (can break things if pushed to remote).
 > 
 > **<font color=red>git revert</font> HEAD^**</br>
 > Create new commit that undo last commit changes.

 > 
 > **<font color=red>git cherry-pick</font> commit1 ccommit12 ccommit7**</br>
 > Add commits from other branches after HEAD.
 > 
 > **<font color=red>git rebase</font> myBranch**</br>
 > Takes commits on myBranch and replays them on current branch (from their last common parent).
 > 
 > **<font color=red>git rebase -i HEAD~</font>4**</br>
 > Opens the interactive rebase window. This allows to: change the order of the last 4 commits, omit some commits, overwrite commits.
