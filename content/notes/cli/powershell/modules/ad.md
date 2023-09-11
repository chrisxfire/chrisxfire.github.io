---
title: ad
date: 2022-06-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2019-ps  
> Module: `ActiveDirectory`

The Active Directory module requires [RSAT](https://learn.microsoft.com/en-us/troubleshoot/windows-server/system-management-components/remote-server-administration-tools) tools for Windows.

# Manage User Accounts
## Locked Accounts
Find locked user accounts:
```powershell
Search-AdAccount -LockedOut
```

### Find the Source of Locked Accounts
1. Find the Domain Controller with the PDCe role:
    ```powershell
    $pdce = Get-ADDomain.PDCEmulator
    ```

2. Check the Event Log for lockouts (ID 4740):
    ```powershell
    Get-WinEvent -ComputerName $pdce -FilterHashTable @{'LogName' ='Security';'Id' = 4740}
    ```


# Find an AD User by Property
```powershell
Get-ADUser -Filter "EmployeeNumber -eq '000024'" -Properties *
```
