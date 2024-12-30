---
title: commit signatures
date: 2023-07-27T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/cli/git
---

# overview
Commits and tags can be signed via GPG, SSH, or S/MIME.

GPG signatures have the advantage over SSH signatures in that they can expire or be revoked.

GitHub automatically uses GPG to sign commits made via the web interface.  The GPG public key is available at https://github.com/web-flow.gpg.

# verification statuses
## default statuse
- Verified — commit is signed and signature verified
- Unverified — commit is signed but signature could not be verified
- No verification status — commit is not signed

## vigilant mode statuses
- Verified — commit signed, signature verified, committer is the only vigilant-mode author
- Partially verified — commit signed, signature verified, commit has an author who is not the committer and not a vigilant-mode author
- Unverified — either:
  - Commit signed, signature could not be verified
  - Commit not signed, committer has enabled vigilant mode
  - Commit not signed, author has enabled vigilant mode

# using gpg key commit signatures
## generate a new gpg key
```bash
gpg --full-generate-key
```
Follow the prompts.

## check existing keys
```bash
# Check for existing keys:
gpg --list-secret-keys --keyid-format=long

# Display key's public key for use with signatures:
gpg --armor --export KEY-ID

```
Copy your GPG key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----` 

## configure git to use a signing key
```bash
# Add the signing key to Git's config:
git config --global user.signingkey GPG-KEY
# If the above is a subkey, use KEY-ID! (with the ! suffix)

# Optionally, configure Git to sign all commits by default:
git config --global commit.gpgsign true
```

## associate an email with gpg key
The GPG key you use must be associated with a GitHub verified email that matches your committer identity.
1. [Find the key](#check-existing-keys)
2. Edit the key to add an email address:
```bash
gpg --edit-key KEY-ID

gpg> adduid
# follow the prompts

gpg> save
```

## add gpg key to github account
Profile Photo > **Settings** > Access > **SSH and GPG Keys** > GPG keys > **New GPG Key** > enter **Title** > enter **Key** > **Add GPG key** > 

## signing commits
On Windows, to store GPG key passphrase so you don't have to enter it each time you sign a commit, use https://www.gpg4win.org/.

Commit and add a commit signature:
```powershell
git commit -S -m "commit message"
```

Push as normal.

## signing tags
```powershell
git tag -s TAG-NAME
```
