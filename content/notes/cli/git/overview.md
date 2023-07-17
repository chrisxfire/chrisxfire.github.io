---
title: notes > cli > git > overview
date: 2021-05-26T10:13:25-0600
draft: false
weight: -1
---
# Git
A distributed version control system

# Concepts
*commit* – save the state of your project (take a snapshot of all files and store a reference to that snapshot)

## File States
- *unmodified* – file has not been changed
- *modified* – file has been changed but not committed
- *staged* – file has been marked to go into next commit snapshot
- *committed* – file stored in database
- *untracked* – files in your working directory that were not in last snapshot and not in staging
- *tracked* – files Git knows about: unmodified, modified, and staged file states

## Sections of a Git Project
- *working* – a single checkout of one version of the project
- *staging* – a file, generally in the Git directory, of information about what goes into the next commit (aka index)
- *repository* – metadata and database of the project
