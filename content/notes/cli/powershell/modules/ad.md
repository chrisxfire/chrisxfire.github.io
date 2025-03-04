---
title: ad
date: 2022-06-23T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2019-ps)  
> Module: `ActiveDirectory`

The Active Directory module requires [RSAT](https://learn.microsoft.com/en-us/troubleshoot/windows-server/system-management-components/remote-server-administration-tools) tools for Windows.

# manage user accounts
## locked accounts
Find locked user accounts:
```powershell
Search-AdAccount -LockedOut
```

Unlock user accounts:
```powershell
Unlock-ADAccount -Identity 'lockeduser'
```

Or, both in one command:
```powershell
Search-ADAccount -LockedOut | Unlock-ADAccount
```

### find the source of locked accounts
1. Find the Domain Controller with the PDCe role:
    ```powershell
    $pdce = Get-ADDomain.PDCEmulator
    ```

2. Check the Event Log for lockouts (ID 4740):
    ```powershell
    $filter = @{'LogName' = 'Security';'Id' = 4740}
    $events = Get-WinEvent -ComputerName $pdce -FilterHashTable $filter
    $events | Select-Object @{'Name' ='UserName'; Expression={$_.Properties[0]}}, @{'Name' ='ComputerName';Expression={$_.Properties[1]}}
    ```


# find an ad user by property
```powershell
Get-ADUser -Filter "EmployeeNumber -eq '000024'" -Properties *
```
