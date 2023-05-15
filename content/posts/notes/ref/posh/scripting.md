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