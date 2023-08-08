---
title: openssh
date: 2023-05-21T00:00:00-06:00
draft: false
weight: 1
---

# Public-key Cryptography / Asymmetric Encryption
## Generate a public/private keypair
1. Use ssh-keygen to generate a public/private keypair: `ssh-keygen -t ed25519`
2. The keys are stored in ~./ssh as `id_ed25519` and `id_ed25519.pub`

## Trust the public key on OpenSSH Server
Add the contents of `id_ed25519.pub` to `./ssh/authorized_keys`
