# Git Bash Commands for GitHub

## Introduction
This document provides a concise guide to using essential Git Bash commands for basic GitHub operations. It's ideal for beginners or as a quick reference for experienced users.

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

## Clone a Repository
To start working locally with a repository, clone it to your local machine:

```bash
git clone https://github.com/username/repository.git
```
- Replace `https://github.com/username/repository.git` with your repository's URL.

## Check Status
To see the status of your working directory and staging area:

```bash
git status
```

## Pull Latest Changes
Before you work, pull the latest changes from the remote repository:

```bash
git pull origin main
```
- Use the branch name relevant to your project if other than `main`.
- Example:
```bash
git pull origin develop
```

## Add Changes
To add changes to your staging area:

```bash
git add .
```
- For specific files, use `git add <filename>`.
- Example:
```bash
git add index.html
```

## Commit Changes
To commit your staged changes to your local repository:

```bash
git commit -m "Add a descriptive message about the changes"
```
- Example:
```bash
git commit -m "Update index.html with new header"
```

## Push Changes
To push your committed changes to the remote repository:

```bash
git push origin main
```
- Ensure the branch name is correct for your project.
- Example:
```bash
git push origin develop
```

## Creating and Switching Branches
To create a new branch or switch branches:

```bash
git branch new-branch
git checkout new-branch
```
- Replace `new-branch` with the desired branch name.
- Example:
```bash
git branch feature-login
git checkout feature-login
```

## Merging Branches
To merge changes from one branch into another:

```bash
git checkout main
git merge new-branch
```
- Replace `new-branch` with the branch you want to merge into `main`.
- Example:
```bash
git checkout main
git merge feature-login
```
