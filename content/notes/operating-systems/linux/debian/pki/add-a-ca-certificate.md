---
title: add a ca certificate
date: 2023-06-12T00:00:00-06:00
draft: false
weight: 1
---

# add a ca certificate to a debian linux server
```bash
cp <path/to/ca-cert-file.crt> /usr/local/share/ca/certificates/
sudo update-ca-certificates
```
