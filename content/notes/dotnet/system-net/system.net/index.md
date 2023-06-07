---
title: "notes > dotnet > system net > system.net"
date: 2022-01-09T19:29:17-0700
draft: true
---
# System.Net
Types for working with network resources.

Common Types
- DNS, IP Addresses, and Web Requests: Dns, Uri, Cookie, WebClient, IPAddress
- FTP: FtpStatusCode, FtpWebRequest, FtpWebResponse

# Uri
string url = "<https://stack.overflow.com/search?q=securestring>";
Uri uri = new(url);

.Schemehttps
.Port443
.Hoststackoverflow.com
.Path/search
.Query?q=securestring

# IPHostEntry
IPHostEntry entry = Dns.GetHostEntry(uri.Host);

.HostNamestackoverflow.com

foreach (IPAddress address in entry.AddressList) {
// addressreturns 151.101.193.69
// address.AddressFamilyreturns InterNetwork
}