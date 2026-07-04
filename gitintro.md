
# Git & GitHub Notes

---

# What is Git?

**Git** = Version Control Software

* Git is software that tracks changes made to files over time.
* It allows you to go back to previous versions whenever needed.

**GitHub** = Online Hosting Service

* GitHub is an online platform used to host Git repositories.
* Git works locally, while GitHub stores repositories online.

---

# Basic Git Terminologies

## Check Git Version

```bash
git --version
```

---

## Present Working Directory

```bash
pwd
```

Shows your current working directory.

---

## Check Repository Status

```bash
git status
```

Shows:

* Modified files
* Untracked files
* Staged files
* Current branch status

---

# Configure Git (First Time Only)

Set your username and email.

```bash
git config --global user.email "tanvirmeryem2@gmail.com"

git config --global user.name "Maryyam"
```

To check all configured settings:

```bash
git config --list
```

> If the output opens in a pager, press **q** to exit.

---

# Creating a Git Repository

Initially:

```bash
git status
```

Initialize Git:

```bash
git init
```

What happens?

* A hidden `.git` folder is created.
* Git starts tracking the project.

---

# Complete Git Workflow

```
git init
      ↓
Choose Working Directory
      ↓
Write Code
      ↓
git add
      ↓
Staging Area
      ↓
git commit
      ↓
Local Repository
      ↓
git push
      ↓
GitHub Repository
```

---

# Useful Terminal Tip

To move back one directory:

```bash
cd ..
```

---

# Adding Files

Add specific files:

```bash
git add file1.txt file2.txt
```

Add everything:

```bash
git add .
```

(No need to manually add every file.)

---

# Checking Staged Files

```bash
git status
```

Example:

```text
Changes to be committed:
(use "git rm --cached <file>..." to unstage)

new file: file1.txt
new file: file2.txt
```

Git tells you exactly what will be committed.

---

# Making a Commit

```bash
git commit -m "first commit"
```

---

# Modifying an Existing File

Suppose only `file2.txt` was changed.

```bash
git status
```

Output:

```text
modified: file2.txt
```

Stage only that file:

```bash
git add file2.txt
```

Commit it:

```bash
git commit -m "file 2 modified"
```

---

# Viewing Commit History

```bash
git log --oneline
```

Example:

```text
4c812d4 (HEAD -> master) file 2 modified
53ded08 first commit
```

Shows all commits in a compact format.

---

# .gitignore

`.gitignore` contains files/folders that should **not** be tracked by Git.

Examples:

* `.env`
* `node_modules`

After creating `.gitignore`:

```bash
git add .gitignore

git commit -m "added git ignore"
```

Those files will no longer be tracked.

---

# .gitkeep

Git does **not** track empty folders.

If you want Git to keep an empty folder, create:

```
.gitkeep
```

inside that folder.

---

# Git Branches

A branch is an **alternative timeline** of your project.

`HEAD` points to the current branch.

---

## Check Current Branch

```bash
git branch
```

---

## Create a Branch

```bash
git branch bug-fix
```

---

## Switch to a Branch

```bash
git switch bug-fix
```

(or)

```bash
git checkout bug-fix
```

---

Example:

```bash
git add fixes.txt

git commit -m "add fix file"
```

Check branches:

```text
* bug-fix
master
```

---

## Switch Back to Master

```bash
git switch master
```

After switching back, files created only in `bug-fix` (like `fixes.txt`) will not appear in `master`.

---

## Create and Switch Together

```bash
git switch -c dark-mode
```

This creates **dark-mode** and immediately switches to it.

You can also switch using:

```bash
git checkout orange-mode
```

---

# Merging Branches

Suppose work is completed in:

```
bug-fix
```

Now merge it into:

```
master/main
```

```bash
git checkout master

git merge bug-fix
```

If Vim opens:

* Press **Esc**
* Type

```
:wq
```

* Press **Enter**

---

# Merge Conflict

Suppose:

* You modify `file2.txt` in **master**
* Commit it
* Switch to **bug-fix**
* Modify the **same file**
* Commit it

Now both branches have different versions of the same file.

While merging:

```bash
git status
```

Example:

```text
On branch master

You have unmerged paths.

(fix conflicts and run "git commit")
(use "git merge --abort" to abort the merge)

Unmerged paths:
(use "git add <file>..." to mark resolution)

both modified: file2.txt
```

To cancel the merge:

```bash
git merge --abort
```

---

## After Manually Fixing Conflicts

```bash
git add file2.txt

git commit -m "manual merge conflict fixed with bug-fix"
```

Example:

```text
[master f71a4b4] manual merge conflict fixed with bug-fix
```

---

# Rename a Branch

```bash
git branch -m <oldname> <newname>
```

---

# Git Diff

Used to compare changes.

## Compare Working Directory with Last Commit

```bash
git diff
```

---

## Compare Staged Changes

```bash
git diff --staged
```

These are files that have been added but not committed.

Example:

```text
diff --git a/file1.txt b/file1.txt

index 4dabddd..61c6690 100644

--- a/file1.txt
+++ b/file1.txt

@@ -3,4 +3,6 @@
```

Meaning:

* `a` → Old version
* `b` → New version
* `@@` → Line numbers

Example:

```diff
+another marketing section added to file1
```

`+` means added.

`-` means removed.

---

## Compare Two Commits

```bash
git diff aa8442a..94ef64f
```

Example:

```diff
diff --git a/file1.txt b/file1.txt

--- a/file1.txt
+++ b/file1.txt

@@ -3,4 +3,4 @@

-another 2026 in master
+another 2026 in master
```

---

# Git Stash

