# 📌 Useful Day-to-Day Git Commands

---

## 🔍 Checking Repository Status & Logs
```sh
# Check the current status of your repo
$ git status

# View commit history (compact view)
$ git log --oneline --graph --decorate --all

# View last N commits
$ git log -n 5

# Show changes in files before committing
$ git diff

# Show changes in a specific file
$ git diff file-name.js

# Check the current branch in terminal
$ git branch --show-current
```

---

## 🌿 Branch Management
```sh
# List all local branches
$ git branch

# List all remote branches
$ git branch -r

# List all local & remote branches
$ git branch -a

# Create a new branch and switch to it
$ git checkout -b new-branch

# Switch to an existing branch
$ git checkout branch-name

# Delete a local branch
$ git branch -d branch-name

# Delete a remote branch
$ git push origin --delete branch-name

# Rename the current branch
$ git branch -m new-branch-name
```

---

## 🔄 Syncing & Fetching
```sh
# Fetch latest changes from remote (without merging)
$ git fetch

# Fetch & rebase changes from the remote branch
$ git pull --rebase

# Stash uncommitted changes (to come back later)
$ git stash

# List stashed changes
$ git stash list

# Apply last stashed changes
$ git stash apply

# Apply and remove last stashed changes
$ git stash pop
```

---

## 🔥 Undoing Changes
```sh
# Undo changes in a specific file (before committing)
$ git checkout -- file-name.js

# Reset the last commit (keep changes unstaged)
$ git reset --soft HEAD~1

# Reset the last commit (discard changes)
$ git reset --hard HEAD~1

# Remove a file from staging area (undo `git add`)
$ git reset file-name.js

# Revert a pushed commit (without losing history)
$ git revert commit-hash
```

---

## 🏎️ Advanced & Useful Commands
```sh
# Show which branch contains a specific commit
$ git branch --contains commit-hash

# Show the author and date of each line in a file
$ git blame file-name.js

# Check remote repository URL
$ git remote -v

# Change the remote repository URL
$ git remote set-url origin new-repo-url.git

# Clean untracked files (dangerous, use with caution)
$ git clean -f

# View differences between two branches
$ git diff branch-1..branch-2
```

---

## 🚀 Bonus: Aliases for Faster Work
```sh
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.cm commit
git config --global alias.br branch
git config --global alias.lg "log --oneline --graph --decorate --all"
```
