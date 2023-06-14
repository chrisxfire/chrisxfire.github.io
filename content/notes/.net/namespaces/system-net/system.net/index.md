---
title: notes > .net > namespaces > system net > system.net
date: 2022-01-09T19:29:17-0700
draft: false
---
# System.Net
Types for working with network resources.

Common Types
- DNS, IP Addresses, and Web Requests: `Dns`, `Uri`, `Cookie`, `WebClient`, `IPAddress`
- FTP: `FtpStatusCode`, `FtpWebRequest`, `FtpWebResponse`

# Uri
```cs
string url = "https://stackoverflow.com/search?q=securestring";
Uri uri = new(url);
```

## Fields
- `.Scheme` — https
- `.Port` — 443
- `.Host` — stackoverflow.com
- `.Path` — /search
- `.Query` — ?q=securestring

# IPHostEntry
```cs
IPHostEntry entry = Dns.GetHostEntry(uri.Host);

foreach (IPAddress address in entry.AddressList) 
{
    // addressreturns 151.101.193.69
    // address.AddressFamilyreturns InterNetwork
}
```
