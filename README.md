# LOG

git log
git show
git reflog (all the actions taken)
git status
git ls-files (tracking files)
git remote show origin
git show <branch name or tag>

# ADD

git add .
git add filename
git add -u (only add modifications)

# COMMIT
git commit -m "commit description"
git commit (should open default editor)
git commit -am "commit desctiption"  (add+commit all modifided files)

# RESET
git reset HEAD filename (unstage change of the file)
git checkout -- filename (undo changes in the file)

# RENAME FILES
git mv oldname newname
git rm demo.txt

# DIFF
git diff 0821af5 HEAD
git difftool 0821af5 HEAD
git difftool -y

git diff branch1 branch2

# BRANCH
git branch -a (check branches)
git checkout -b branchname (create branch. Carries modifications to new branch)

## Delete branch
git branch -d <branch-to-remove>
git fetch -p (-p is the prune option)

git push origin :<deleted branch>

# MERGE
git checkout master
git pull
git merge updates (merges updates branch to current branch)

git pull --all (updates all tracking branches, not only the active)

## With conflict
cat filename (shows conflicts)
git mergetool

# REMOVE BRANCH
 git branch -d branchname

# TAG
## list
git tag --list 
git show tagname (shows info)


### Lightweight tag
  git tag tagname (Adds tag to current commit)
  $ git tag tagname branchname (Adds tag to last commit of the branch)

### Annotated tag 
  git tag -a tagname -m "tag info"

$ git tag -a v0.1-alpha -m "Release 0.1 (Alpha)" 0fd86ac

### Remove 
  git tag -d tagname

### Show info
$ git show v0.1-alpha
tag v0.1-alpha
Tagger: ******** <********@gmail.com>
Date:   Thu Oct 10 12:16:41 2024 +0200

Release 0.1 (Alpha)

commit 0fd86ac98358b5081f229367b1610bb000daf170 (tag: v0.1-alpha)
Author: ******** <*********@gmail.com>
Date:   Wed Oct 2 13:33:43 2024 +0200

    Updating README

diff --git a/README.md b/README.md
index 09257f3..5d6d4cb 100644
--- a/README.md
+++ b/README.md
@@ -1,3 +1,5 @@
 # Demo Project README

-This is a simple readme file
\ No newline at end of file
+This is a simple readme file
+
+## Heading 2
\ No newline at end of file


## PUSH BY TAG
git push origin tag-name (pushes tag to remote)
git push --tags (pushes all tags to remote)

# STASHING
$ git stash
Saved working directory and index state WIP on master: 234f1f5 updating ignore to exclude merge files

git stash list
stash@{0}: WIP on master: 234f1f5 updating ignore to exclude merge files

git stash pop (applies and drops stash)

git reset commitHash --soft (Changes HEAD position)
git reset commitHash --mixed (default, unstages some changes)
git reset commitHash --hard (Removes pending changes)

# UPDATE repo link
git remote set-url origin <new clone link in the updated repo url in github>
git remote show origin

git push -u origin target

# REBASE

Rewinds the current commits that are on your branch to a point to where the branch you're merging in originally diverged.
Then playing back the commits that happened on the branch that you're wanting to bring in. 
And then, after that, playing on top of that any commits that have happened on the branch that you're currently on.
Thus making any changes that you have include the changes that happened on the remote branch, but with your changes made ahead of them.
This is  a good strategy when you're working on something, and you want to make sure that your changes are ahead of whatever's going on from the remote side

$ git pull
... (changes are made on github)
... (changes are made on local)
git commit -m "commit changes"
$ git status
On branch master
Your branch and 'origin/master' have diverged
and have 1 and 1 different commit eahc, respectively
  (use "git pull" to merge the remote branch into yours)
nothing to commit, working directory clean

$ git pull --rebase
Firts, rewinding head to replay your work on top of it...
Applying: Updating ...

$ git push

# GRAPHS

$ git log --oneline --graph
* 2822e56 (HEAD -> master, origin/master) Updating readme again
* 3e4e243 updating license file
* 234f1f5 (tag: v1.0) updating ignore to exclude merge files
*   15cc581 Resolving conflict
|\
| * 1a7c28d (very-bad) very bad update
* | 5826d3c Causing issues again
|/
* 79b76e1 Adding updates from branch
* 7dd527d Adding ignore file
* 0dad58f remove myfile.txt
* 3765c3c rename and add
* d228842 deleting demo file
* 4224c88 renaming example
* f926bea adding example file
* 0fd86ac Updating README
* 14be163 Adiing both a README and a LICENSE file to the repo

-- on github
Graphs --> Network


# SSH KEY

$ cd
$ ls .ssh
ls: cannot access '.ssh': No such file or directory
$ mkdir .ssh
$ cd .ssh

$ ssh-keygen -t rsa -C "*****@gmail.com"
Generating public/private rsa key pair.

__Open id_rsa.pub, copy contents and add it to github accounts__


## Check

