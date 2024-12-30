---
title: azure ad
date: 2022-06-02T00:00:00-06:00
draft: false
weight: 1
---

# importing
Must use Windows PowerShell (not PowerShell 7)
```powershell
Import-Module AzureAd -UseWindowsPowerShell
```

# connecting
```powershell
Connect-AzureAD
```

# get a list of groups of which user is a member  
```powershell
Get-AzureADUser -SearchString hanawayc@gejohnson.com | Get-AzureADUserMembership | % {Get-AzureADObjectByObjectId -ObjectId $_.ObjectId | select DisplayName,ObjectType,MailEnabled,SecurityEnabled,ObjectId} | Format-Table
```

# get a list of groups of which user is an owner
```powershell
Get-AzureADUser -SearchString user@example.com | Get-AzureADUserOwnedObject
```
AzureAD POSH module is deprecated in favor of MS Graph.
