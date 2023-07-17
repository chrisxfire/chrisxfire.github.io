---
title: notes > cli > git > gitignore
date: 2022-10-23T16:07:20-0600
draft: false
weight: 1
---

# Overview
gitignore files specify intentional untracked files that Git should ignore.

# Order of Precedence
1. Patterns from the command line
2. Patterns from `.gitignore` file in same directory
3. Patterns from `.gitignore` file in parent directories up to the top level of the working tree
4. Patterns from `$GIT_DIR/info/exclude`
5. Patterns from the file specified by `core.excludesFile`

# Pattern Format
- `#` for comments
- `\` for escapes
- `/` as the directory separator char
    - `/` at the end of a pattern matches directories only
- `!` to negate the pattern; any matching file excluded by the previous pattern will be included again
    - Unless the parent directory of that file is excluded
- `*` matches anything except `/`
- `**` followed by `/` means match all directories:
    - `**/foo` matches a file or directory named `foo` anywhere (the saame as the pattern `foo`)
    - `**/foo/bar` matches file or directory `bar` anywhere directly under directory `foo`
    - `a/**/b` matches a/b, a/x/b, a/x/y/b, and so on.
- `?` matches any one character except `/`
    - Range notation `[a-zA-Z]` can be used to match one of the characters in the range

- Trailing spaces are ignored (unless escaped)

# Ignoring Files
If the file is currently tracked:
1. `git rm <glob> --cached` to remove the file from the index
2. Add the pattern to `.gitignore`
