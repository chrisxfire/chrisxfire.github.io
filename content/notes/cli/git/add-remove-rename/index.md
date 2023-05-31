---
title: "notes > cli > git > add remove rename"
date: 2022-10-23T16:06:02-0600
draft: true
---
# Add Files
git add *path*adds *path* to Staging
# 
# Removing Files From Tracking and Working Directory
git rm --cached <file>untrack file; ADD FOLDER TO .gitignore FIRST
git rm -r --cached <folder>untrack folder; ADD FOLDER TO .gitignore FIRST
git rm <file>delete and untrack <file>; at next commit, file will be removed and
no longer tracked

# Moving/Renaming Files
git mv <from> <to>