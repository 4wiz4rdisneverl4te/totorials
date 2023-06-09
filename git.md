# Git

Git is a distributed version control system that allows multiple developers to collaborate on a project and track changes to source code or any other set of files.

# Intro
Easy way to create a repository and add a remote origin
```
echo "# repository_name" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:user_name/repository_name.git
git push -u origin main
```

<br>

Easy way to show graph of branches

```
git log --graph --oneline --decorate --all
```

# Commands

## Clone
Clone a repository from remote

```
git clone <repository-url>
```

<br>

When you clone a repository you dont need make "git remote add origin ...." because the remote is set automatically

## config
Configure Git on your local machine. It allows you to set various Git configuration options, such as your name, email, preferred text editor, default branch name, and more.

<br>

Set your name
```
git config --global user.name "Your Name"
```

<br>

Set your preferred text editor

```
git config --global user.email "your@example.com"
```

<br>

Set your preferred text editor

```
git config --global core.editor "your-editor"
```

<br>


Set the default branch name
```
git config --global init.defaultBranch "main"
```

<br>

List your Git configuration

```
git config --list
```

##  Init
initialize a new Git repository in an existing directory. 

```
git init
```

## status

Display the current status of your Git repository. It shows information about the branch you are on, the state of your files (tracked, modified, untracked), and any pending changes that are in the staging area.

```
git status
```

## Add
Add changes or new files to the staging area. The staging area is an intermediate step before committing changes to the repository.

<br>

You can specify the names of specific files or directories that you want to add to the staging area. For example:

```
git add file1.txt       # Adds a specific file
git add directory/      # Adds all files in a directory
```

<br>

To add all modified files: You can use a period (.) to add all modified files in the current directory and its subdirectories

```
git add .
```
<br>

If you want more control over which changes to add, you can use the -p or --patch option with git add to interactively select and add changes:

```
git add -p
```

## Commit

Create a new commit, which represents a snapshot of the current state of the repository. Commits in Git are used to record changes made to files and provide a meaningful description of those changes.
```
git commit -m "confirmation message"
```

## Merge
Combine changes from one branch into another branch. It integrates the changes made in the source branch into the target branch, creating a new merge commit.

<br>

If you have a branch called feature and you want to merge its changes into the main branch first checkout to main branch and them
```
git merge feature
```

## Checkout
Switch between branches or restore files from different commits. It allows you to navigate between different states of your project.

<br>

Switch to an existing branch
```
git checkout <branch-name>
```

<br>

Create a new branch and automatically switch to it in a single step

```
git checkout -b <branch-name>
```
## Tag
Add a tag to a specific commit in Git

<br>

Simple tag 

```
git tag <tag-name> <commit>   # <commit> can be empty to put a tag in the current commit
```

<br>

Push the tags to a remote repository,

```
git push --tags
```

## Push
Push your local changes to a remote repository in Git

```
git push <remote-name> <branch-name>
```

## Pull
Fetch changes from a remote repository and merge them into the current branch.

```
git pull <remote-name> <branch-name>
```

<br>


If you want to pull changes from the default remote repository named "origin" into the current branch, you can simply use

```
git pull
```

## Remote
List the remote repositories configured in your Git repository

```
git remote -v
```

<br>

Add remote repository

```
git remote add <remote-name> <remote-url>
```

<br>

Example to add Github

```
git remote add origin git@github.com:user_name/repository:name.git
```

## Branch

Manage branches within a repository. Branches allow you to work on different lines of development independent of each other, making it easier to work on new features, bug fixes, or experiments without affecting the main codebase.    
<br>

This command lists all the branches in the repository. The currently active branch is indicated with an asterisk (*) symbol.
```
git branch
```

<br>

This command creates a new branch with the specified name. The new branch will be created based on the current commit you're on.
```
git branch <branch-name>
```

<br>

This command creates a new branch with the specified name and automatically switches to it.  
```
git checkout -b <branch-name>
```
  
<br>  

This command deletes the specified branch. Note that you cannot delete the branch you're currently on. You may need to switch to a different branch first using git checkout.
```
git branch -d <branch-name>
```

<br>

This command renames an existing branch. It changes the name of the specified branch to the new name.
```
git branch -m <old-branch-name> <new-branch-name>
```

<br>

This command lists all the remote branches in the repository. Remote branches are branches on the remote server (such as GitHub, GitLab, or Bitbucket).
```
git branch -r
```

<br>


This command lists both local and remote branches, showing all branches in the repository.
```
git branch -a
```

<br>

This command lists the branches that have been merged into the current branch.
```
git branch --merged:
```

<br>

This command lists the branches that have not been merged into the current branch.
```
git branch --no-merged
```
