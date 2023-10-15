---
title: pipes
date: 2023-10-14T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/io/pipe-operations

Pipes provide means for interprocess communication.  There are two types:
1. *Anonymous pipes* provide interprocess communication on a local computer.
2. *Named pipes* provide interprocess communication over a network.

| Pipe Type | Communication<br />Direction | Server Instances | Used for communication between...         | Implemented Via                                                    |
| --------- | ---------------------------- | ---------------- | ----------------------------------------- | ------------------------------------------------------------------ |
| Anonymous | One-way                      | Single           | Threads or between parent/child processes | `AnonymousPipeServerStream` <br /> and `AnonymousPipeClientStream` |
| Named     | Duplex                       | Multiple         | Two processes over a network              | `NamedPipeServerStream` <br /> and `NamedPipeClientStream`         |
