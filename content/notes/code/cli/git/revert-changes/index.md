---
title: notes > code > cli > git > revert changes
date: 2022-10-23T16:04:59-0600
draft: false
weight: 1
---
# Reset
`git reset <commit>` – undo all commits after commit, preserving changes locally  
`git reset --hard <commit> ` – discard all history and change back to commit  

# Reverting Changes
`git commit --amend` – undo a commit to allow you to make more changes, stage them, and commit again  
- this replaces the most recent commit with a new commit  
`git restore <file>` – revert file back to when you last committed or initially cloned  
`git restore --staged <file>` – unstages file  
`git restore --source=<hash-value>`  
- restore files from commit with hash value <hash>
- then, you should:
  - `git add .`
  - `git commit -m msg`
  - `git push`

# Rebasing
- Rebasing makes for a cleaner history.
- A rebased branch appears as if all the work happened in a series, even when it actually happened in parallel.
- You may rebase when contributing to a project to which you do not maintain.
- Do not rebase commits that exist outside of your repository.
- Do not rebase commits that people may have based work on.
- Do rebase local changes before pushing to clean up your work.
