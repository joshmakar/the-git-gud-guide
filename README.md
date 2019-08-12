# The Git Gud Guide

For referencing the most used git commands and terminology.

## Why I wrote this guide

This guide was written as a place to hold useful git commands in a centralized location to easily be referenced.


# The Git Basics

**Working Directory**
This is where all of your files and directories that you're working on live.

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

`$ git add -A` Stages **all changes including hidden files**
`$ git add .` Stages new files and modifications, **without deletions**
`$ git add -u` Stages modifications and deletions, **without new files**

This will tell git to stage all files and folders.

### Wildcards

`$ git add *.<ext>`

**Example**

`$ git add *.html`

This will add every file with the .html extension.


## Removing files and directories from the staging area

`$ git reset HEAD <file_or_folder>`


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


## Commiting

`$ git commit -m "A useful message."`

This will commit and create a message for the files added to the staging area.


## Checking Out

Checking out can loosely be thought of as, "I'm checking out/viewing the state of my project at this particular time."

### Previous commits

`$ git checkout <commit_hash>`

**Example**
`$ git checkout c7a2a019170031f89dadad42f49a2c38265756ac`

This will checkout the commit with the matching hashtag.

### Master

Master is the central or main state of your application. After checking out a previous commit, you will likely want to switch back to the master to continue working.

`$ git checkout master`

### Reverting to previous commits

`$ git log`

Find the hashtag that corrisponds to where you want to revert back to.

`$ git revert --no-commit <short_or_full_commit_hash>`

**Example**
`got revert --no-commit c7a2a01..HEAD`

This will revert you back to the selected commit. You'll want to perform a new commit with a message such as "Revert back to c7a2a01".


## Branches

Branches are versions of code split off from the master branch, best used when testing features and development. Once changes are finalized, you can then merge the finished branch into the master branch.

`$ git branch` List all branches

### Create a new branch

`$ git checkout -b <branch_name>`

This will create and switch to the named branch.

### Switching between branches

`$ git checkout <branch_name>`

**Example**
`$ git checkout master`

### Merging branches

First checkout the branch you want to merge in to, typcially this would be *master*

`$ git merge <branch_name>`

This will merge the named branch into the branch currently checked out and create a new commit.

### Removing branches

`$ git branch -d <branch_name>`

This will delete the named branch.


## Misc

### Change author name and email

`$ git config --global user.name "John Doe"`

`$ git config --global user.email "john@doe.org"`

This will change your user name and email address globally.

**Example**
```
$ git config user.name "John Doe"
$ git config user.email "john@doe.org"
```

This will change your user name and email only for the repository/directory you're working in.


# Github Basics

`$ git push <remote_name> :<branch_name>`

`$ git push origin :feature-branch`

This will push your changes to your Github remote repository and delete the named branch.