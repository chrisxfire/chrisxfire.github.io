---
title: azure ad
date: 2022-06-02T00:00:00-06:00
draft: false
weight: 1
---

# Importing
Must use Windows PowerShell (not PowerShell 7)
```powershell
Import-Module AzureAd -UseWindowsPowerShell
```

# Connecting
```powershell
Connect-AzureAD
```

# Get a List of Groups of Which User is a Member  
```powershell
Get-AzureADUser -SearchString hanawayc@gejohnson.com | Get-AzureADUserMembership | % {Get-AzureADObjectByObjectId -ObjectId $_.ObjectId | select DisplayName,ObjectType,MailEnabled,SecurityEnabled,ObjectId} | Format-Table
```

# Get a List of groups of Which User is an Owner
```powershell
Get-AzureADUser -SearchString user@example.com | Get-AzureADUserOwnedObject
```
AzureAD POSH module is deprecated in favor of MS Graph.
