---
title: "notes > asp.net > core > web servers"
date: 2023-05-14T00:00:000-07:00
draft: false
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>

# Overview
ASP.NET on Windows ships with:
- Kestrel
- IIS HTTP Server (an in-process server for IIS)
- HTTP.sys

On IIS/Express:
- IIS HTTP Server—runs in same process as IIS worker process
- Kestrel—runs in separate process as IIS worker process

# Kestrel vs HTTP.sys
| Server | Performance | Cross-platform | Port and TLS configuration | Alternate transports | Port Sharing | Authentication | Fast proxying | Direct file transmission | Response caching |
|--------|-------------|----------------|----------------------------|----------------------|--------------|----------------|---------------|--------------------------|---------|
| Kestrel | Better | Yes | Yes | Yes | No | user-mode | No | No | No |
| HTTP.sys | Poorer | No | No | No | Yes | kernel-mode | Yes | Yes | Yes |

## Kestrel
Use Kestrel unless a feature that only HTTP.sys provides is required.

###  Use Cases
#### Edge server  
![Edge server](edge-server.png)

#### Reverse proxy  
![Reverse proxy](reverse-proxy.png)

## HTTP/2 Support
Both Kestrel and HTTP.sys require Windows 10/Server 2016 or later.
On Linux, Kestrel requires OpenSSL 1.0.2.
