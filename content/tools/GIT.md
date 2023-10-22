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

`HEAD` is the location in the commit tree. It's a "pointer" to a commit. It is possible to move it with `git checkout`.

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
 > **<font color=red>git config --global gpg.format ssh</font>**</br>
 > Set SSH key method to sign commits.
 > 
 > **<font color=red>git config --global user.signingkey</font> /path/to/my/public/key**</br>
 > Specify the public key to used for signing commits (the private key has to be configured in GitHub settings.

 > 
 > **<font color=red>git config --global http.sslBackend schannel</font>**</br>
 > Switch SSL Backend from OpenSSL (default) to Schannel (Windows built-in). This is useful in an organization with enterprise-managed certificates.

## Basis


 > 
 > **<font color=red>git init</font>**</br>
 > Create git repository (local).
 > 
 > **<font color=red>git clone</font> \[REPO_URL\]**</br>
 > Clone remote repository to local machine.
 > 
 > **<font color=red>git add submodule</font> \[REPO_URL\]**</br>
 > Add a submodule (a repo in a repo). Use `--recurse-submodule` to include submodule when using git commands.

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
 > **<font color=red>git commit -S -m "</font>Commit Message<font color=red>"</font>**</br>
 > Create a commit (`-S` to sign the commit and `-m` to set the commit's message).
 > 
 > **<font color=red>git commit --amend</font>**</br>
 > Modify last commit (only works if commit was not pushed).
 > 
 > **<font color=red>git tag</font> myTag**</br>
 > Create a tag.

 > 
 > **<font color=red>git push</font>**</br>
 > Push commits to remote repository.

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
 > **<font color=red>git checkout</font> myBranch<font color=red>^</font>**</br>
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

## LFS


 > 
 > **<font color=red>git lfs install</font>**</br>
 > Initiate LFS for the repo.

 > 
 > **<font color=red>git lfs ls-files</font>**</br>
 > Show currently tracked files.
 > 
 > **<font color=red>git lfs status</font>**</br>
 > Show staged files.

 > 
 > **<font color=red>git lfs track "</font>\*.png<font color=red>"</font>**</br>
 > Update LFS config to track all new PNG files added to the repo.
 > 
 > **<font color=red>git add .gitattributes</font>**</br>
 > Add LFS config.

## History


 > 
 > **<font color=red>git show</font> myCommit**</br>
 > Display commit information.

 > 
 > **<font color=red>git log</font>**</br>
 > Show commit history.
 > 
 > **<font color=red>git log --pretty=fuller</font>**</br>
 > Commit history with more info (Committer name, commit date,...).
 > 
 > **<font color=red>git log --show-signature</font>**</br>
 > Show signature information on commit history.
 > 
 > **<font color=red>git log --oneline --graph --decorate</font>**</br>
 > Show commit history with graph.
 > 
 > **<font color=red>git log -p</font>**</br>
 > Shows difference between commits.
 > 
 > **<font color=red>git reflog</font>**</br>
 > Show local history with IDs.

## Rewrite History


 > 
 > **<font color=red>git reset</font> HEAD^**</br>
 > Moves HEAD 1 commit back as if it had never happened (can break things if the commit as laeready been pushed to remote).
 > 
 > **<font color=red>git revert</font> HEAD^**</br>
 > Create new commit that undo last commit changes.

 > 
 > **<font color=red>git cherry-pick</font> commit1 commit12 ccommit7**</br>
 > Add commits from other branches after HEAD.

 > 
 > **<font color=red>git rebase</font> myBranch**</br>
 > Takes commits on myBranch and replays them on current branch (from their last common parent).
 > 
 > **<font color=red>git rebase --root</font>**</br>
 > Takes commits from the root of the repository and replays them.
 > 
 > **<font color=red>git rebase --committer-date-is-author-date --root</font>**</br>
 > Rebase commits from the root and keep original commit date. 

 > 
 > **<font color=red>git rebase -i</font> myBranch**</br>
 > Use rebase interactive mode. Select commits that you want to modify by changing `pick` by `e` (for edit) and reorder commits as you which.
 > 
 > **<font color=red>git commit --amend --no-edit</font>**</br>
 > Make your modification to the code and then issue this command to modify the commit (`--no-edit` to keep the name of the old commit).
 > 
 > **<font color=red>git rebase --continue</font>**</br>
 > Continue to the next commit marked for edition.
 > 
 > **<font color=red>git rebase --abort</font>**</br>
 > Abort the rebase (useful in case of issues).

## Advanced Rewrite History

#### Change Commits Author Name

````bash
git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
````

 > 
 > Checkout all branches locally.

````bash
git filter-branch --force --tag-name-filter cat --commit-filter '
        if [ "$GIT_AUTHOR_NAME" = "myOldName" ];
        then
                GIT_AUTHOR_NAME="myNewName";
                GIT_AUTHOR_EMAIL="myEmail@email.com";
                GIT_COMMITTER_NAME="myNewName";
                GIT_COMMITTER_EMAIL="myEmail@email.com";
                git commit-tree "$@";
        else
                git commit-tree "$@";
        fi' -- --all
````

 > 
 > Change author and committer names for each commit authored by a specific name.

 > 
 > **<font color=red>git push --all origin --force</font>**</br>
 > Push changes (all branches) to origin. Force is required because it rewrites history.

#### Sign Old Commits of a Specific Author

````bash
git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
````

 > 
 > Checkout all branches locally.

````bash
git filter-branch --force --tag-name-filter cat --commit-filter '
        if [ "$GIT_AUTHOR_NAME" = "myName" ];
        then
                git commit-tree -S "$@";
        else
                git commit-tree "$@";
        fi' -- --all
````

 > 
 > Sign each commits authored by a specific name.

 > 
 > **<font color=red>git push --all origin --force</font>**</br>
 > Push changes (all branches) to origin. Force is required because it rewrite history.
