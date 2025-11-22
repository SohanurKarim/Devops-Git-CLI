
# Complete Git + WSL + GitHub Workflow Guide

## 1. Version Control Systems (VCS): Quick Comparison
- Git — Distributed, fast, reliable  
- Mercurial — Distributed, simpler model  
- SVN — Centralized, linear workflows  
- Perforce — Centralized, optimized for large binaries  

---

## 2. Install & Configure WSL
```
wsl --install
wsl --set-default-version 2
wsl --install -d Ubuntu-24.04
wsl
sudo apt update && sudo apt upgrade -y
```

---

## 3. Backup & Restore WSL
```
wsl --list --verbose
wsl --export Ubuntu-24.04 "C:/WSL-Backup/Ubuntu-Backup.tar"
wsl --unregister Ubuntu
wsl --import Ubuntu "C:/WSL" "C:/WSL-Backup/Ubuntu-Backup.tar"
```

---

## 4. Install & Configure Git
```
sudo apt install git -y
git config --global user.name "md-sarowar-alam"
git config --global user.email "sarowar.alam@gmail.com"
git config --global init.defaultBranch main
git config --global core.autocrlf input
git config --global color.ui auto
```

---

## 5. GitHub SSH Authentication
```
ssh-keygen -t ed25519 -C "md-sarowar-alam"
git remote set-url origin git@github.com:md-sarowar-alam/batch-08-class-git.git
```

---

## 6. Working with Branches
```
git branch -a
git checkout -b feature/my-change
git add -A
git commit -m "meaningful message"
```

---

## 7. Rebase with Main
```
git fetch origin
git rebase origin/main
```

---

## 8. Merge Branches
```
git checkout main
git pull origin main
git merge --no-ff feature/my-change
git push origin main
```

---

## 9. Revert & Reset
```
git revert -m 1 <commit>
git reset --hard <commit>
git push origin main --force
```

---

## 10. Useful Commands
```
git status
git log --oneline --graph
git diff
git stash
```

---

## 11. Initializing a New GitHub Repository (Your Added Part)

### Create README and initialize Git repo
```
echo "# guide-line" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:md-sarowar-alam/guide-line.git
git push -u origin main
```

---

