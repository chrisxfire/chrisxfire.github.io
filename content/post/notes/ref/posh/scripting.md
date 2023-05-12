# Multi-line
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