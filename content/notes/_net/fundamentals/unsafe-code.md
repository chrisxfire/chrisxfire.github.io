---
title: unsafe code
date: 2024-12-13T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/fundamentals/unsafe-code
---

# Overview
> [!NOTE]
> Documentation: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/unsafe-code  
> Documentation: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/unsafe-code  

C# provides value types and reference types. It does not provide pointer types. *Safe code* does not directly access memory using pointers.

Pointer types (and, by extension, direct memory access) are needed for certain use cases:
- Interfacing with the underlying operating system
- Accessing a memory-mapped device
- Implementing a time-critical algorithm

In these and other use cases, *unsafe code* must be used. Unsafe code is code where it is possible to declare and operate on pointers, to take the 
address of variables, and so on. Unsafe code blocks must be marked with the `unsafe` modifier in the declaration of a type, member, or local function.