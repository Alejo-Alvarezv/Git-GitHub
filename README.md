### Basic configuration (git config --global)
List all configurations.
```yaml 
-  git config --list 
-  git config -l
```
`Configure name that come out in commits.`
```
$ git config --global user.name "Alejo"
```
`Configure email.`
```yaml	
$ git config --global user.email alejo@ejemplo.com
```
`Color frame for commands.`
```ssh
$ git config --global color.ui true
```
`In order to disable SSL certificates and download the project locally.`
```ssh
$ git config --global http.sslVerify false
```
`To allow downloading with proxy problems.`
```ssh
$ git config --global --unset http.proxy 
```
`To change the editor when you need to enter information.`
```ssh
$ git config --global core.editor "code --wait" 
```
`To remove configured parameters.`
```ssh
$ git --global --unset-all core.editor 
```
`To remove an specific parameter.`
```ssh
$ git --global --unset-all user.name "Name user"
```
`Change a global configuration.`
```ssh
$ git config --global --replace user.name "Modified name" 
```
## Create repository (git init)
`We start GIT in the folder where the project is:`
```ssh
$ git init
```

## Clone repository (git clone)
`Clone the repository.`
```ssh
$ git clone <url>
```

## Add file to the stanging area (git add)
`Add all the files for the commit.`
```ssh
$ git add . OR
$ git add -A
```
`We add the files for the commit.`
```ssh
$ git add <file>
```
`We add all the files for the commit omitting the new ones.`
```ssh
$ git add --all 
```
`We add all files with the specified extension for example (.txt).`
```ssh
$ git add *.txt
```
`We add all the files inside a directory and with a specific extension.`
```ssh
$ git add src/*.txt
```
`We add all the files inside a directory.`
```ssh
$ git add src/
```
##  Commit (git commit)
`Upload the changes made to the HEAD.`
```ssh
$ git commit -m "Text that identifies why the commit was made"
```
`Add and load the changes made to the HEAD.`
```ssh
$ git commit -a -m "Text that identifies why the commit was made" OR
$ git commit -am "Text that identifies why the commit was made"
```
`If there are conflicts it shows them.`
```ssh
$ git commit -a 
```
`Add to the last commit, this is not shown as a new commit in the logs. A new message can be specified.`
```ssh
$ git commit --amend -m "Text that identifies why the commit was made"
```

## Branches (git branch)
`Create a branch`
```ssh
$ git branch <nameBranch
```
`Delete a branch`
```ssh
$ git branch -d <branch-name>
```

`List branches and show the last commit`
```ssh
$ git branch -v ---- listar ramas y muestra último commit 
```
`Rename branch`
```ssh
$ git branch -m <OldNamebranch> <NewNameBranch>
```

## Push changes(git push)
`Upload to repository.`
```ssh
$ git push <origin> <branch>
```
`Upload a tag.`
```ssh
$ git push --tags
```
`Upload the tags from master to origin.`
```ssh
$ git push origin master --tags
```
`Send from a local branch to a remote branch.`
```ssh
$ git push origin <branch-local>:<branch-remote>
```
`Remove remote branch`
```ssh
$ git push origin -- delete <name-branch>
```

## History commits (git log)
`Show the logs for commits.`
```ssh
$ git log
```
`Show the logs for commits about an specific file.`
```ssh 
$ git log <File_Name>
```
`Show changes on the commits.`
```ssh
$ git log --oneline --stat OR
$ git log --oneline --decorate
```
`Show graphs on the commit.`
```ssh
$ git log --oneline --graph
```
`Save log into a file`
```ssh
$ git log > log.txt
```
`look for commits that comply regardless of upper or lower case`
```ssh
$ git log --grep "INVIE" -i
```
`look for commits by an specific author.`
```ssh
$ git log --author "Name_Author"
```
## Differences (git diff)
`Show changes made to a file.`
```ssh
$ git diff <tag> 
$ git diff <SHA1> 
$ git diff <old_tag> <tag2> 
```
## Reset file (git reset)
`Remove a file from the commit.`
```ssh
$ git reset HEAD <file>
```
`Returns the last commit that was made and puts the changes in staging.`
```ssh
$ git reset --soft HEAD^
```
`Returns the last commit and all changes.`
```ssh
$ git reset --hard HEAD^
```
`Returns the last 2 commits and all changes.`
```ssh
$ git reset --hard HEAD^^
```
`Rollback merge/commit.`
```ssh
$ git log
$ git reset --hard <commit_sha>
```
`To recover the SHA1 lost by a reset.`
```ssh
$ git reflog 
```
## Remote

