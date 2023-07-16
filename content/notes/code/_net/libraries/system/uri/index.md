---
title: notes > code > .net > libraries > system > uri
date: 2021-11-28T08:30:06-0700
draft: false
---
# [System.Uri](https://docs.microsoft.com/en-us/dotnet/api/system.uri?view=net-6.0)
`Object` –> `Uri`  

An object representation of a URI.  

# [Construction](https://docs.microsoft.com/en-us/dotnet/api/system.uri?view=net-6.0#constructors)
## From String
```cs
Uri uri = new Uri("https://user:password@www.contoso.com:80/Home/Index.htm?q1=1&q2=v2#FragmentName");
```
## Specify Base URI or Relative URI
```cs
Uri uri = new Uri(string "s", UriKind.Absolute); // or UriKind.Relative.
// or
Uri uri = new Uri(Uri baseUri, string "relativeUriString");
// or
Uri uri = new Uri(Uri baseUri, Uri relativeUri);
```

# [Fields](https://docs.microsoft.com/en-us/dotnet/api/system.uri.schemedelimiter?view=net-6.0)
Various fields are available for different URI schemes such as File, FTP, SSH, Telnet, etc.

# Properties
- `AbsolutePath` — /Home/Index.htm
- `AbsoluteUri`  — https://user:password@www.contoso.com:80/Home/Index.htm?q1=v1&q2=v2#FragmentName
- `DnsSafeHost` — [www.contoso.com](http://www.contoso.com)
- `Fragment` — #FragmentName
- `Host` — [www.contoso.com](http://www.contoso.com)
- `HostNameType` — Dns
- `IdnHost` — [www.contoso.com](http://www.contoso.com)
- `IsAbsoluteUri` — True
- `IsDefaultPort` — False
- `IsFile` — False
- `IsLoopback` — False
- `IsUnc` — False
- `LocalPath` — /Home/Index.htm
- `OriginalString` — https://user:password@www.contoso.com:80/Home/Index.htm?q1=v1&q2=v2#FragmentName
- `PathAndQuery` — /Home/Index.htm?q1=v1&q2=v2
- `Port` — 80
- `Query` — ?q1=v1&q2=v2
- `Scheme` — https
- `Segments` — /, Home/, Index.htm
- `UserEscaped` — False
- `UserInfo` — user:password

# Methods
- `CheckHostName(string)` — Returns a UriHostNameType indicating if this is a valid hostname or IP address.
- `CheckSchemeName(string)` — Boolean if string equals a specific Uri.UriScheme
- `EscapeDataString(string)` — Returns string as an escaped Uri string.
- `IsWellFormedOriginalString()` — Boolean if string used to build this Uri was well-formed and properly escaped.
- `IsWellFormedUriString(string, UriKind)` — Boolean if string is a well-formed Uri of UriKind.
- `TryCreate(baseUri, relativeUri, out Uri)` — Boolean if URI created successfully and stored to Uri.
- `UnescapeDataString(string)` — Returns string as an unescaped Uri string.
