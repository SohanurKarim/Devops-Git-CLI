# Complete Git + WSL + GitHub Workflow Guide

## 1. Version Control Systems (VCS): Quick Comparison

### Git

-   Distributed, fast, reliable\
-   Best for open-source & DevOps workflows

### Mercurial

-   Distributed, simpler model\
-   Less community support

### Subversion (SVN)

-   Centralized\
-   Good for legacy linear workflows

### Perforce

-   Centralized, extremely fast for huge binary repositories

------------------------------------------------------------------------

## 2. Install & Configure WSL

### Enable WSL

    wsl --install

### Set WSL 2 as Default

    wsl --set-default-version 2

### Install Ubuntu

    wsl --install -d Ubuntu-24.04
    wsl
    sudo apt update && sudo apt upgrade -y

------------------------------------------------------------------------

## 3. Backup & Restore WSL

### List Instances

    wsl --list --verbose

### Backup

    wsl --export Ubuntu-24.04 "C:/WSL-Backup/Ubuntu-Backup.tar"

### Unregister

    wsl --unregister Ubuntu

### Restore

    wsl --import Ubuntu "C:/WSL" "C:/WSL-Backup/Ubuntu-Backup.tar"

------------------------------------------------------------------------

## 4. Install & Configure Git

### Install Git

    sudo apt install git -y

### Configure Identity

    git config --global user.name "md-sarowar-alam"
    git config --global user.email "sarowar.alam@gmail.com"

### Recommended Settings

    git config --global init.defaultBranch main
    git config --global core.autocrlf input
    git config --global color.ui auto

------------------------------------------------------------------------

## 5. GitHub SSH Authentication

### Generate SSH Key

    ssh-keygen -t ed25519 -C "md-sarowar-alam"

### Add to GitHub

Upload the `id_ed25519.pub` to\
**GitHub → Settings → SSH and GPG Keys**

### Change Remote to SSH

    git remote set-url origin git@github.com:md-sarowar-alam/batch-08-class-git.git

------------------------------------------------------------------------

## 6. Working with Branches

### Check Branches

    git branch -a

### Create Branch

    git checkout -b feature/my-change

### Stage & Commit

    git add -A
    git commit -m "meaningful message"

------------------------------------------------------------------------

## 7. Rebase with Main

    git fetch origin
    git rebase origin/main

------------------------------------------------------------------------

## 8. Merge Branches

### Local Merge

    git checkout main
    git pull origin main
    git merge --no-ff feature/my-change
    git push origin main

------------------------------------------------------------------------

## 9. Revert & Reset

### Revert Merge Commit

    git revert -m 1 <commit>

### Reset (Dangerous)

    git reset --hard <commit>
    git push origin main --force

------------------------------------------------------------------------

## 10. Useful Commands

    git status
    git log --oneline --graph
    git diff
    git stash

