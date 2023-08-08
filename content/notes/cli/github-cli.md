---
title: github cli
date: 2022-12-22T00:00:00-07:00
draft: false
weight: 1
---

# Authenticate
```powershell
gh auth login 
	--git-protocol ssh | https 
	--scopes strings
	--web
	--with-token # Read token from STDIN
gh auth logout
gh auth refresh
	--scopes strings
gh auth setup-git # Configure git to use GitHub CLI as credential helper
gh auth status
	--show-token
gh auth token
```

# Aliases
```powershell
gh alias set prd "pr create --draft" # gh prd will now run gh pr create --draft
```

# Browse
```powershell
gh browse # Open browser to issue/PR #
gh browse filename:line-number
gh browse
	--commit # Open the last commit
	--no-browser # Just print destination URL
	--projects # Open repo projects
	--repo owner/repo
	--settings # Open repo settings
	--wiki # Open repo wiki
```

# [Codespace](https://cli.github.com/manual/gh_codespace)
```powershell
gh codespace # Manage codespaces
```

# Config
```powershell
gh config get key
gh config list
gh config set key value
```

Keys:
```powershell
git_protocol # the protocol to use for git clone and push operations (default: "https")
editor # the text editor program to use for authoring text
prompt # toggle interactive prompting in the terminal (default: "enabled")
pager # the terminal pager program to send standard output to
http_unix_socket # the path to a Unix socket through which to make an HTTP connection
browser # the web browser to use for opening URLs
```

# Forks
```powershell
gh repo fork # Fork the current repo
gh repo fork owner/repo
gh repo fork --remote=false # Don't add a git remote
gh repo fork --clone=false # Don't clone the forked repo
```

# [Gist](https://cli.github.com/manual/gh_gist)
```powershell
gh gist
```

# [GPG-Key](https://cli.github.com/manual/gh_gpg-key)

# Help
```powershell
gh help command
```

# [Issues](https://cli.github.com/manual/gh_issue)
```powershell
gh issue create
gh issue create --title "title" --body "body"
gh issue create --web # Navigate to the issue on the web
gh issue list --assignee @me
gh issue status
gh issue view issue-#
```

# [Labels](https://cli.github.com/manual/gh_label)
```powershell
gh label
```

# [Pull Requests](https://cli.github.com/manual/gh_pr)
```powershell
gh pr create
gh pr create --title "title" --body "body"
gh pr create --web # Navigate to the PR on the web
gh pr checkout pr-# | branch-name | url
gh pr diff
gh pr list # The most recent 30 items
gh pr list --state closed --assignee user
gh pr review
gh pr status
gh pr view pr-#
```

# [Release](https://cli.github.com/manual/gh_release)
```powershell
gh release
```

# [Repo](https://cli.github.com/manual/gh_repo)
```powershell
gh repo clone owner/repo | url
gh repo view owner/repo
```

# [Run](https://cli.github.com/manual/gh_run)

# [Search](https://cli.github.com/manual/gh_search)

# [Secret](https://cli.github.com/manual/gh_secret)
```powershell
gh help secret set
```

# [SSH-Key](https://cli.github.com/manual/gh_ssh-key)

# [Status](https://cli.github.com/manual/gh_status)
Get status about your work across all of GitHub.

# [Workflow](https://cli.github.com/manual/gh_workflow)
Manage workflows for GitHub Actions.
