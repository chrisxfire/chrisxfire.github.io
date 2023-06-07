---
title: "notes > dotnet > system net > networkinformation"
date: 2022-01-09T19:32:00-0700
draft: true
---
# System.Net.NetworkInformation
Types for working with low-level network protocols.

Common Types: IPStatus, NetworkChange, Ping, TcpStatistics

# Pinging
Ping ping = new();
PingReply reply = ping.Send(uri.Host);

reply.StatusICMP success/failure?
reply.AddressThe IP address that replied.
reply.RoundtripTimeResponse time in milliseconds.