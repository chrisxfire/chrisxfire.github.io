---
title: troubleshooting
date: 2021-12-21T16:57:18-0700
draft: false
weight: 1
tags:
 - kb/cli/git
---

# Git is not respecting .gitignore
```powershell
git rm -rf --cached .
git add .
```

# Line endings ("LF will be replaced by CRLF")
Files with Unix-style (LF) line endings will be replaced by Windows-style (CRLF) line endings when running on Windows. This is likely because Git's `core.autocrlf` setting is `true`.

To prevent this:
```powershell
git config --system core.autocrlf false            # per-system solution
git config --global core.autocrlf false            # per-user solution
git config --local core.autocrlf false             # per-project solution
```

Note that this change is only for future files. To renormalize line endings for existing files:
```powershell
git add --renormalize .
```

[Learn more.](https://stackoverflow.com/questions/1967370/git-replacing-lf-with-crlf#:~:text=These%20messages%20are%20due%20to%20an%20incorrect%20default%20value%20of%20core.autocrlf%20on%20Windows.)

# SSL certificate problem: unable to get local issuer certificate
```powershell
git config --global http.sslbackend schannel
```
