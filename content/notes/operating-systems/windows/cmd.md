---
title: notes > operating systems > windows > cmd
date: 2017-04-03T00:00:00-06:00
draft: false
weight: 1
---

# Disk Management
## Recover flash drive
```batchfile
diskpart
list disk
select disk *#*
clean
create partition primary
--optional--
list volume
select volume *#*
format fs=ntfs quick
```

# Files & Directories
`dir /p` *wildcard search* # Pause at each screen
`dir /s` *wildcard search* # traverse through Subdirectories as well

# Find Local Administrators
`net localgroup administrators`

## Mapping Drives
`net use` # show list of mapped drives
`net use DRIVE: PATH` # map PATH to DRIVE
`net use DRIVE: PATH /persistent:Yes` # make this drive mapping persistent
`net use DRIVE: PATH /user:USER PASSWORD` # make this mapping with USER PASSWORD credentials
`net use DRIVE: /delete` # delete this drive mapping
`net use * /delete` # delete all mapped drives

# Group Policy
`gpresult /Scope User /view` # all Policies applied to the current user  
`gpresult /Scope Computer /v` # view all Policies applied to this computer  
`gpresult /h` # instead of outputting to the console, save as HTML file  
`rsop.msc` # Resultant Set of Policy report

# Network
## Net Shell
`netsh wlan show profile name=labnol key=clear`	# Find the wifi password of your current network
`netsh interface ipv4 set address name="*interface name* static *IP Address* *subnet mask* *gateway*` # Change your IP address

## Reset Network Adapter
`netsh int ip reset`  
`netsh winsock reset`  
`ipconfig /release`  
`ipconfig /flushdns`  
`ipconfig /renew`  

# OS Image Management
`dism /online /cleanup-image /checkhealth` # reports whether the image is healthy, repairable, or not repairable
`dism /online /cleanup-image /restorehealth` # repairs a broken image

# Performance Monitor
`perfmon /report` # Performance monitor system report

# Robocopy
usage: `robocopy *source* *destination* *options*`
common: 
- `robocopy /S` # copy Subdirectories  
- `robocopy /B` # copy files in Backup mode  
- `robocopy /MIR` # Mirror the source directory at the destination directory  
- `robocopy /R:*n*` # Retry *n* times  
- `robocopy /W:*n*` # Wait *n* seconds before retries  
- `robocopy /L` # List only (like --dry-run)  
- `robocopy /X` # Report all eXtra files, not just those selected  
- `robocopy /V` # Verbose logging  
- `robocopy /FP` # Include Full Pathname in the output
- `robocopy /LOG+:*file*` # Output log to *file*, appending
- `robocopy /TEE` # Output to console window as well as log file
- `robocopy /SAVE:*jobname*` # Saves parameters to jobfile *jobname*
- `robocopy /LOAD:*jobname*` # Loads parameters from jobfile *jobname*

`robocopy "C:\Users\chris\Google Drive" Z:\public\google-drive /S /MIR /R:5 /W:30 /TEE /V /LOG+:C:\Users\chris\Dropbox\Logs\robocopy.log /SAVE:gdrive-to-optiplex`

# User Account
## Unlocking
`net user *account* /domain | find /I "Account Active"`

If no:
`net user *account* /domain /active:YES`

# Windows Update Service
## Restarting the Windows Update service
```batchfile
net stop bits
net stop wuauserv
net stop appidsvc
net stop cryptsvc
```
