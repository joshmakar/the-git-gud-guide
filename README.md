# The Git Gud Guide

## Why I wrote this guide

This guide was/is being written as a reference and learning tool for using Git and GitHub

## The Git Basics

### Git Initialization

`git init`

This will initialize git in the current directory and create a hidden folder called *.git*.

### Git Status

`git status`

This will display the git status. You'll use this a lot.

### Git Log

`git log`

This will display a log of commits made.


## Adding files and directories

### Single files

`git add <file_or_folder_name>`

*Example*

`git add app.js`

This will tell git to stage the file or folder specified.

### All files

`git add .`

This will tell git to stage all files and folders.


## Commiting

`git commit -m "A useful message."`

This will commit and create a message for the files added to the staging area.


## Checking Out

Checking out can loosely be thought of as, "I'm checking out/viewing the state of my project at this particular time."

### Previous commits

`git checkout <commit_hash>`

*Example*
`git checkout c7a2a019170031f89dadad42f49a2c38265756ac`

This will checkout the commit with the matching hashtag.

### Master

Master is the central or main state of your application. After checking out a previous commit, you will likely want to switch back to the master to continue working.

`git checkout master`

### Reverting to previous commits

`git log`

Find the hashtag that corrisponds to where you want to revert back to.

`git revert --no-commit <short_or_full_commit_hash>`

*Example*
`got revert --no-commit c7a2a01..HEAD`

This will revert you back to the selected commit. You'll want to perform a new commit with a message such as "Revert back to c7a2a01".