$ ssh -T git@github.com
The authenticity of host 'github.com (140.82.121.4)' can't be established.
ED25519 key fingerprint is SHA256:******************************************
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Enter passphrase for key '**********/.ssh/id_rsa':
Hi ********! You've successfully authenticated, but GitHub does not provide shell access.

# Basics

## Initialization
git init <repo folder name>

## States
working directory
Staging Area
Repository (.git folder)

# First commit
$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)

$ touch README.md

$ git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
nothing added to commit but untracked files present (use "git add" to track)

$ git add README.md

$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md

$ git commit -m "First commit in demo repo"
[master (root-commit) 91a67cf] First commit in demo repo
 1 file changed, 3 insertions(+)
 create mode 100644 README.md

$ git status
On branch master
nothing to commit, working tree clean


# SOCIAL CODING
Fork from https://github.com/scm-ninja/starter-web
$ git clone https://github.com/aratzpuerto/starter-web.git
$ git checkout -b feature-readme
Switched to a new branch 'feature-readme'

$ npp README.md
Add content

$ git add README.md
$ git commit -m "Adds README file"
$ git push -u origin feature-readme


# ISSUES
## Close by commit
$ git commit -m "message, close #1"

# CONFIG

git config --global user.name "*****"
git config --global user.email "*********@gmail.com"

# Quick Installation on Windows Notes

Install for Windows

Go to the Google Chrome Desktop page at https://www.google.com/chrome/browser/desktop
Click on the Download Chrome button
Accept the Terms of Service agreement (after reading, of course)
Follow the instructions through the install process
Git for Windows
Required.

Git is the source control tool used in this course. While Jenkins supports many other control control tools, Git is the most popular these days.

Install on Windows 10

Download Git for Windows directly from https://github.com/git-for-windows/git/releases/latest.
Run the installer program, follow the defaults (recommend other choices in the video, but defaults are ok too)
Open the Git Bash program, which is a Bash Shell terminal designed specifically for Git on Windows
Configure Git

Git requires your name and email address before any real work can be done. It is best to just configure Git from the start.

git config --global user.name "Your Name"
git config --global user.email "your.email@your-place.com"
Notepad++
Optional.

Windows comes with a text editor called Notepad, but it doesn't do much beyond allow you to edit text and many IT professionals prefer something more. I use a free and open-source program called Notepad++ for most of my Windows based courses. If you are happy with Notepad, then this step is optional.

Install

Download Notepad++ from https://notepad-plus-plus.org/download
Since there are many adverts on the page, ensure you select the Notepad++ Installer and not an AD by mistake.
Once the installer has finished downloading, run the installer.
Follow all the defaults through the install process with the following exceptions:
Check Create Shortcut on Desktop (personal choice)
Notepad++ System-Wide

If you plan to use Notepad++ a lot, I highly recommend adding Notepad++ to your system's PATH environment variable. You can confirm weather or not this is needed by opening a command prompt or Git Bash and type notepad++ and press the enter key. If Notepad++ launches, then no additional work is needed. If you get a Command Not Found or similar error, then add the Notepad++ install folder to the system Path variable.

Bash Configuration

Open or create the ~/.bash_profile file and add the following line:

alias npp='notepad++ -multiInst -nosession'
Git Integration

Open Git Bash and issue the command:

git config core.editor "notepad++ -multiInst -nosession"
Then test it out by:

git config --global -e
P4Merge on Windows
P4Merge for Windows which is a visual comparsion and merge resolution tool that integrates well with Git.

Install

Download P4Merge: Visual Merge Client from https://www.perforce.com/downloads/helix#clients
Once the installer has finished downloading, run the installer.
Follow all the defaults through the install process with the following exceptions:
During install, take care to only install the P4Merge Visual Merge client
Configuration

Now, let's integrate P4Merge with Git. You'll need to know where P4Merge is installed on your system -- which is normally under Program Files. With the next series of commands, you may need to modify them slightly to fit your system.

Configure P4Merge as Diff Tool in Git:

git config --global diff.tool p4merge
git config --global difftool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
git config --global difftool.prompt false
Configure P4Merge as Merge Tool in Git:

git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
git config --global mergetool.prompt false
The above commands should work, but some systems may require converting the paths to Unix friendly versions where C: is replaced with /c/.

## NOTEPAD++
/mnt/c/Program\ Files/Notepad++/notepad++.exe ~/.bash_profile
  Gehitu: alias npp='/c/Program Files/Notepad++/notepad++.exe -multiInst -nosession'

git config --global core.editor "/c/Program Files/Notepad++/notepad++.exe -multiInst -nosession"
git config --global -e

/c/Program\ Files/Perforce/p4merge.exe

## P4MERGE
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "/c/Program Files/Perforce/p4merge.exe"
git config --global difftool.prompt false

git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "/c/Program Files/Perforce/p4merge.exe"
git config --global mergetool.prompt false

##HIST
git config --global alias.hist "log --oneline --graph --decorate --all"
git config --global --list
