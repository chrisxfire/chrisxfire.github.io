---
title: cmd
date: 2017-04-03T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/operating-systems/windows/cmd
---

# certificate management
Find available encryption algorithms:
`certutil -oid 2 | findstr pwszCNGAlgid`

Find available hash algorithms:
`certutil -oid 1 | findstr pwszCNGAlgid | findstr /v CryptOIDInfo`

Find available CSPs:
`certutil -csplist`
# disk management
## recover flash drive
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

# find local administrators
`net localgroup administrators`

## mapping drives
`net use` # show list of mapped drives
`net use DRIVE: PATH` # map PATH to DRIVE
`net use DRIVE: PATH /persistent:Yes` # make this drive mapping persistent
`net use DRIVE: PATH /user:USER PASSWORD` # make this mapping with USER PASSWORD credentials
`net use DRIVE: /delete` # delete this drive mapping
`net use * /delete` # delete all mapped drives

# group policy
`gpresult /Scope User /view` # all Policies applied to the current user  
`gpresult /Scope Computer /v` # view all Policies applied to this computer  
`gpresult /h` # instead of outputting to the console, save as HTML file  
`rsop.msc` # Resultant Set of Policy report

# network
## net shell
`netsh wlan show profile name=labnol key=clear`	# Find the wifi password of your current network
`netsh interface ipv4 set address name="*interface name* static *IP Address* *subnet mask* *gateway*` # Change your IP address

## reset network adapter
`netsh int ip reset`  
`netsh winsock reset`  
`ipconfig /release`  
`ipconfig /flushdns`  
`ipconfig /renew`  

# os image management
`dism /online /cleanup-image /checkhealth` # reports whether the image is healthy, repairable, or not repairable
`dism /online /cleanup-image /restorehealth` # repairs a broken image

# performance monitor
`perfmon /report` # Performance monitor system report

# robocopy
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
- `robocopy /SAVE:JOB_NAME` # Saves parameters to jobfile *jobname*
- `robocopy /LOAD:JOB_NAME` # Loads parameters from jobfile *jobname*

`robocopy "C:\Users\chris\Google Drive" Z:\public\google-drive /S /MIR /R:5 /W:30 /TEE /V /LOG+:C:\Users\chris\Dropbox\Logs\robocopy.log /SAVE:gdrive-to-optiplex`

# user account
## unlocking
`net user ACCOUNT_NAME /domain | find /I "Account Active"`

If no:
`net user ACCOUNT_NAME /domain /active:YES`

# windows update service
## restarting the windows update service
```batchfile
net stop bits
net stop wuauserv
net stop appidsvc
net stop cryptsvc
```
