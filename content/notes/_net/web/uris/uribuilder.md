---
title: uribuilder
date: 2021-11-28T09:03:08-0700
draft: false
weight: 1
---

# [System.UriBuilder](https://docs.microsoft.com/en-us/_net/api/system.uribuilder?view=net-6.0)
`Object` –> `UriBuilder`  

Construct and modify URIs for the Uri class.  

# [Construction](https://docs.microsoft.com/en-us/_net/api/system.uribuilder?view=net-6.0#constructors)
- `UriBuilder()` — Returns a new UriBuilder instance.
- `UriBuilder(string)` — Returns a new UriBuilder instance from string.
- `UriBuilder(Uri)` — Returns a new UriBuilder instance from Uri.

# Properties
Assuming a URI https://user:password@www.contoso.com:80/Home/Index.htm?q1=v1&q2=v2#FragmentName:
- `Fragment` — #FragmentName
- `Host` — [www.contoso.com](http://www.contoso.com)
- `Password` — password
- `Path` — /Home/Index.htm
- `Port` — 80
- `Query` — ?q1=v1&q2=v2
- `Scheme` — https
- `Uri` — https://user:password@www.contoso.com:80/Home/Index.htm?q1=v1&q2=v2#FragmentName
- `UserName` — user
