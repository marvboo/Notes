### Note

>This cheatsheet is based on the online version of the [Pro Git Book](https://git-scm.com/book) and
the Git man pages.

---


## Contents
---

- [Introduction](#intro)
- [File states](#states)
- [Creating / cloning a repository](#init)
  - [Config](#config)
- [Basic workflow](#workflow)
  - [Staging](#staging)
  - [Commit](#commit)
- [Branching and merging](#branching)
  - [Resolving merge conflicts](#conflicts)
- [Remotes](#remote)
- [Rebase](#rebase)
- [Stash](#stash)
- [Viewing changes](#changes)
- [Undo](#undo)
- [Utilities](#utilities)




<a id="intro"></a>

### Introduction

------------------------------------------------

Git is a tool that tracks file changes over time. It can compare changes and
revert files back to a previous state. It also tracks who made what changes.
Git works with any file type, such as source code or images. Creating new branches is
fast, which makes it easy to test new ideas or work on bug fixes.   

A repository (.git directory) can be used locally without a separate
server.  Or, the repository can be hosted on a server so clients can clone
(mirror) it. Each clone is a full copy of the repository.



<a id="states"></a>

### File states

-------------------------------

There are three main sections of a Git project:

1. Local repository
 * a compressed database of committed files
 * HEAD is a pointer to the current branch
 * also known as the .git directory
 * can also have a remote repository
2. Working directory
 * a checkout from the local repository
 * edit or create new files here
3. Staging area
 * files here are ready to be committed
 * also known as the index



To check the status of files, run the following command:

```
git status
```




<a id="init"></a>

### Creating / cloning a repository

--------------------------------

To start tracking an existing project, change to the project
directory and run:

```
git init
```

This creates a .git folder inside the project directory.

However, if it's a shared repository, use the bare option. This omits the working directory
so files can't be edited and committed there.

SSH to the server and run:

```
git init --bare yourProjectName.git
```

Commit to the bare repository by pushing to it from a local repository.



To clone an existing repository, run:

```
git clone [path or url]
```



<a id="config"></a>

### Config
------------------------------------------

Use git config to setup the repository or global options ( use `--global` ).  

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git config user.name "My Name"`                 | tell Git your name   |
| `git config user.email myname@codeDelish.com`    | tell Git your e-mail |
| `git config --edit`  				   | edit the config file for the current repository |


<br>

#### .gitignore file

Create a .gitignore file to tell Git which type of files to leave untracked.
See <https://github.com/github/gitignore> for templates.

A sample .gitignore file:

	# no .a files
	*.a

	# but do track lib.a, even though we ignore .a files above
	!lib.a

	# ignore all files in the build/ directory
	build/



<a id="workflow"></a>

### Basic workflow
------------------------------------------



<a id="staging"></a>

### Staging
------------------------------------------

```
git add <file or directory, e.g. *.cpp, . >
```


The previously tracked file that has been modified becomes staged.
Untracked files added this way are now tracked and staged.




<a id="commit"></a>

### Commit
------------------------------------------

```
git commit -m "message"
```

Staged files now committed.




<a id="branching"></a>

### Branching and merging
------------------------------------------

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git branch`                 | lists current branches <br> `-v` shows last commit on each branch <br> `-a` shows all branches (including remotes) |
| `git branch [branchName]`                 | create a new branch |
| `git checkout aBranchName`                 |  switch to an existing branch (moves the HEAD pointer to that branch) and updates the working directory <br> you should commit changes before switching branches, or stash changes |
| `git checkout -b [branchName]`                 | create a branch and switch to it (combines the 2 commands above)|
| `git merge fixesBranch`                 | merge fixesBranch into the current branch |
| `git merge --abort`                 | abort the merge, losing unstashed / uncommited changes |
| `git branch -d fixesBranch`                 | delete fixesBranch |
| `git branch -dr origin/fixesBranch`                 | delete fixesBranch on remote repository |
| `git branch -m <newBranchName>`                 | rename current branch |

<br>

To check out a previous commit, run `git checkout <commit hash>`.  You are now
in a detached HEAD state, which means HEAD points to a commit instead of a
branch.  Use git log or gitk to find the commit hash. If you modify things at
this point, create a new branch here to retain commits with `git checkout
-b newBranchName`.

To return to latest snapshot on master branch, run `git checkout master`.



<a id="conflicts"></a>

### Resolving merge conflicts
-----------------------

After merging, use `git status` to find any unmerged paths (files).
If there are conflicts, use `git mergetool` to select which version to keep, or
manually edit the file with a text editor. The file will contain
conflict markers:

	<<<<<<< HEAD:file.txt
	stuff from HEAD (master branch)
	=======
	stuff from fixesBranch
	>>>>>>> fixesBranch:file.txt


Edit the conflict marker to save the version you want.
After resolving conflicts, run `git status`, then stage and commit the changes.



<a id="remote"></a>

### Remotes
----------

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git clone [url]`                 | copies a repository and adds a remote named 'origin' <br> sets your local master branch to track default remote branch (usually master) |
| `git remote add [remoteName] [url]`              | adds a remote |
| `git remote -v`              | show configured remote server(s) |
| `git remote show [remoteName]`              | shows how a remote is configured |
| `git remote rename [oldRemoteName] [newRemoteName]`              | rename a remote |
| `git remote rm [remoteName]`              | remove a remote |
| `git fetch [remoteName]`              | downloads data to your local repository <br> you can now merge the fetched master branch into one of your own branches, <br> or check out a local branch at this point to inspect it |
| `git pull`              | fetch and merge tracked remote branch into your current branch |
| `git push [remoteName] [branchName]`              | `git push origin master` pushes your master branch to the origin remote |



<a id="rebase"></a>

### Rebase
---------

A rebase is used if you want to perform a local cleanup on branches of unneeded merge commits.


1. `git checkout fixesBranch`
2. `git rebase master`
  * replays fixesBranch commits onto the master branch
  * (moves fixesBranch to the end of master, creating new commits)
  * `git rebase -i master`	(interactive option), edit and save commit messages
  * `git rebase --onto master fixesBranch1 fixesBranch2`
    * rebase only fixesBranch2 onto master, and include common commits between fixesBranch1 and fixesBranch2
3. `git checkout master`
4. `git merge fixesBranch`
  * fast-forward master branch to include fixesBranch changes
5. `git branch -d fixesBranch`



<a id="stash"></a>

### Stash
--------

Stash saves your work in progress, allowing you to switch branches without a commit.

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git stash [-u] [--keep-index]`                 | save modified tracked files and staged changes <br> `-u` also stash untracked files <br> `--keep-index` allows you to stash modified tracked files and commit staged files (run `git add` before this command) |
| `git stash list`                 | list stored stashes |
| `git stash apply [--index]`                 | reapplies most recent stash into current branch <br> `--index` option to re-stage changes |
| `git stash apply stash@{2}`                 | reapply an older stash {2} (see `git stash list`) |
| `git stash drop`                 | remove a stash from the stack |
| `git stash branch [newBranchName] [<stash>]`                 | creates a new branch, checks out the commit with the stash, reapplies the stash, and drops the stash if it applies <br> then you commit changes to newBranchName <br> specify the stash option like `stash@{<revisionNumber>}`, otherwise defaults to last stash |




<a id="changes"></a>

### Viewing changes
----------

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git difftool`                 | show difference to previous commit |
| `git difftool anotherBranch`   | show difference between current branch and another one |
| `git difftool commitA:file.txt commitB:file.txt`   | show difference between commits |
| `gitk`   | mark a commit in gitk, then diff another commit with the marked one |


<a id="undo"></a>

### Undo
------------------------

| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git commit --amend`                 | change the commit message and commits staged files since last commit <br> don't amend your last commit if you've already pushed it (it changes the commit hash) |
| `git revert <commit>`                 | change the commit message and commits staged files since last commit <br> creates a new commit that undoes changes in <commit> (only undoes changes in that commit, not subsequent ones) <br> revert keeps revision history, as opposed to reset <br> revert can be used on public commits, reset should only be used for local commits <br> specify `HEAD` to revert the last commit |
| `git reset HEAD -- <file>`                 |  unstage a staged file (after adding) so it won't be committed <br> the dashes `--` are used to separate options and file path(s) <br> HEAD is a pointer to the last commit on current branch |
| `git reset <commitHash>`                 | revert to that commit, changes made since that commit become modified / not staged |
| `git reset --soft <commitHash>`                 | changes since are now staged for commit <br> undoes commits since and puts file back onto stage, useful for redoing last few commits as one big commit |
| `git reset --hard <commitHash>`                 | discards changes since that commit!!! |
| `git checkout -- <file>`                 | undo changes to a file, but you lose all changes!!!! <br> Alternatively, use stash or create a new branch to keep the changes |
| `git checkout <branchName or commitHash> <fileName>`                 | replaces (discarding changes ) an existing file with one from another branch |


<a id="utilities"></a>

### Utilities
------------------------


| Command                                          | Description          |
| :----------------------------------------------- | :------------------- |
| `git archive HEAD --format=zip > archive.zip`    | Export a repo |
| `git archive HEAD | gzip > archive.tar.gz`	   | Export a repo |
| `git rm [--cached] <file>`	   | Stop tracking file and deletes it from disk (removes file from staging and from working directory) <br> after committing, file is no longer tracked <br> use `--cached` to keep the file on drive without Git tracking |
| `git mv file newfile`	   | Rename a file |
| `git log --pretty=format:"%h %s" --graph`	   | Pretty logging |
| `git grep [--count] [-n] [searchTerm]`   |  options: `--and` (boolean search) `--break` (split up output) `--heading`	(easier to read) <br> `--count` list files and matches in each file <br> `-n` prints line numbers and each line of a match in a file |
| `git grep -p [searchTerm] *.cpp`	   | list methods or functions that include a match |







### Git bisect
----------

A binary search to find which commit had bad code.

1. `git bisect start`
2. `git bisect bad`
  * tell git current commit is bad
3. `git bisect good [lastKnownGoodCommit]`
  * tell git the latest commit you know was good
4. Git checks out the middle commit between the good and bad commits
5. Test your code, and tell git if this middle commit was good or bad
  * `git bisect good`
    * or
  * `git bisect bad`
6. `git bisect reset`
  * when you're done, resets HEAD to where you were before running bisect