`Add remote repository.`
```ssh
$ git remote add origin <url>
```
`Change the remote.`
```ssh
$ git remote set-url origin <url>
```
`Delete repository.`
```ssh
$ git remote rm <name/origin>
```
`List the repositories.`
```ssh
$ git remote -v
```
`Show all remote branches.`
```ssh	
$ git remote show origin
```
`Clean up all removed branches.`
```ssh
$ git remote prune origin 
```
## Branch (git branches)
`Create a branch.`
```ssh
$ git branch <nameBranch>
```
`List all branches.`
```ssh
$ git branch
```
`-d command removes the branch and joins it to the master.`
```ssh
$ git branch -d <nameBranch>
```
`Delete without asking.`
```ssh
$ git branch -D <nameBranch>
```
## Tags (git tags)
`Show a list of all tags.`
```ssh
$ git tag
```
`Create a new tag.`
```ssh
$ git tag -a <version> - m "This is the version X"
```
## Rebase (git rebase)

The rebases are used when we work with branches this makes the branches catch up with the master without affecting it.

`Join the current branch with the master, this cannot be seen as a merge.`
```ssh
$ git rebase
```
When a conflict occurs you don't give the following options:

`When we resolve conflicts --continue continue the rebase sequence where it paused.`
```ssh	
$ git rebase --continue 
```
`Skip the conflict and go your way.`
```ssh
$ git rebase --skip
```
`Returns everything at the beginning of the rebase.`
```ssh
$ git reabse --abort
```
`To rebase a specific branch.`
```ssh	
$ git rebase <nameBranch>
```

## Status(git status)
List a current repository status with list of modified or added files.
```ssh
$ git status
```

# Checkout (git checkout)
`Removes a file from HEAD and sets it to not working.`
```ssh
$ git checkout -- <file>
```
`Create a branch based on one online.`
```ssh
$ git checkout -b newlocalbranchname origin/branch-name
```
`Change the branche.`
```ssh
$ git checkout <nameBranch/tagname>
```

## Pull changes (git pull)
`Check for new changes and update the repository.`
```ssh
$ git pull origin <nameBranch>
```

## Save version (git tag)
`Allows us to add tags to our changes.`
```ssh
$ git tag
$ git tag -a (-a annotations)
$ git tag -m (-m message)
$ git tag -l (-l show the list of tags)
$ git tag -f (-f rename tag)
$ git tag -d (-d delete)
```

## Another commands 

`Check for new changes and update the repository.`
```ssh
$ git merge <nameBranch>
```
`Verify changes in the online repository with the local.`
```ssh
$ git fetch
```
`It shows us the changes that have existed over the last two commit`
```ssh
$ git show
```

## Remove file (git rm)
`Remove a file from the repository.`
```ssh
$ git rm <file> 
```
`Return form the stangin area to working directory (delete file from stanging)`
```code
$ git rm --cached <file>
```
`It allows removing a commit from one branch and putting it in another, this can happen when changes are added to a branch that were not due, but to avoid losing those changes, use that command.`
```ssh
$ git cherry-pick <SHA1> 
```

## Fork
`Download remote form a fork`
```
$ git remote add upstream <url>
```
`Merge with master from a fork`
```
$ git fetch upstream
$ git merge upstream/master
```
