---
title: "notes > cli > git > remotes"
date: 2022-10-23T16:05:11-0600
draft: false
---
# Remote Repositories
`git fetch <remote>` – retrieve all data from remote repository since last fetch (or clone)
- does not modify working directory; requires merging
`git fetch --all` – fetch from all remotes
`git pull` – executes fetch > merge
`git push <remote> <branch>` – push <branch> to <remote> repository
`git remote -v` – return remote repositories, their shortnames, and URLs
`git remote add <remote> <url>` – add a new Git remote repository
`git remote show <remote>` – return information about <remote> repository, including if you're up-to-date.
`git remote rename <old> <new>` – rename a remote from <old> to <new>
`git remote rm <remote>` – remove <remote>