Git Stash is a **temporary storage area** where you can save unfinished work before switching branches.

Situation:

```bash
git checkout bug-fix
```

Error:

```text
Your local changes to the following files would be overwritten by checkout:

file1.txt

Please commit your changes or stash them before you switch branches.
```

If you don't want to commit yet:

```bash
git stash
```

Example:

```text
Saved working directory and index state WIP on master
```

Now switching works:

```bash
git checkout bug-fix
```

---

## Apply Stash

```bash
git stash apply
```

Applies the saved work.

---

## Pop Stash

```bash
git stash pop
```

Applies the stash **and removes it** from the stash list.

---

# GitHub

GitHub is used to **store Git repositories online**.

Git manages the version history locally.

GitHub hosts those repositories on the cloud, making it easy to:

* Back up code
* Collaborate with others
* Share projects
* Push and pull changes



git branch -M main 
it changes the master name to main
git remote add origin https://github.com/meryem-cmd/my-gitndgithub-notes
origin is the name given to the remote repo i.e. github one 
git remote -v
origin  https://github.com/meryem-cmd/my-gitndgithub-notes (fetch)
origin  https://github.com/meryem-cmd/my-gitndgithub-notes (push)
this gives the relation that what repo are you fetching and what u are pushing in github
git push -u origin main 















GIT:
version control software
git -> software that track files for changes , github ->online service to host that software

Terminologies:
git --version   (to check the version of git)
pwd             (present working directory)
git status
created four folders one,two,three,four
git config --global user.email "tanvirmeryem2@gmail.com" 
git config --global user.name "Maryyam"  
has set the email and name 

to check all the settings that have changed 
git config --list   (use q when you want to move to new command)


Creating a repo:
git status

git init   (now a repo is created and a .git folder is create inside it and tracking has been started)
write -> add -> commit

Complete git flow:
git init -> choose the working directory(chose one in this case) -> git add -> staging area -> git commit -> repo  -> git push 

fun fact: to go back to root folder from an inside folder enter cd .. 


git add file1.txt file2.txt  
git add .  (no need for manual adding all the files)

git status 
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file1.txt
        new file:   file2.txt
it will tell everything that needs to be committed

git commit -m "first commit"

now if you have only worke don single file
now with git status 
this will be the output modified:   file2.txt 
git add file2.txt
git commit -m "file 2 modified"


git log --oneline
4c812d4 (HEAD -> master) file 2 modified
53ded08 first commit
to check what u have done

in .gitignore all those files r to be placed that you dont want to push such as .env, node_modules
git add .gitignore   
git commit -m "added git ignore" now these wont be getting tracked

those folders which dont have any data rn but could be in the future in them a .gitkeep file is created


Git branches:
alternative timeline
head -> points to the current branch
git branch (to check on which branch u r currently at)
git branch bug-fix (now a new branch bug-fix is created )
git switch bug-fix (with this you can switch to that branch)
 git add fixes.txt
 git commit -m "add fix file"


 git branch
* bug-fix
  master

now to go to master
git switch master
ab ap master p agye ho toh jonsi file hai uski fixes.txt wali woh ab dekhegi h nai


git switch -c dark-mode 
now a branch dark-mode is created asw shifted here
git checkout orange-mode isse b shift hskte

now some work has been done in bug fix branch and also committed
so bug-fix => master/main
git checkout master      
now we have to attach bug-fix 
git merge bug-fix


now done many changes in branch master asw in bug-fix so 
git merge bug-fix

press esc then :wq then press enter if vim opens


Merge conflict: suppose u move on to main branch and change one file there then add and commit it and then moved to bug-fix branch and changed that same exact file and add and commit it , now in both branches both the files r different 


git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   file2.txt

no changes added to commit (use "git add" and/or "git commit -a")
git merge --abort (for now merging is aborted)

after manually fixing the conflicts:
git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   file2.txt

no changes added to commit (use "git add" and/or "git commit -a")

git add file2.txt                   
PS C:\internship\gitndgithub\one> git commit -m "manual merge conflict fixed with bug-fix"
[master f71a4b4] manual merge conflict fixed with bug-fix


Rename a branch:
git branch -m  <oldname> <newname>



git diff 
batana prta kin k bech m comparison jate
git diff --staged
staged  is what we have added but not commited
(a is file A(indicated by ---), b is file B(indicated by +++))
diff --git a/file1.txt b/file1.txt
index 4dabddd..61c6690 100644
--- a/file1.txt
+++ b/file1.txt
(@ indicates line number)
@@ -3,4 +3,6 @@ now more content is added
 
 
 
+another marketing section added to file1 

Comparison between two files:
git diff aa8442a..94ef64f
diff --git a/file1.txt b/file1.txt
index 4dabddd..430f0ab 100644
--- a/file1.txt
+++ b/file1.txt
@@ -3,4 +3,4 @@ now more content is added
 
 
 
-another 2026 in master
+another 2026 in master
:


Git stash: okay so it is a temp location where you store your work before moving on to another branch and after coming you can apply or drop that work
temproray location 
PS C:\internship\gitndgithub\one> git checkout bug-fix
error: Your local changes to the following files would be overwritten by checkout:
        file1.txt
Please commit your changes or stash them before you switch branches.
Aborting 


if you are not in the mood of like commiting your changes before switching then you can use git stash to temp store 
git stash
Saved working directory and index state WIP on master: aa8442a manual merge conflict fixed with bug-fix for file1.txt
PS C:\internship\gitndgithub\one> git checkout bug-fix
Switched to branch 'bug-fix'

git stash apply
apply the stash asw drop in that branch
git stash pop



GITHUB:
saves the repo


