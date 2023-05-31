---
title: "notes > cli > git > git"
date: 2021-05-26T10:13:25-0600
draft: true
---
# Git
A distributed version control system

# Concepts
commitsave the state of your project (take a snapshot of all files and store a reference to that snapshot)

## File States
unmodifiedfile has not been changed
modifiedfile has been changed but not committed
stagedfile has been marked to go into next commit snapshot
committedfile stored in database
untrackedfiles in your working directory that were not in last snapshot and not in staging
trackedfiles Git knows about: unmodified, modified, and staged file states

## Sections of a Git Project
workinga single checkout of one version of the project
staging a file, generally in the Git directory, of information about what goes into the next commit (aka index)
repositorymetadata and database of the project