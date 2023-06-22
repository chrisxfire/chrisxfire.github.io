---
title: notes > cli tools > git > add remove rename
date: 2022-10-23T16:06:02-0600
draft: false
---
# Add Files
```powershell
git add path # adds path to Staging
```
# Removing Files From Tracking and Working Directory
```powershell
git rm --cached <file> # untrack file; ADD FOLDER TO .gitignore FIRST
git rm -r --cached <folder> # untrack folder; ADD FOLDER TO .gitignore FIRST
git rm <file> # delete and untrack <file>; at next commit, file will be removed and no longer tracked
```
# Moving/Renaming Files
```powershell
git mv <from> <to>
```
