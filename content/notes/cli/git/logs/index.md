---
title: "notes > cli > git > logs"
date: 2022-10-23T16:05:41-0600
draft: true
---
# Logs
git logreturn commits made in this repository
git log *vX.X..vY.Y | helper-script > changelogs/Y.Y*
- generate changelogs
- see also: <https://github.com/github-changelog-generator/github-changelog-generator>
- see also: <https://pypi.org/project/gitchangelog/>
git log *branch*return commits of *branch*
--allreturn commits of all branches
-<n>return only the last *n* entries
--after <date>only return results after <date>; format of <date> is either YYY-MM-DD or relative
--before <date>only return results before <date>
--allreturn commit history for all branches
--decoratereturn where the branch pointers are pointing
--followlist version history for a file, including renames
--graphreturn an ASCII graph depicting branch and merge history
--no-mergesdo not return merge commits
--prettyreturn pretty-printed results
--pretty=onelinereturn each commit on a single line. also short, full and fuller
--pretty=formatreturn results formatted with a specification language
--patchreturn the difference introduced in each commit
--relative-datedisplay dates in a relative format ("2 weeks ago")
--statreturn abbreviated stats for each commit
-S *string*return only commits that changed the number of occurrences of *string*
-- *path*return only results that introduced changes to file(s) at *path*