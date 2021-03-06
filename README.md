# The Git Gud Guide

For referencing the most used git commands, terminology, and workflows.


## Preface

This guide is a work in progress and some of the content may be inaccurate.

If you find any issues or would like to contribue, please feel free to create a pull request.


## Why I wrote this guide

This guide was written as a place to hold useful git commands in a centralized location to easily be referenced.


# Git and GitHub are not the same

Git is a revision control system, a tool to manage your source code history. GitHub is a hosting service for Git repositories.

You can use Git alone for local version control. GitHub is primarily used for backup and collaboration.


# The Git Basics

## Terminology 

**Working Directory**  
This is where all of your files and directories that you're working on live. An example of this may be `Desktop/my-app/`.

**Staging Area**  
This is where you add files with `$ git add` that are ready to be commited to the Git repository.

**Repository**  
This is where all your snapshots/files are stored after you've commited them with `$ git commit`.


## Basic Workflow

1. Initialize git `$ git init`.
2. Add files `$ git add <files_or_folders>`.
3. Commit changes `$ git commit -m "Useful message"`.
4. Create feature branch `$ git checkout -b <branch_name>`.
5. Repeat steps 2 and 3 until satisfied.
6. Switch to Master branch and merge feature branch into it `$ git merge <branch_name>`.
7. Remove merged branch `$ git branch -d <branch_name>`.
8. Repeat.


## Git Initialization

`$ git init`

This will initialize git in the current directory and create a hidden folder called *.git*.


## Git Status

`$ git status`

This will display the git status. You'll use this a lot.


## Git Log

`$ git log`

This will display a log of commits made.


## Adding files and directories to the staging area

### Single files

`$ git add <file_or_folder_name>`

**Example**  
`$ git add app.js`

This will tell git to stage the file or folder specified.


### Multiple files

`$ git add .`

Stages new files and modifications, **without deletions**  
You'll use this one the most.

`$ git add -A`

Stages **all changes including hidden files**

`$ git add -u`

Stages modifications and deletions, **without new files**


### Wildcards

`$ git add *.<ext>`

**Example**  
`$ git add *.html`

This will add every file with the .html extension.


## Removing files and directories from the staging area

`$ git reset HEAD <file_or_folder>`

**Example**  
`$ git reset HEAD app.js`

This is basically the opposite of `git add`.


## Stashing changes in order to switch to the correct branch without modifying the current branch

If you've begun making changes with the wrong branch checked out, you can stash your changes, then checkout the correct branch, and finally apply the stashed changes.

`$ git stash`  
`$ git checkout correct-branch`  
`$ git stash apply`  


## Ignoring files and folders

Create a file in the root directory called *.gitignore*.

Add file or folder names to the *.gitignore* file separated by line breaks.

```
.env
.passwords
node_modules
*.sublime-*
*.code-workspace*
```


## Commits and Commiting

`$ git commit -m "A useful message."`

This will commit and create a message for the files added to the staging area.


### Checking out

Checking out can loosely be thought of as, "I'm checking out/viewing the state of my project on this particular branch, or at this particular time."


#### Previous commits

`$ git checkout <commit_hash>`

**Example**  
`$ git checkout c7a2a019170031f89dadad42f49a2c38265756ac`

This will checkout the commit with the matching hashtag.


#### Master

Master is the central or main state of your application. After checking out a previous commit, you will likely want to switch back to the master to continue working.

`$ git checkout master`


### Reverting to previous commits

`$ git log`

Find the hashtag that corrisponds to where you want to revert back to.

`$ git revert --no-commit <short_or_full_commit_hash>`

**Example**  
`$ git revert --no-commit c7a2a01..HEAD`

This will revert you back to the selected commit. You'll want to perform a new commit with a message such as "Revert back to c7a2a01".


## Branches

Branches are versions of code split off from the master branch, best used when testing features and development. Once changes are finalized, you can then merge the finished branch into the master branch.

`$ git branch`

Lists all branches


### Create a new branch

`$ git checkout -b <branch_name>`

This will create and switch to the named branch.


### Switching between branches

`$ git checkout <branch_name>`

**Example**  
`$ git checkout feature-fix`


### Merging branches

First checkout the branch you want to merge in to, typcially this would be *master*

`$ git merge <branch_name>`

This will merge the named branch into the branch currently checked out and create a new commit.


### Removing branches

`$ git branch -d <branch_name>`

This will delete the named branch.


### Remote branches

`$ git remote -v`

This will list remote branches.


## Misc

### Change author name and email

```
$ git config --global user.name "John Doe"
$ git config --global user.email "john@doe.org"
```

This will change your user name and email address globally.


```
$ git config user.name "John Doe"
$ git config user.email "john@doe.org"
```

This will change your user name and email only for the repository/directory you're working in.

### Check for package updates

```
npm outdated
```

This will display a list of packages that are outdated. Packages in *red* means there's a newer version matching your requirements. Packages in *yellow* indicates that there's a newer version above your requirements, so proceed with caution.


# Github Basics

## Push to Github

`$ git push`

This will perform a basic push to the remote repository. If you're in a new local branch, follow the instructions output after performing a git push with the new branch checked out.

## Get updated list of remote branches

`$ git fetch origin`

## Delete a remote branch

`$ git push -d <remote_name> <branch_name>`

**Example**  
`$ git push -d origin feature-branch`

This will push your changes to your Github remote repository and delete the named remote branch.  
[Delete a local branch](#removing-branches)