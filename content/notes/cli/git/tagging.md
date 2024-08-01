---
title: tagging
date: 2022-10-23T16:05:23-0600
draft: false
weight: 1
tags:
 - kb/cli/git
---
# Tagging
Tags apply to commits.

`git tag --list` – return existing tags
`git tag -a <tag> -m "<msg>"` – create annotated tag named <tag> for pending commit with tagging message <msg>
`git show <tag>` – return information on <tag>
`git tag -a <tag> [checksum]` – tag commit [checksum] as <tag> after the fact; [checksum] can be partial
`git push <remote> <tag>` – push <tag> to <remote>
`git push <remote> --tags` – push all tags to <remote>
`git tag -d <tag>` – delete <tag> from local repository
`git push <remote> --delete <tag>` – delete <tag> from <remote> repository
