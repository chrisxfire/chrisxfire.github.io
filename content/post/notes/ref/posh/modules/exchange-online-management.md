```powershell
Install-Module -Name ExchangeOnlineManagement -Force

Update-Module -Name ExchangeOnlineManagement

Import-Module ExchangeOnlineManagement

Connect-ExchangeOnline -UserPrincipalName user@example.com

Disconnect-ExchangeOnline -Confirm:$false
```