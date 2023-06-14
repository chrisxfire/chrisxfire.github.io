---
title: "notes > asp.net > ef core > logging events and diagnostics > overview"
date: 2023-06-14T00:00:00-06:00
draft: true
---

# Logging Mechanisms Quick Reference
| Mechanism                    | Async | Scope       | Registered                  | Intended Use               |
| ---------------------------- | ----- | ----------- | --------------------------- | -------------------------- |
| Simple logging               | No    | Per context | Context configuration       | Development-time logging   |
| Microsoft.Extensions.Logging | No    | Per context | DI or context configuration | Production logging         |
| Events                       | No    | Per context | Any time                    | Reaching to EF events      |
| Interceptors                 | Yes   | Per context | Context configuration       | Manipulating EF operations |
| Diagnostics listeners        | No    | Process     | Globally                    | Application diagnostics    |