# Git Commands Memo

## Introduction
This document provides a concise guide to essential Git commands for everyday use.

## Navigation in Git Bash
**To navigate to a subdirectory:**

```bash
cd subdirectory/
```
**To return to the parent directory:**

```bash
cd ..
```
**To list files in the current directory:**

```bash
ls
```

## Basic commands

### Clone a repository
To start working locally with a repository, clone it to your local machine:
```bash 
git clone https://github.com/username/repository.git
```

### Check status
To see the status of your working directory and staging area:
```bash 
git status
```

### Fetch changes / Récupérer sans fusionner les changements
Fetch changes from the remote repository without merging:
```bash 
git fetch origin
```

### Pull changes / récupérer et fusionner les changements
Fetch and merge changes from the remote repository to your local:
```bash 
git pull origin main
```

### Add changes to the staging area
The staging area allows you to prepare changes before committing them to the repository, providing flexibility on what to include in each commit.

**Add changes in specific files to the staging area**:
```bash 
git add <filename>
```

**Add all changes to the staging area**:
```bash
git add .
```

### Commit changes / Commenter les changements
Commit your staged changes:
```bash 
git commit -m "Commit message explaining the changes"
```

### Push changes / Pousser les changements
Push your committed changes to the remote repository:
```bash 
git push origin main
```

### Create branch
Create a new branch and switch to it:
```bash 
git checkout -b new-branch-name
```

### Merge branch
Merge another branch into your current branch:
```bash 
git merge other-branch-name
```

### View log
View the commit log:
```bash 
git log 
```
