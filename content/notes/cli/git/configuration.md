---
title: configuration
date: 2022-10-23T09:52:51-0600
draft: false
weight: 1
---
# Configuration
## Config Files 
- `/etc/git/gitconfig` or `C:\Program Files\Git\etc\gitconfig` — config for all users on the system (`--system`)
- `~/.git` — config for all repositories of the current user (`--global`)
  - `~` is `$HOME` on Windows
- `.git/` — config for this repository only (`--local` (default))

# Configuration Commands
- `git config [scope] <key> <value>` set configuration \<key\> to \<value\>

# Checking Configuration
- `git config --list` — list all configuration settings Git can find
  - Note: Git uses the last value for each unique key it sees
- `git config <key>` return the value of \<key\>  
- `git config --show-origin <key>` return the origin (configuration file) of \<key\> and its value  

# One-Time Config
- `git config --global user.name "<name>"` — set your username  
- `git config --global user.email <email address>` — set your email address  
- `git config --global init.defaultBranch <name>` –set the default branch to \<name\> (recommend *main*)  
- `git config --global core.editor "<path>"` — set the default editor used when Git needs input  
- `git config --global credential.helper cache` set up a credential cache

# Aliases
- `git config --global alias.<alias> '<command>'` — create \<alias\> for \<command string\>
- `git config --global alias.last 'log -1 HEAD'` — return the last commit via last

## Common Aliases
- `git config --global alias.co checkout`
- `git config --global alias.br branch`
- `git config --global alias.ci commit`
- `git config --global alias.st status`
