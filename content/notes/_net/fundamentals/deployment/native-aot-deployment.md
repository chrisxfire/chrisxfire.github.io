---
title: notes > .net > fundamentals > deployment > native aot deployment
date: 2022-11-25T20:53:06-0700
draft: false
weight: 1
---
# Overview
Publishing as Native AOT produces a self-contained app that has been ahead-of-time compiled into native code.

# App Models
Console apps only.

# Requirements
- On Windows, Desktop Development w/C++ workload
- On Linux, clang, zlib1g-ev

# Limitations
- All limitations of trimming apply.
- All limitations of single-file deployments apply.
- No dynamic loading (`Assembly.LoadFile`)
- No runtime code generation (`System.Reflection.Emit`)

# Publishing
.csproj:
`<PublishAot>true</PublishAot>`

# Native Libraries
This capability also allows for publishing .NET class libraries that can be consumed from non-.NET languages.
