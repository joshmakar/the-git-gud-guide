# The Git Gud Guide

## Why I wrote this guide

This guide was/is being written as a reference and learning tool for using Git and GitHub

## The Git Basics

### Git Status

`git status`

This will display the git status. You'll use this a lot.

### Git Initialization

`git init`

This will initialize git in the current directory and create a hidden folder called *.git*.

### Adding files and directories

#### Single files

`git add <file_or_folder_name>`

##### Example

`git add app.js`

This will tell git to stage the file or folder specified.

#### All files

`git add .`

This will tell git to stage all files and folders.

### Commiting changes

`git commit -m "A useful message."`

This will commit and create a message for the files added to the staging area.