---
title: "notes > cli > git > branching"
date: 2021-05-30T18:28:35-0600
draft: true
---
# Managing Branches
git branch *branch*create a new branch named *branch* (but don't switch to it)
- `HEAD` *will still point to the current branch*
git branchreturn current branches
git branch --merged *branch* return branches that have merged into current branch or *branch*
git branch --no-merged *branch*return branches that have not merged into current branch or *branch*
--listlist all branches in the repo
--all
--delete <branch>delete <branch>
--move <old> <new>rename branch from <old> to <new>
--set-upstream-to <remote/branch> [local]track remote branch at <remote:branch> to [local branch]
-vreturn current branches and last commit on each branch
-vvreturn current branches, last commit, tracking, and position of current branch
# Switching Branches
Switching branches changes files in your working directory to match your last commit on this branch.

git switch [--create] <branch>switch to <branch>; optionally create it first
git switch -switch to previous branch

# Remote Branches
git push --set-upstream <remote> <branch>push <branch> to <remote>
git push <remote> --delete <branch>delete <branch> from <remote>
git push <remote> <local branch>:<remote branch>push <local> to <remote>

# Remote-tracking Branches
References to the state of remote branches.
Remote-tracking branch names are in the form *remote/branch*.
Example: `origin/master` is a remote-tracking branch of origin:master.

<u>Workflow Strategies for Branches (with recommended names)</u>
master – code that is entirely stable
develop – the working branch used to test stability
topic – branches used to work on individual topics (issues, hotfixes, features)
