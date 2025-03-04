---
title: overview
date: 2021-12-02T00:00:00-06:00
draft: false
weight: -1
---

# automatic variables
| Variable | Description |
| -------- | ----------- |
| `$$` | Returns the last token in the last line received by the session |
| `$^` | Returns the first token in the last line received by the session |
| `$?` | Returns bool if the last command succeeded | 
| `$_` | Alias to `$PSItem`.  Returns the current object in the pipeline object.  Use in commands that perform an action on every object in the pipeline. | 
| `$Error` | Returns an array of error objects of the most recent errors |
| `$HOME` | Returns the full path of the user's home directory (same as $env:USERPROFILE) |
| `$Host` | An object that represents the current host application for PowerShell |
| `$isCoreCLR` | |
| `$isLinux` | |
| `$isMacOS` | |
| `$isWindows` | |
| `$LASTEXITCODE` | Returns the exit code of the last native program or PowerShell script ran |
| `$PROFILE` | The full path of the posh profile for the current user and current host application | 
| `$PSHOME` | The full path of the installation directory for posh |
| `$PWD` | The current working directory |
| `$StackTrace` | The stack trace for the most recent error |

# chaining commands
Run `cmd2` only if `cmd1` succeeds: `cmd1 && cmd2`  
Run `cmd2` only if `cmd1` fails: `cmd1 || cmd2`  
Run `cmd1` and `cmd2` regardless of `cmd1`'s result: `cmd1; cmd2`  

# environment variables  
Get:  
```powershell
$Env:variable-name
```
Set:  
```powershell
$Env:variable-name = "new-value"  
$Env:variable-name += "new-value-to-append"
```

Persist:
```powershell
[Environment]::SetEnvironmentVariable('key', 'value', 'scope') # scope = machine or user
```

## set environment variables
Set an environment variable for this session only:		    `set key="value"`  
Set an environment variable that persists:			        `setx key="value"`  
Set the environment variable in system intead of user:	    `setx /M key="value"`  
Set an environment variable that has a hierarchical key:	`set level1:level2="value"`  
- The `:` separator is not recognized on all platforms.  Use `__` instead:  `set level1__level2="value"`

# Files & Directories
## cat clipboard to file
```powershell
Get-Clipboard | Out-File filename
```

## Copy Files / Directories
```powershell
copy /srcdir/subdir /dstdir/newsubdir -Recurse # copy /srcdir/subdir and all of its files and subdirectories to /dstdir/newsubdir and create it if it doesn't exist
```

## cwd
```powershell
Get-Location
```

## find
```powershell
gci -Path <starting-path> `
    -Include <glob> `
    -Directory <# if only directories should be returned, not files #>`
    -File <# if only files should be returned, not directories #>`
    -Exclude <glob>
    -ErrorAction SilentlyContinue
    -Recurse -Force
```

## "grep"
```powershell
Get-ChildItem -Path ./*.<EXT> -Recurse | Select-String 
  -Pattern "<REGEX>" <# The pattern to match #>`
  -Context n,m <# Add n lines before and m lines after the match; matches are denoted with > #>
  -Raw # Don't output file names
```

## pipe to a file
```powershell
cmd | out-file filename
```

## pipe to a file and console
```powershell
cmd | Tee-Object -File filename
```

## remove directory recursively
```powershell
ri path -Recurse -Force
```

## remove file recursively
```powershell
Get-ChildItem  -Include .csv -Recurse | Remove-Item
```

## "tail"
```powershell
Get-Content filename -Tail n
```

## "tail -f"
```powershell
Get-Content path -Tail 1 -Wait
```

## "touch"
```powershell
ni filename
```

## write to a file
```powershell
Set-Content -Path ./path/to/file.txt -Value 'Hello, World'
```

## write to a specific line in a file
```powershell
$fileContent = Get-Content $filePath
$fileContent[$lineNumber-1] += $textToAdd
$fileContent | Set-Content $filePath
```

# history
```powershell
get-history # Stored in `%userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline`
```

# powershell version
```powershell
$PSVersionTable
```

# profiles
Locations  
`AllUsersAllHosts`, `AllUsersCurrentHost`, `CurrentUserAllHosts`, `CurrentUserCurrentHost`

# set a profile
```powershell
notepad $Profile.Location
```

# system folders
```powershell
[environment]::getfolderpath("system-folder-name")
```

# windows services
```powershell
Get-Services [-DisplayName "glob"]
```
