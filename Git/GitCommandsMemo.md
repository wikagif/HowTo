# Git Commands Memo / Mémo des Commandes Git

## Introduction / Introduction
This memo provides a quick reference to essential Git commands for everyday use in software development.\
Ce mémo fournit une référence rapide aux commandes Git essentielles utilisées quotidiennement dans le développement logiciel.

## Basic Commands / Commandes de Base

### Clone a Repository / Cloner un Dépôt
Clone a repository to your local machine. \
Cloner un dépôt sur votre machine locale :

```bash
git clone https://github.com/username/repository.git
```

### Check Status / Vérifier le Statut
Check the current state of your working directory and staging area. \
Vérifier l'état actuel de votre répertoire de travail et de la zone de staging :

```bash
git status
```

### Fetch Changes / Récupérer les Changements
Fetch changes from the remote repository without merging. \
Récupérer les changements du dépôt distant sans les fusionner :

```bash
git fetch origin
```

### Pull Changes / Tirer les Changements
Fetch and merge changes from the remote repository to your local. \
Récupérer et fusionner les changements du dépôt distant avec votre local :

```bash
git pull origin main
```

### Add Changes / Ajouter des Changements
Add changes in specific files to the staging area. \
Ajouter des changements dans des fichiers spécifiques à la zone de staging :

```bash
git add <filename>
```

Add all changes to the staging area. \
Ajouter tous les changements à la zone de staging :

```bash
git add .
```

### Commit Changes / Commiter les Changements
Commit your staged changes. \
Commiter vos changements en attente :

```bash
git commit -m "Commit message explaining the changes"
```

### Push Changes / Pousser les Changements
Push your committed changes to the remote repository. \
Pousser vos changements commités vers le dépôt distant :

```bash
git push origin main
```

### Create Branch / Créer une Branche
Create a new branch and switch to it. \
Créer une nouvelle branche et y basculer :

```bash
git checkout -b new-branch-name
```

### Merge Branch / Fusionner une Branche
Merge another branch into your current branch. \
Fusionner une autre branche dans votre branche courante :

```bash
git merge other-branch-name
```

### View Log / Voir le Journal
View the commit log. \
Voir le journal des commits :

```bash
git log
```
