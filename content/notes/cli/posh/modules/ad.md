---
title: "notes > ref > posh > modules > ad"
date: 2023-01-01T00:00:00-06:00
draft: true
---

# Find an AD User by Property
```powershell
Get-ADUser -Filter "EmployeeNumber -eq '000024'" -Properties *
```