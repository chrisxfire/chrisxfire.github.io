---
title: "notes > operating systems > linux > debian > pki > add a ca certificate"
date: 2023-06-12T00:00:00-06:00
draft: false
---

# Add a CA Certificate to a Debian Linux Server
```bash
cp <path/to/ca-cert-file.crt> /usr/local/share/ca/certificates/
sudo update-ca-certificates
```
