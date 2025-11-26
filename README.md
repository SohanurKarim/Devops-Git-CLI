------------------------------------------------------------------------
## WSL (Windows Subsystem for Linux) Setup | Enable WSL (PowerShell Admin)
``` powershell
wsl --install
wsl --set-default-version 2
```
### Install Ubuntu 24.04
``` powershell
wsl --list --online
wsl --install -d Ubuntu-24.04
```
### Enter WSL & Update
``` bash
wsl
sudo apt update && sudo apt upgrade -y
```
### Backup WSL
``` powershell
wsl --export Ubuntu-24.04 "C:\WSL-Backup\Ubuntu-Backup.tar"
```
### Restore WSL
``` powershell
wsl --import Ubuntu-24.04 "." "C:\WSL-Backup\Ubuntu-Backup.tar"
```
### Delete Corrupted WSL Instance
``` powershell
wsl --unregister Ubuntu-24.04
```
------------------------------------------------------------------------
### 1) Install Git on Ubuntu
**Installation**
``` bash
sudo apt install git -y
```
**Verify**
``` bash
git --version
```
------------------------------------------------------------------------
### Git Examples | Clone Specific Branch
``` bash
git clone --branch feature/test-change-02 --single-branch git@github.com:md-sarowar-alam/batch-08-class-git.git
```
### Clone deafult / main branch 
``` bash
git clone git@github.com:md-sarowar-alam/batch-08-class-git.git
```
### Merge Main Into Branch
``` bash
git checkout feature/test-change-02
git pull origin main
```
### Rebase Branch

``` bash
git fetch origin
git rebase origin/main
```
### Commit or Stash Before Rebase
``` bash
git add .
git commit -m "WIP"
git rebase origin/main
```
### Reset Branch to Main
``` bash
git checkout feature/my-change
git fetch origin
git reset --hard origin/main
git push --force origin feature/my-change
```
### Create a new branch (best practice: don't work on main)
``` bash
git checkout -b feature/edit-readme
```
### Edit a file
``` bash
vi README.md
```
### Check what changed
``` bash
git status
# Shows modified files and your branch name
git diff README.md
# Shows the unstaged changes you made in README.md
```
### Stage (add) changes
``` bash
git add README.md
# or add everything changed:
git add -A

````
### Confirm staged changes:
``` bash
git status
git diff --staged   # shows exactly what will be committed
```
### Commit your changes
``` bash
git commit -m "Improve README: add clone and usage examples"
# If you prefer multi-line message:
git commit
# (this opens your editor to write subject + body)
```
### Push the branch to remote
``` bash
git push -u origin feature/edit-readme
```
### Merge main into your branch (simple & safe)
``` bash
cd batch-08-class-git
git checkout feature/test-change-02
git pull origin main
# or (same thing)
git merge origin/main
```
------------------------------------------------------------------------
## GitHub CLI Setup (Ubuntu)

``` bash
sudo apt install curl -y
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh -y
gh --version
```
------------------------------------------------------------------------
### Here is exactly how to create a repo locally and push it to GitHub | Create a local folder for your new repository
``` bash
mkdir my-new-repo
cd my-new-repo
```
### Initialize Git
``` bash 
git init
```
### Set default branch to main (recommended):
``` bash
git branch -M main
```
### Create some files
``` bash
echo "Hello GitHub" > README.md
```
### Stage and commit your files
``` bash
git add .
git commit -m "Initial commit"
```
### Create a remote repository on GitHub | Use GitHub CLI (gh)
``` bash
gh repo create my-new-repo --public --source=. --remote=origin
gh repo create my-new-repo --private --source=. --remote=origin
```
### Push your local repo to GitHub
``` bash
git push -u origin main
```
### Done! Your repo is now on GitHub.
``` bash
git remote -v
```
------------------------------------------------------------------------
### Merge one Branch into another
``` bash
git checkout feature/my-change-01
git fetch origin
git pull --rebase origin feature/my-change-01
git merge feature/my-change-02
```
### Revert & Reset Operations | Safe Revert (Creates new commit)
``` bash
git revert -m 1 7f076de5fed8cf5ac9cb544fa0f6e28e4243ed6d
git push origin main
```
### Dangerous Reset (Rewrites history)
``` bash
git reset --hard 38f5d6
git push origin main --force
```
### Warning: --force push overwrites remote history. Use with caution!
### Cleanup Operations | Delete Branches | Delete local branch
``` bash
git branch -d feature/my-change-01
```
### Force delete local branch
``` bash
git branch -D feature/my-change-01
```
### Delete remote branch
``` bash
git push origin --delete feature/my-change-01
```
------------------------------------------------------------------------
### Restore file from main | If you want the file back:
``` bash
git checkout origin/main -- file.txt
git add file.txt
git commit
```

---

## 🧑‍💻 Author
**Md. Sarowar Alam**  
Lead DevOps Engineer, Hogarth Worldwide  
📧 Email: sarowar@hotmail.com  
🔗 LinkedIn: [linkedin.com/in/sarowar](https://www.linkedin.com/in/sarowar/)

---
