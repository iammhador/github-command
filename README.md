# 📚 Comprehensive Git Commands Reference

## 📌 Useful Day-to-Day Git Commands
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
## 🔰 Basic Operations
```sh
# Clone a repository
$ git clone <repository-url>
# Initialize a new Git repository
$ git init
# Add a file to the staging area
$ git add file-name.js
# Add all files to the staging area
$ git add .
# Commit staged changes with a message
$ git commit -m "Your descriptive commit message"
# Commit all changes (including untracked files)
$ git commit -a -m "Commit message"
# Amend the last commit message
$ git commit --amend -m "New commit message"
# Push local changes to remote repository
$ git push origin branch-name
# Push and set upstream branch for the first time
$ git push -u origin branch-name
# Pull changes from remote repository
$ git pull origin branch-name
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
## 🔀 Merging & Rebasing
```sh
# Merge a branch into current branch
$ git merge branch-name
# Merge without creating a merge commit (fast-forward)
$ git merge --ff-only branch-name
# Merge with a commit even if fast-forward is possible
$ git merge --no-ff branch-name
# Abort a merge in progress
$ git merge --abort
# Rebase current branch onto another branch
$ git rebase branch-name
# Interactive rebase for editing commits
$ git rebase -i HEAD~3  # Last 3 commits
# Continue rebase after resolving conflicts
$ git rebase --continue
# Abort a rebase in progress
$ git rebase --abort
```
---
## 🔄 Syncing & Fetching
```sh
# Fetch latest changes from remote (without merging)
$ git fetch
# Fetch changes from a specific remote
$ git fetch remote-name
# Fetch & rebase changes from the remote branch
$ git pull --rebase
# Stash uncommitted changes (to come back later)
$ git stash
# Stash with a descriptive message
$ git stash save "Work in progress on feature X"
# List stashed changes
$ git stash list
# Apply last stashed changes
$ git stash apply
# Apply a specific stash
$ git stash apply stash@{1}
# Apply and remove last stashed changes
$ git stash pop
# Drop a specific stash
$ git stash drop stash@{1}
# Clear all stashed changes
$ git stash clear
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
# Reset to a specific commit
$ git reset --hard commit-hash
# Cleanup merged branches
$ git fetch -p && git branch -vv | grep 'origin/.*: gone]' | awk '{print $1}' | xargs git branch -d
```
---
## 🏷️ Tags & Releases
```sh
# List all tags
$ git tag
# Create a lightweight tag
$ git tag v1.0.0
# Create an annotated tag with message
$ git tag -a v1.0.0 -m "Version 1.0.0 release"
# Push tags to remote
$ git push origin --tags
# Push a specific tag
$ git push origin v1.0.0
# Delete local tag
$ git tag -d v1.0.0
# Delete remote tag
$ git push origin --delete v1.0.0
# Check out code at a specific tag
$ git checkout v1.0.0
```
---
## 📊 History & Inspection
```sh
# Show commit history with a pretty format
$ git log --pretty=format:"%h %an %ar - %s"
# Filter commits by author
$ git log --author="username"
# Filter commits by date range
$ git log --after="2023-01-01" --before="2023-02-01"
# Search for commits containing specific text
$ git log -S "function searchFunction"
# Show commits that modified a specific file
$ git log --follow -- file-name.js
# Show who changed what and when in a file
$ git blame file-name.js
# Show the contents of a file at a specific commit
$ git show commit-hash:file-name.js
```
---
## 🔧 Configurations & Setup
```sh
# Set username globally
$ git config --global user.name "Your Name"
# Set email globally
$ git config --global user.email "your.email@example.com"
# Set username for current repository only
$ git config user.name "Your Name"
# Set default editor
$ git config --global core.editor "code --wait"
# Set default merge tool
$ git config --global merge.tool vimdiff
# List all configurations
$ git config --list
# Setup global .gitignore
$ git config --global core.excludesfile ~/.gitignore_global
```
---
## 🏎️ Advanced & Useful Commands
```sh
# Create and apply patches
$ git format-patch -1 commit-hash
$ git am < patch-file.patch
# Cherry-pick a commit from another branch
$ git cherry-pick commit-hash
# Squash the last N commits
$ git reset --soft HEAD~N && git commit
# Show the remote branches that have been merged
$ git remote prune origin --dry-run
# Archive a branch into a zip file
$ git archive --format=zip HEAD > archive-HEAD.zip
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
# Find when a line of code was introduced
$ git log -S "function name" --pretty=format:'%h %an %ad %s'
```
---
## 👷 Working with Remote Repositories
```sh
# Add a new remote
$ git remote add upstream https://github.com/original/repo.git
# Fetch all branches from a remote
$ git fetch upstream
# Pull from upstream to keep your fork updated
$ git pull upstream main
# Push to multiple remotes
$ git remote set-url --add --push origin https://github.com/your/repo.git
$ git remote set-url --add --push origin https://github.com/other/repo.git
# Show detailed info about a remote
$ git remote show origin
# Remove a remote
$ git remote remove remote-name
```
---
## 🔒 Git Hooks & Automation
```sh
# Create a pre-commit hook (in .git/hooks/pre-commit)
$ chmod +x .git/hooks/pre-commit
# Sample pre-commit hook to run linter
#!/bin/sh
npm run lint
# Create a post-merge hook (in .git/hooks/post-merge)
$ chmod +x .git/hooks/post-merge
# Sample post-merge hook to install dependencies
#!/bin/sh
npm install
```
---
## 🌊 Git Workflows
```sh
# Git Flow - Start a feature
$ git flow feature start feature-name
# Git Flow - Finish a feature
$ git flow feature finish feature-name
# Trunk-based - Create a short-lived feature branch
$ git checkout -b feature-name main
$ git push -u origin feature-name
# Pull request workflow - After PR is merged
$ git checkout main
$ git pull origin main
$ git branch -d feature-name
```
---
## 🛠️ Repository Maintenance
```sh
# Check repository integrity
$ git fsck
# Optimize repository
$ git gc
# Deeply clean and optimize repository
$ git gc --aggressive
# Cleanup unnecessary files
$ git clean -fd
# Cleanup unnecessary files (including ignored files)
$ git clean -fdx
# Check for corruption and repair
$ git fsck --full
```
---
## 🚀 Bonus: Aliases for Faster Work
```sh
# Status shorthand
git config --global alias.st status
# Checkout shorthand
git config --global alias.co checkout
# Commit shorthand
git config --global alias.cm commit
# Branch shorthand
git config --global alias.br branch
# Pretty log
git config --global alias.lg "log --oneline --graph --decorate --all"
# Unstage files
git config --global alias.unstage "reset HEAD --"
# Last commit
git config --global alias.last "log -1 HEAD"
# Show all aliases
git config --global alias.aliases "config --get-regexp ^alias\."
# Commit all changes
git config --global alias.cma "commit -a -m"
# Ammend last commit
git config --global alias.amend "commit --amend"
```
---
## ⚠️ Danger Zone (Use with Caution)
```sh
# Force push (only when you know what you're doing)
$ git push --force origin branch-name
# Force push with safeguards
$ git push --force-with-lease origin branch-name
# Delete all untracked files and directories
$ git clean -fd
# Reset to match remote branch completely
$ git fetch origin && git reset --hard origin/branch-name
# Remove file from all commits (rewrite history)
$ git filter-branch --tree-filter 'rm -f file-to-remove' HEAD
# Interactive rebase (squash, edit, reorder commits)
$ git rebase -i HEAD~10
```
