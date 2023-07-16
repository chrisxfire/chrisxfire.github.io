---
title: notes > code > .net > libraries > system.net > networkinformation
date: 2022-01-09T19:32:00-0700
draft: false
weight: 1
---
# System.Net.NetworkInformation
Types for working with low-level network protocols.

Common Types: `IPStatus`, `NetworkChange`, `Ping`, `TcpStatistics`

# Pinging
```cs
Ping ping = new();
PingReply reply = ping.Send(uri.Host);

reply.Status // ICMP success/failure?
reply.Address // The IP address that replied.
reply.RoundtripTime // Response time in milliseconds.
```
