---
title: troubleshooting
date: 2021-12-21T16:57:18-0700
draft: false
weight: 1
---
# Git is not respecting .gitignore
```powershell
git rm -rf --cached .
git add .
```

# SSL certificate problem: unable to get local issuer certificate
```powershell
git config --global http.sslbackend schannel
```
