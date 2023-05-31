---
title: "notes > cli > git > workflows"
date: 2021-08-18T10:28:58-0600
draft: true
---
# Initliaizing a Repository
1.  Go to the project's directory
<!-- -->
2.  git init
<!-- -->
3.  Go to GitHub and create repository
<!-- -->
4.  git remote add <repository name> <GitHub URL>
5.  git add .
6.  git commit -m "Initial commit."
7.  *git pull <name> mainOnly needed if anything was added to GitHub repository directly (like README).
8.  git push --set-upstream <name> main
<!-- -->
9.  Make a [Virtual Environments](onenote:Python%203.one#Virtual%20Environments&section-id={8663E0CB-BB05-40FC-9E82-D6465163705D}&page-id={FF9E817E-31F3-4556-A6D2-3BC4756CE2A4}&end&base-path=https://d.docs.live.net/1489beaac91cb6b6/Documents/Notebooks/Reference)

# Common Branching Workflow
## Create a new branch and do some work
1.  git switch --create hotfixCreate and switch to branch hotfix
2.  git push --set-upstream <remote> hotfixCreate hotfix branch on remote
3.  Do work as normal.

## Merge the new branch back into main
1.  git switch - or git switch mainSwitch to branch main
2.  git merge hotfixMerge branch hotfix into main
3.  git branch --delete hotfixDelete branch hotfix locally
4.  git push <remote> --delete hotfixDelete branch hotfix on remote
5.  git commit -m "Merged hotfix into main"
6.  git push

# Renaming Master to Main
1.  git branch -m master main
2.  git push -u origin main
<!-- -->
3.  GitHub > Settings > Branches > master > main > Update
<!-- -->
4.  git branch -u origin/main main
<!-- -->
5.  GitHub > Branches > master > Delete this branch.

# Renaming repositories
1.  git mv <old> <new>
2.  git commit
3.  git push
4.  git remote rename <old> <new>
5.  git remote set-url --add <new> <URL>
6.  git remote set-url --delete <new> <old URL>
<!-- -->
7.  GitHub > <old> repository > Settings > Rename
8.  Rename local directory

# Delete a Remote Branch
git push -d origin *branch-name*

# Cleaning a Remote Repository
git remote prune origin