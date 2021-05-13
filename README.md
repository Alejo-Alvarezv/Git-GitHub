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
<img height="400" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20init%201.png">
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
- **Tracket**: The files live inside the repository are updated and have no pending changes
- **Modified**: means that you have modified the file but have not yet confirmed them to your database
- **Committed**: files that are safely stored in your database


**git show**
shows all the changes we have made, this includes the lines we have changed, when and who made those changes

```sh
git show
```

**git log**
It allows us to see the complete history of a file

```
git log <file>
```

## Create a commit (git add and git commit)

**add**
<p align="center">
<img height="400" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20add%201.png">
</p>

Send your file to **stanging area** where it is temporarily saved before being sent to the **repository**

```sh
git add <file>
```

Add all the files for the commit (**.** refers to the folder where is located **./**).

```sh
git add . 
git add -A
```

**commit**
<p align="center">
<img height="400" src="https://github.com/alejoalvarez/Images/blob/trunk/git/git%20commit%201.png">
</p>

send the file to the **repository** committing the changes made and leaving a user message when adding -m

```sh
git commit -m "Message for commit"
```

This commando combenes add and commit (It will only work if the files have already been previously applied a **git add**):

```sh
git commit -am "Message"
```
