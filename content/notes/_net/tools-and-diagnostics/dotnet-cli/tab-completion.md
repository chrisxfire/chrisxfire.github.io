---
title: tab completion
date: 2023-07-17T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/dotnet-cli
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/tools/enable-tab-autocomplete)
The `dotnet` driver supports tab completion. Below are instructions to enable it in PowerShell and Bash.

## powershell
Edit the profile at `$PROFILE`:
```powershell
# powershell parameter completion shim for the dotnet cli
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
    param($commandName, $wordToComplete, $cursorPosition)
        dotnet complete --position $cursorPosition "$wordToComplete" | 
    ForEach-Object {
        [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
    }
}
```

## bash
```bash
# bash parameter completion for the dotnet cli
function _dotnet_bash_complete()
{
    local cur="${COMP_WORDS[COMP_CWORD]}" IFS=$'\n' # On Windows you may need to use use IFS=$'\r\n'
    local candidates
    
    read -d '' -ra candidates < <(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)
    read -d '' -ra COMPREPLY < <(compgen -W "${candidates[*]:-}" -- "$cur")
}

complete -f -F _dotnet_bash_complete dotnet
```
