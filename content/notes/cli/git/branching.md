---
title: notes > cli > git > branching
date: 2021-05-30T18:28:35-0600
draft: false
weight: 1
---
# Managing Branches
- `git branch BRANCH` – create a new branch named branch (but don't switch to it) 
  - `HEAD` will still point to the current branch  
- `git branch` – return current branches  
  - `--merged BRANCH` – return branches that have merged into current branch or branch  
  - `--no-merged BRANCH` – return branches that have not merged into current branch or branch  
  - `--list` – list all branches in the repo  
  - `--all`  
  - `--delete BRANCH` – delete BRANCH
  - `--move OLD-BRANCH-NAME NEW-BRANCH-NAME` – rename branch from OLD-BRANCH-NAME to NEW-BRANCH-NAME
  - `--set-upstream-to REMOTE/BRANCH-NAME [LOCAL-BRANCH]` – track remote branch at `REMOTE/BRANCH-NAME` to `LOCAL-BRANCH`  
  - `-v` – return current branches and last commit on each branch  
  - `-vv` – return current branches, last commit, tracking, and position of current branch  

# Switching Branches
Switching branches changes files in your working directory to match your last commit on this branch.

- `git switch [--create] BRANCH` – switch to BRANCH; optionally create it first  
- `git switch` – switch to previous branch  

# Remote Branches
- `git push --set-upstream REMOTE BRANCH` – push BRANCH to REMOTE
- `git push REMOTE --delete BRANCH` – delete BRANCH from REMOTE
- `git push REMOTE LOCAL-BRANCH:<remote branch>` – push LOCAL-BRANCH to REMOTE

# Remote-tracking Branches
- References to the state of remote branches.  
- Remote-tracking branch names are in the form REMOTE/BRANCH-NAME.  
  - Example: `origin/master` is a remote-tracking branch of `origin:master`.

# Workflow Strategies for Branches (with recommended names)
- master – code that is entirely stable
- develop – the working branch used to test stability
- topic – branches used to work on individual topics (issues, hotfixes, features)
