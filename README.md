# Cheat sheet
A cheatsheet of commands for my workflow.

## - git & Terminal Cheat Sheet
Local Navigation (Shell)
- cd – go to home
- cd ~/Desktop – absolute path
- cd .. – up one directory
- pwd – print current path

- ls – names
- ls -la – incl. hidden + details

## Inspect Repo State
- git status – what's changed/staged?
- git status -sb – short, with branch
- git diff – unstaged changes
- git diff --staged – staged changes

## Working with an Existing Repo
- git clone <url> – HTTPS or SSH
- cd <folder>
- git remote -v – view remotes
- git fetch – update refs (no merge)
- git pull – fetch + merge (or rebase; see config below)

## Day-to-Day: Add, Commit, Push
- git add . – stage all modified/new files
- git add -p – stage hunks interactively
- git commit -m "meaningful msg" – commit staged changes
- git push -u origin <branch> – first push; sets upstream
- git push – subsequent pushes

## Starting a Brand-New Repo
- git init
- git add --all
- git commit -m "initial commit"
- git branch -M main – (optional) rename to main
- git remote add origin <url>
- git push -u origin main

## Branching & Switching
- git branch -av – list local & remote branches
- git branch <new-branch> – create branch
- git checkout <branch> – switch (old syntax)
- git switch <branch> – switch (newer, nicer)
- git switch -c <new-branch> – create + switch

## Merging (Safe Workflow)
- git checkout main
- git pull --ff-only – update main safely
- git checkout <feature>
- git merge main – bring latest main into feature
- git checkout main
- git merge <feature> – merge feature into main
- git push

## Rebasing (Optional)
- git checkout <feature>
- git fetch origin
- git rebase origin/main
- git add <fixed-files>
- git rebase --continue
- git push --force-with-lease

## Stashing
- git stash – stash tracked changes
- git stash -u – include untracked
- git stash list
- git stash pop – restore & remove from stash

## Undo & Recover
- git restore <file> – discard unstaged changes
- git checkout -- <file> – older syntax

- git reset HEAD <file> – unstage a staged file
- git reset --soft HEAD~1 – undo commit, keep staged
- git reset --mixed HEAD~1 – undo commit, keep changes unstaged
- git reset --hard HEAD~1 – undo commit AND changes

- git revert <commit> – make a new commit that undoes <commit>
- git reflog – find lost commits & HEAD moves

## Logs & History
- git log --oneline --graph --decorate --all
- git blame <file>
- git show <commit>

## Comparing Things
- git diff <branchA>..<branchB>
- git diff --name-only HEAD~1

## Tags (Releases)
- git tag v1.0.0
- git tag -a v1.0.0 -m "msg"
- git push origin v1.0.0
- git push --tags

## Remotes
- git remote add origin <url>
- git remote set-url origin <url>
- git fetch origin --prune

## .- gitignore Example
node_modules/
*.log
.env
.DS_Store

## To apply .- gitignore after adding files:
- git rm -r --cached .
- git add .
- git commit -m "apply .- gitignore"

## Useful Config
- git config --global user.name "Your Name"
- git config --global user.email "you@example.com"
- git config --global pull.rebase true
- git config --global init.defaultBranch main
- git config --global alias.lg "log --oneline --graph --decorate --all"

## Common Fixes for Push
- git push -u origin <branch>
- git branch -m <old> <new>
- git push origin :<old> <new>
- git push -u origin <new>
- git fetch origin
- git rebase origin/main
