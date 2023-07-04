---
title: notes > code > cli > powershell > modules > exchange online management
date: 2022-06-02T00:00:00-06:00
draft: false
---

```powershell
Install-Module -Name ExchangeOnlineManagement -Force

Update-Module -Name ExchangeOnlineManagement

Import-Module ExchangeOnlineManagement

Connect-ExchangeOnline -UserPrincipalName user@example.com

Disconnect-ExchangeOnline -Confirm:$false
```
