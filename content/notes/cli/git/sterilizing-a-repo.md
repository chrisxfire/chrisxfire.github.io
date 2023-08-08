---
title: sterilizing a repo
date: 2022-03-04T20:41:48-0700
draft: false
weight: 1
---
1.  `git clone --mirror https://github.com/user/repo.git`
2.  `java -jar bfg.jar --delete-folders "{one,two,three}" repo.git`
3.  `cd repo.git`
4.  `git reflog expire --expire=now --all && git gc --prune=now --aggressive`
5.  `git push`
