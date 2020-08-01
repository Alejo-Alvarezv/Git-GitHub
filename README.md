### Basic configuration
Configure name that come out in commits.
```
$ git config --global user.name "Alejo"
```
Configure email.
```ssh	
$ git config --global user.email alejo@ejemplo.com
```
Color frame for commands.
```ssh
$ git config --global color.ui true
```

## Create repository
We start GIT in the folder where the project is:
```ssh
$ git init
```

The first commit.
```ssh
$ git commit -m "description"
```
Save to repository.
```ssh
$ git push origin master
```

## GIT CLONE
Clone the repository.
```ssh
$ git clone <url>
```

## GIT ADD
Add all the files for the commit.
```ssh
$ git add . 
```
We add the files for the commit.
```ssh
$ git add <file>
```
We add all the files for the commit omitting the new ones.
```ssh
$ git add --all 
```
We add all files with the specified extension for example (.txt).
```ssh
$ git add *.txt
```
We add all the files inside a directory and with a specific extension.
```ssh
$ git add src/*.txt
```
We add all the files inside a directory.
```ssh
$ git add src/
```
## GIT COMMIT

Upload the changes made to the HEAD.
```ssh
$ git commit -m "Text that identifies why the commit was made"
```
Add and load the changes made to the HEAD.
```ssh
$ git commit -a -m "Text that identifies why the commit was made"
```
If there are conflicts it shows them.
```ssh
$ git commit -a 
```
Add to the last commit, this is not shown as a new commit in the logs. A new message can be specified.
```ssh
$ git commit --amend -m "Text that identifies why the commit was made"
```
## GIT PUSH

Upload to repository.
```ssh
$ git push <origin> <branch>
```
Upload a tag.
```ssh
$ git push --tags
```
## GIT LOG
Show the logs for commits.
```ssh
$ git log
```
Show changes on the commits.
```ssh
$ git log --oneline --stat
```
Show graphs on the commit.
```ssh
$ git log --oneline --graph
```
## GIT DIFF

Show changes made to a file.
```ssh
$ git diff 
```
## GIT HEAD
Remove a file from the commit.
```ssh
$ git reset HEAD <file>
```
Returns the last commit that was made and puts the changes in staging.
```ssh
$ git reset --soft HEAD^
```
Returns the last commit and all changes.
```ssh
$ git reset --hard HEAD^
```
Returns the last 2 commits and all changes.
```ssh
$ git reset --hard HEAD^^
```
Rollback merge/commit.
```ssh
$ git log
$ git reset --hard <commit_sha>
```
## GIT REMOTE

Add remote repository.
```ssh
$ git remote add origin <url>
```
Change the remote.
```ssh
$ git remote set-url origin <url>
```
Delete repository.
```ssh
$ git remote rm <name/origin>
```
List the repositories.
```ssh
$ git remote -v
```

Show all remote branches.
```ssh	
$ git remote show origin
```
Clean up all removed branches.
```ssh
$ git remote prune origin 
```
## GIT BRANCH

Create a branch.
```ssh
$ git branch <nameBranch>
```

List all branches.
```ssh
$ git branch
```
-d command removes the branch and joins it to the master.
```ssh
$ git branch -d <nameBranch>
```
Delete without asking.
```ssh
$ git branch -D <nameBranch>
```
## GIT TAG
Show a list of all tags.
```ssh
$ git tag
```
Create a new tag.
```ssh
$ git tag -a <version> - m "This is the version X"
```
## GIT REBASE

The rebases are used when we work with branches this makes the branches catch up with the master without affecting it.

Join the current branch with the master, this cannot be seen as a merge.
```ssh
$ git rebase
```
When a conflict occurs you don't give the following options:

When we resolve conflicts --continue continue the rebase sequence where it paused.
```ssh	
$ git rebase --continue 
```
Skip the conflict and go your way.
```ssh
$ git rebase --skip
```
Returns everything at the beginning of the rebase.
```ssh
$ git reabse --abort
```
To rebase a specific branch.
```ssh	
$ git rebase <nameBranch>
```
## Another commands

List a current repository status with list of modified or added files.
```ssh
$ git status
```
Removes a file from HEAD and sets it to not working.
```ssh
$ git checkout -- <file>
```

Create a branch based on one online.
```ssh
$ git checkout -b newlocalbranchname origin/branch-name
```
Check for new changes and update the repository.
```ssh
$ git pull origin <nameBranch>
```
Change the branche.
```ssh
$ git checkout <nameBranch/tagname>
```
Check for new changes and update the repository.
```ssh
$ git merge <nameBranch>
```
Verify changes in the online repository with the local.
```ssh
$ git fetch
```
Remove a file from the repository.
```ssh
$ git rm <file> 
```
## Fork

Download remote form a fork
```
$ git remote add upstream <url>
```

Merge with master from a fork
```
	git fetch upstream
	git merge upstream/master
```
