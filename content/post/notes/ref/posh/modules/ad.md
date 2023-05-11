# Find an AD User by Property
```powershell
Get-ADUser -Filter "EmployeeNumber -eq '000024'" -Properties *
```