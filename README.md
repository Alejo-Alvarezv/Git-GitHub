# Git tutorial

## What is git

- Performance
- Security
- Flexibility

### Performance

- The basic performance characteristics of Git are very strong in comparison with many alternatives. The algoritms implemented inside git take advantage of deep konwlegde about common attributes of real source code file trees.
- Git is not fooled by the names of the files when determining what the storage and version history of the file tree should be, instead Git focuses on the file content itself. The object format of Git's repository files uses a combination of delta encoding (storing content differences), compression and explicitly stores directory contents and version metadata objects.
- Being distributed enables significant performance benefits as well.

### Security

- Git has been designed with the integrity of managed source code as a top priority.
- All object in the git repository are secured with a crytographically secure hasing algorithm (SHA1)
- You can sure you have an authetic content history of your source code

### Flexibility

- Git is flexible in several respects: in support for various kinds of nonlinear development workflows, in its efficiency in both small and large projects and in its compatibility with many existing systems and protocols.

## Basic information about git

- Was created by Linux Torvalds
- Git is different to github
- Keep track of changes
- Coordinate the work of several people or work teams
- **Working directory**: It is a copy of a version of the project. These files are taken from the compressed database in the **.git** directory and placed on disk so that you can use or modify them.
- **Stanging area**: It is the place where the changes are temporarily saved, to later be permanently saved in the repository, sometimes it is called "Index"
- **.git (local repository)** : is where the change history of our files is stored, metadata and the object database are stored, it is the most important part of git
- gitk - tool for show git graphically

<p align="center">
<img height="200" src="https://github.com/alejoalvarez/Images/blob/trunk/git/basic%20information%20about%20git%201.png">
</p>

- Git is a VCS
- Save only the changes made in any file or project making clear
    - where did they? 
    - where did they run?
    - who did it?
- We can travel back in time to review changes made in the past to the git repository

<p align="center">
<img height="140" src="https://github.com/alejoalvarez/Images/blob/trunk/git/basic%20information%20about%20git%202.png">
</p>

## Basic configuration git

- List all configurations

```sh
git config --list  or git config -l
```

- Configure name that come out in commits.

```sh
git config --global user.name "Alejo"
```

- Configure email

```sh
git config --global user.email alejo@ejemplo.com
```

- Color frame for commands.

```name
git config --global color.ui true
```

- In order to disable SSL certificates and download the project locally.

```sh
git config --global http.sslVerify false
```

- To allow downloading with proxy problems.
```sh
git config --global --unset http.proxy 
```

- To change the editor when you need to enter information.
```sh
git config --global core.editor "code --wait" 
```

- To remove configured parameters.
```sh
git --global --unset-all core.editor 
```

- To remove an specific parameter.
```sh
git --global --unset-all user.name "Name user"
```
- Change a global configuration.
```sh
git config --global --replace user.name "Modified name" 
```

## Git help

Provides a description about the command to use

```sh
git help config <command>
```

## Create a repository (git init)

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20init%201.png">
</p>

We start GIT in the folder where the project is:

```sh
git init <repository-name>
```

This command create a hidden folder called **.git** (local repository) where the project's atomic change log will be saved and create a space in RAM called **stanging area**

## Validate file status (git status, git log, git show)

These commands are to observe how the files and commits are behaving in our work environment

**git status**
It allows me to know the status of files and folders

```sh
git status
```

States for files
- **Untracket**: The file does not live in git, only on the disk (it is only in the **working directory**)
- **Unstaged**: These are files that git has records of its changes but they are out of date.
- **Staged**: Files that have been sent staged with **git add**
- **Tracket**: The files live inside the **repository** are updated and have no pending changes
- **Modified**: means that you have modified the file but have not yet confirmed them to your database
- **Committed**: files that are safely stored in your database

**git show**
shows all the changes we have made, this includes the lines we have changed, when and who made those changes

```sh
git show
```

**git log**
It allows us to see the complete history of a file

See all files
```sh
git log
```

See an specify file
```sh
git log <file-name>
```

Allows you to see the commits and mergers graphically
```sh
git log --online --decorate
git log --oneline --graph
```

Save log into a file
```sh
git log > log-name.txt
```

Look for the commits that fulfill as is what is written in quotes
```sh
git log --grep "Example"
```

Look for commits that comply regardless of upper or lower case
```sh
git log --grep "Example" -i
```

look for commits by an specific author.
```sh
git log --author "name_author"
```

