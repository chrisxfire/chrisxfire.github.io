---
title: overview
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

# Git Command Groups
## Main Commands
| Command         | Description                                                        |
| --------------- | ------------------------------------------------------------------ |
| add             | Add file contents to the index                                     |
| am              | Apply a series of patches from a mailbox                           |
| archive         | Create an archive of files from a named tree                       |
| bisect          | Use binary search to find the commit that introduced a bug         |
| branch          | List, create, or delete branches                                   |
| bundle          | Move objects and refs by archive                                   |
| checkout        | Switch branches or restore working tree files                      |
| cherry-pick     | Apply the changes introduced by some existing commits              |
| citool          | Graphical alternative to git-commit                                |
| clean           | Remove untracked files from the working tree                       |
| clone           | Clone a repository into a new directory                            |
| commit          | Record changes to the repository                                   |
| describe        | Give an object a human readable name based on an available ref     |
| diff            | Show changes between commits, commit and working tree, etc         |
| fetch           | Download objects and refs from another repository                  |
| format-patch    | Prepare patches for e-mail submission                              |
| gc              | Cleanup unnecessary files and optimize the local repository        |
| gitk            | The Git repository browser                                         |
| grep            | Print lines matching a pattern                                     |
| gui             | A portable graphical interface to Git                              |
| init            | Create an empty Git repository or reinitialize an existing one     |
| log             | Show commit logs                                                   |
| maintenance     | Run tasks to optimize Git repository data                          |
| merge           | Join two or more development histories together                    |
| mv              | Move or rename a file, a directory, or a symlink                   |
| notes           | Add or inspect object notes                                        |
| pull            | Fetch from and integrate with another repository or a local branch |
| push            | Update remote refs along with associated objects                   |
| range-diff      | Compare two commit ranges (e.g. two versions of a branch)          |
| rebase          | Reapply commits on top of another base tip                         |
| reset           | Reset current HEAD to the specified state                          |
| restore         | Restore working tree files                                         |
| revert          | Revert some existing commits                                       |
| rm              | Remove files from the working tree and from the index              |
| scalar          | A tool for managing large Git repositories                         |
| shortlog        | Summarize 'git log' output                                         |
| show            | Show various types of objects                                      |
| sparse-checkout | Reduce your working tree to a subset of tracked files              |
| stash           | Stash the changes in a dirty working directory away                |
| status          | Show the working tree status                                       |
| submodule       | Initialize, update or inspect submodules                           |
| switch          | Switch branches                                                    |
| tag             | Create, list, delete or verify a tag object signed with GPG        |
| worktree        | Manage multiple working trees                                      |

## Manipulators
| Command       | Description                                                    |
| ------------- | -------------------------------------------------------------- |
| config        | Get and set repository or global options                       |
| fast-export   | Git data exporter                                              |
| fast-import   | Backend for fast Git data importers                            |
| filter-branch | Rewrite branches                                               |
| mergetool     | Run merge conflict resolution tools to resolve merge conflicts |
| pack-refs     | Pack heads and tags for efficient repository access            |
| prune         | Prune all unreachable objects from the object database         |
| reflog        | Manage reflog information                                      |
| remote        | Manage set of tracked repositories                             |
| repack        | Pack unpacked objects in a repository                          |
| replace       | Create, list, delete refs to replace objects                   |

## Interrogators
| Command       | Description                                                           |
| ------------- | --------------------------------------------------------------------- |
| annotate      | Annotate file lines with commit information                           |
| blame         | Show what revision and author last modified each line of a file       |
| bugreport     | Collect information for user to file a bug report                     |
| count-objects | Count unpacked number of objects and their disk consumption           |
| diagnose      | Generate a zip archive of diagnostic information                      |
| difftool      | Show changes using common diff tools                                  |
| fsck          | Verifies the connectivity and validity of the objects in the database |
| gitweb        | Git web interface (web frontend to Git repositories)                  |
| help          | Display help information about Git                                    |
| instaweb      | Instantly browse your working repository in gitweb                    |
| merge-tree    | Perform merge without touching index or working tree                  |
| rerere        | Reuse recorded resolution of conflicted merges                        |
| show-branch   | Show branches and their commits                                       |
| verify-commit | Check the GPG signature of commits                                    |
| verify-tag    | Check the GPG signature of tags                                       |
| version       | Display version information about Git                                 |
| whatchanged   | Show logs with difference each commit introduces                      |

## User-facing Interfaces
| Command           | Description                                        |
| ----------------- | -------------------------------------------------- |
| attributes        | Defining attributes per path                       |
| cli               | Git command-line interface and conventions         |
| hooks             | Hooks used by Git                                  |
| ignore            | Specifies intentionally untracked files to ignore  |
| mailmap           | Map author/committer names and/or E-Mail addresses |
| modules           | Defining submodule properties                      |
| repository-layout | Git Repository Layout                              |
| revisions         | Specifying revisions and ranges for Git            |

## External Commands
- askpass
- askyesno
- credential-helper-selector
- credential-manager
- credential-manager-core
- credential-manager-ui
- flow
- lfs
- update-git-for-windows

Also:
- Interactors
- Low-level manipulators
- Low-level interrogators
- Low-level syncing repos
- Developer-facing interfaces
