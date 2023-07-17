---
title: notes > cli > git > logs
date: 2022-10-23T16:05:41-0600
draft: false
weight: 1
---
# Logs
`git log` – return commits made in this repository
`git log vX.X..vY.Y | helper-script > changelogs/Y.Y`
- generate changelogs
- see also: <https://github.com/github-changelog-generator/github-changelog-generator>
- see also: <https://pypi.org/project/gitchangelog/>

`git log <branch>` – return commits of branch
`--all` – return commits of all branches
`-<n>` – return only the last n entries
`--after <date>` – only return results after <date>; format of <date> is either YYY-MM-DD or relative
`--before <date>` – only return results before <date>
`--all` – return commit history for all branches
`--decorate` – return where the branch pointers are pointing
`--follow` – list version history for a file, including renames
`--graph` – return an ASCII graph depicting branch and merge history
`--no-merges` – do not return merge commits
`--pretty` – return pretty-printed results
`--pretty=oneline` – return each commit on a single line. also short, full and fuller
`--pretty=format` – return results formatted with a specification language
`--patch` – return the difference introduced in each commit
`--relative-dated` – isplay dates in a relative format ("2 weeks ago")
`--stat` – return abbreviated stats for each commit
`-S string` – return only commits that changed the number of occurrences of string
`-- path` – return only results that introduced changes to file(s) at path