## Create a commit (git add and git commit)

**add**
<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20add%201.png">
</p>

Send your file to **stanging area** where it is temporarily saved before being sent to the **repository**, move a file from untracked or unstaged to staged

```sh
git add <file>
```

Add all the files for the commit (**.** refers to the folder where is located **./**).

```sh
git add . 
git add -A
```

* add all files with the specified extension for example (.txt).
```sh
git add *.txt
```

* add all the files inside a directory and with a specific extension.
```sh
git add src/*.txt
```

* add all the files inside a directory.
```ssh
git add src/
```

**commit**
<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20commit%201.png">
</p>

send the file to the **repository** committing the changes made and leaving a user message when adding -m (move the files from **working directory**  to **local repository**)

```sh
git commit -m "Message for commit"
```

This commando combenes add and commit (It will only work if the files have already been previously applied a **git add**):
git add + git commit 

```sh
git commit -am "Message"
```

* Add to the last commit, this is not shown as a new commit in the logs. A new message can be specified.
```sh
git commit --amend -m "Text that identifies why the commit was made"
```

## Differences between commits (git diff)

It allows us to see the difference between one version and another specifically, to obtain the IDs (SHA1) of your commits you use the **git log** command, git will give you the response with the changes made between the two commits (recommended to put the oldest commit at the beginning, since git takes the former as the older of the two)


Compare working directory with stanging area

```sh
git diff
```

```sh
git diff commit1 commit2
```

```sh
git diff <tag1> <tag2>
```

## Branches (git branch)

When you create your repository in your working folder, a main branch called **master** is created by default (this name can be modified)

it can be seen as the linear map of the commits you have made to the file

Branches are the way to make changes in our project without affecting the workflow of the main branch, this is because we want to work in a very specific part of the application or because we simply want to experiment

The HEAD header represents the branch and the commit of that branch where we are working, by default this header will appear in the last commit of our main branch,

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20branch.png">
</p>

**branch**

Create a branch
```sh
git branch <name-branch>
```

List all branches
```sh
git branch -l 
```

Another way for list all branches 
```sh
git show-branch --all
```

List branches and show the last commit
```sh
git branch -v
```

Rename branch
```sh
git branch -m <old-name-branch> <new-name-branch>
```

Delete a branch
```sh
git branch -d <branch-name>
```

Delete without asking.
```sh
git branch -D <name-branch>
```

Move all existing changes in your master branch to the new main branch
```sh
git branch -M <main>
```

## Checkout (git checkout)

You use checkout to create a new branch from the commit you want of your master branch, this branch serves you to make experiments, changes or repair errors in your main code without affecting it

Change the branche.
```sh
git checkout <name-branch>
git checkout <branch> <file>
```

creates a branch and positions itself on it
```sh
git checkout -b <branch-name>
```

Create a branch based on one online.
```sh
git checkout -b <new-local-branch-name> origin/branch-name
```

Allows you to go back to any previous version without deleting the file's history
```sh
git checkout <commit-id>
```

Removes a file from HEAD and sets it to not working.
```sh
git checkout -- <file>
```

## Merge (git merge)

To join the changes between branches, merge is used, in this way the two branches will be joined to form a single


* Join the branch
```sh
git merge <name-banch>
```

it should be noted that there may be conflicts between the branches


## go back in time (git reset)

If you "want to go back in time" and go back to a previous version of your file you can use **git reset**

**git reset** Allows you to go back in time without being able to go back to the future

Ways to use git reset:

- delete all the registration information that we have even what is in stanging area

**reset hard**
- delete all the registration information that we have even what is in stanging area
```sh
git reset --hard 
```

- starting from commit-id, remove all future commits to it and does not and keep changes in stanging are or in working directory
```sh
git reset <commit-id> --mixed
```

**reset soft**
- delete the changes you have made to your file but what is in stanging remains there, give you the possibility to apply the changes later.
```sh
git reset --soft
```

- starting from commit-idX, remove all future commits to it and keep all those changes in the stanging area
```sh
git reset <commit-id> --soft 
```

**reset mixed**
- match the local repository to the working directory
```sh
git reset --mixed
```

- starting from commit-id, remove all future commits to it and keep all those changes in the working directory
```sh
git reset <commit-id> --mixed
```

**reset HEAD**
- move the changes from stanging area to unstaged, the last changes are kept, the repository still has the file with the changes made in the commit
```sh
git reset --HEAD
```

To recover the SHA1 lost by a reset.
```sh
git reflog 
```

## Remove file (git rm)

Remove a file from the repository.
```sh
git rm <file> 
```

Return form the stangin area to working directory (delete file from stanging)
```sh
git rm --cached <file>
```

It allows removing a commit from one branch and putting it in another, this can happen when changes are added to a branch that were not due, but to avoid losing those changes, use that command.
```sh
git cherry-pick <SHA1> 
```

## Difference between git reset and git rm

- ```git rm``` just delete files (either from stanging or from the workind directory

- ```git reset``` send you to old versions and delete files, history and records

<p align="center">
<img height="350" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20reset%20vs%20git%20rm.png">
</p>


## Clone remote repository (git clone)

We obtain a copy of the master or main branch from the remote repository to the **working directory** and create the database of all the historical files in the **local repository**, leaving it stanging clean and ready to be used

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20push%201.png">
</p>

## Upload changes to the remote repository (git push)

It allows us to send the changes to the remote server or repository

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20push%201.png">
</p>

Upload to repository.
```sh
git push origin <branch-name>
```

Upload a tag.
```sh
git push --tags
```

Upload the tags from master to origin.
```sh
git push origin master --tags
```

Send from a local branch to a remote branch.
```sh
git push origin <branch-local>:<branch-remote>
```

Remove remote branch
```sh
git push origin -- delete <name-branch>
```

## bring updates from the remote (git fetch) 

It is used to bring updates from the remote server and save them in our local repository (in case there are, of course)

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20fetch%201.png">
</p>

```sh
git fetch 
```

## Combine changes to working directory (git merge)

It is used to combine the latest changes from the remote server and our working directory, it is used in conjunction with the **git fetch** command

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20merge%201.png">
</p>


The git merge command allows us to create a new commit with the combination of two branches (the branch where we are when we execute the command and the branch that we indicate after the command).

Create a new commit in the master branch by combining the **branch-name** changes:
```sh
git checkout master
git merge <branch-name>
```

if we have made a merge with a branch with which we did not want
```sh
git reset --merge HEAD
```

## bring updates from the remote  (git pull =  git fetch + git merge)

Join **git fetch** and **git merge**, basically used to fetch updates from the remote server by saving them to our local repository, and merge the latest changes from the remote server into our working directory

<p align="center">
<img height="250" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20pull%201.png">
</p>

Check for new changes and update the repository.
```sh
git pull origin <nameBranch>
```

this way we can have an updated copy of our project stored on the remote server

## Remote

if we want to connect the github repository with our local repository we must execute the following:

- Add remote repository.
```sh
git remote add origin <url-github>
```

- List the repositories.
```sh
git remote -v
```

- Change the remote.
```sh
git remote set-url origin <url>
```

- Delete repository.
```ssh
git remote rm <name/origin>
```

- Show all remote branches.
```sh	
git remote show origin
```

- Clean up all removed branches.
```sh
git remote prune origin 
```

## Asign version to commits (git tag)

The tags allow us to assign versions to the commits with the most important or significant changes in our project.

Show a list of all tags.
```sh
git tag
```

Create a new tag.
```sh
git tag -a <version-or-name> - m "This is the version X"
```

create a new tag and assign it to a commit:

```sh
git tag -a <name-tag> <id-commit>
```

delete a tag in the local repository:

```sh
git tag -d <name-tag>
```

list the tags of our local repository:

```sh
git tag 
```
list the tags of our local repository with the HASH:
```sh
git show-ref --tags
```

post a tag to the remote repository
```sh
git push origin --tags
```

delete a tag from the remote repository:

```sh
git tag -d <name-tag> and
git push origin :refs/tags/name-tag
```

## Fork 

Download remote form a fork
```sh
git remote add upstream <url>
```

Merge with master from a fork we can use 
```
git pull upstream <branch>
```

## Rebase (git rebase)

The rebases are used when we work with branches this makes the branches catch up with the master without affecting it.

Join the current branch with the master, this cannot be seen as a merge.
```sh
git rebase
```

When a conflict occurs you don't give the following options:

When we resolve conflicts --continue continue the rebase sequence where it paused.
```sh	
git rebase --continue 
```

Skip the conflict and go your way.
```sh

git rebase --skip
```

Returns everything at the beginning of the rebase.
```sh
git reabse --abort
```

To rebase a specific branch.
```sh	
git rebase <nameBranch>
```
