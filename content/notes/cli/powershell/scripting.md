---
title: scripting
date: 2023-05-01T00:00:00-06:00
draft: false
weight: 1
---

# Flow Control
## For
```powershell
for ($i=1; $i -le 10; $i++) {
    # ...
}
```
## Foreach
```powershell
foreach ($item in $collection) {
    # ...
}
```
# Multi-line Statements
```powershell
$x = "Some really long `
value"
```

# Strings
## Concatenating
```powershell
$x = "together"
Write-Host "Smushed$x"
# or...
Write-Host "Smushed$($x)"
```
