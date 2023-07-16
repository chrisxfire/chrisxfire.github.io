---
title: notes > operating systems > linux > debian > pki > fixing legacy trusted.gpg keyring issue
date: 2023-07-02T00:00:00-06:00
draft: false
---

# Overview
This warning means that a key is stored in `/etc/apt/trusted.gpg` which is a deprecated keyring:
```
W: https://example.com/repo: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
```

# Fixing
1. Find the offending key:
    ```bash
    sudo apt-key list | grep -i <keyword> --before --after 3
    ```

    Any keys marked `expired` can be ignored.

    An offending key will be listed under the /etc/apt/trusted.gpg section like this:
    ```
    pub   rsa4096 2015-03-22 [SC]
          CD66 5CBA 0E2F 88B7 373F  7CB9 9720 3C7B 3ADC A79D
    uid           [ unknown] Plex Inc.
    sub   rsa4096 2015-03-22 [E]
    ```

    The line we are interested in is `CD66 5CBA 0E2F 88B7 373F  7CB9 9720 3C7B 3ADC A79D`.
2. From the line above, take the last 8 characters and remove the space, resulting in `3ADCA79D`.  Import that GPG key in its dedicated file:
   ```bash
   sudo apt-key export 3ADCA79D | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/plex.gpg
   ``` 
