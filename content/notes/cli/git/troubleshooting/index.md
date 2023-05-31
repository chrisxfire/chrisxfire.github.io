---
title: "notes > cli > git > troubleshooting"
date: 2021-12-21T16:57:18-0700
draft: true
---
# Git is not respecting .gitignore
git rm -rf --cached .
git add .

# SSL certificate problem: unable to get local issuer certificate
git config --global http.sslbackend schannel