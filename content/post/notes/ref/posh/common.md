# Automatic Variables
| Variable | Description |
| -------- | ----------- |
| `$$` | Returns the last token in the last line received by the session |
| `$^` | Returns the first token in the last line received by the session |
| `$?` | Returns bool if the last command succeeded | 
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
| `$StackTrace` | The stack trace for the most recent error |

# Chaining Commands
Run `cmd2` only if `cmd1` succeeds: `cmd1 && cmd2`
Run `cmd2` only if `cmd1` fails: `cmd1 || cmd2`
Run `cmd1` and `cmd2` regardless of `cmd1`'s result: `cmd1; cmd2`

# Environment Variables  
Get:  `$Env:variable-name`  
Set:  
`$Env:variable-name = "*new-value*"`  
`$Env:variable-name += "*new-value-to-append*"`

Persist:
`[Environment]::SetEnvironmentVariable('*key*', '*value*', '*scope*')` # scope = `machine` or `user`

## Set environment variables
Set an environment variable for this session only:		    `set key="value"`  
Set an environment variable that persists:			        `setx key="value"`  
Set the environment variable in system intead of user:	    `setx /M key="value"`  
Set an environment variable that has a hierarchical key:	`set level1:level2="value"`  
- The `:` separator is not recognized on all platforms.  Use `__` instead:  `set level1__level2="value"`

# Files & Directories
## Cat Clipboard to File
`Get-Clipboard | Out-File filename`

## Copy Files / Directories
`copy /srcdir/subdir /dstdir/newsubdir -Recurse` # copy /srcdir/subdir and all of its files and subdirectories to /dstdir/newsubdir and create it if it doesn't exist

## Find
`gci -Path path -Recurse -Force` # path can include wildcards.

## Find String in Files Recursively
`gci -Path ./*.* -Recurse | Select-String -Path file -Pattern "*regex*"`  
    `-Context n, m` # Add n lines before and m lines after the match; matches are denoted with >

## "grep"
```powershell
Select-String  
  -Path path  
  -Pattern "*regex*" # The pattern to match  
  -Context n,m # Add n lines before and m lines after the match; matches are denoted with >
```

## Pipe to a File
`cmd | out-file filename`

## Remove Directory Recursively
`ri path -Recurse -Force`

## Remove File Recursively
`Get-ChildItem * -Include *.csv -Recurse | Remove-Item`

## "tail"
`Get-Content filename -Tail n`

## "tail -f"
`Get-Content path -Tail 1 -Wait`

## "touch"
`ni filename`

# History
`get-history` # Stored in `%userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline`

# PowerShell version
`$PSVersionTable`

# Profiles
Locations  
`AllUsersAllHosts`, `AllUsersCurrentHost`, `CurrentUserAllHosts`, `CurrentUserCurrentHost`

# Set a Profile
`notepad $Profile.Location`

# System Folders
`View:  [environment]::getfolderpath("*system-folder-name*")`

# Windows Services
`Get-Services [-DisplayName "*glob*"]`
