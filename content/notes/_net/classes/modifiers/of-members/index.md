---
title: notes > .net > classes > modifiers > of members
date: 2022-02-17T20:58:37-0700
draft: false
---
# Access Modifiers (Accessibility)
The accessibility of the return type and parameter types of a method, indexer, or delegate must be >= that of the member itself:
- For a public method `M` that returns class `C`, `C` must also be public.
- For a protected property of Type `A`, `A` cannot be private.

## Struct Members
Default: `private`  
Options: `public`, `internal`, `private`

## Class Members
Default: `private`  
Options: `public`, `protected`, `internal`, `protected internal`, `private protected`, `private`

## Interface Members
Default: `public`   
Options: `public`, `protected`, `internal`, `protected internal`, `private protected`, `private`

## Enumeration Members
Always `public`. No access modifiers allowed.

## Operators
Must always be `public` and `static`.

## Finalizers
Finalizers cannot have access modifiers.
