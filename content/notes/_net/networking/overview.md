---
title: overview
date: 2022-01-09T19:29:17-0700
draft: false
weight: -1
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

## IPHostEntry
```cs
IPHostEntry entry = Dns.GetHostEntry(uri.Host);

foreach (IPAddress address in entry.AddressList) 
{
    // address returns 151.101.193.69
    // address.AddressFamily returns InterNetwork
}
```

# System.Net.NetworkInformation
Types for working with low-level network protocols.

Common Types: `IPStatus`, `NetworkChange`, `Ping`, `TcpStatistics`

## Pinging
```cs
Ping ping = new();
PingReply reply = ping.Send(uri.Host);

reply.Status // ICMP success/failure?
reply.Address // The IP address that replied.
reply.RoundtripTime // Response time in milliseconds.
```
