---
title: modifiers
date: 2022-11-25T21:11:47-0700
draft: false
weight: 1
---

# Access Modifiers
- `public` – Access is unrestricted.
- `private` – Access is limited to this type in this assembly only.
- `protected` – Access is limited to this type or derivatives, or derivatives in a referenced assembly.
- `internal` – Access is limited to this assembly only.
- `protected internal` – Combination of protected + internal.
- `private protected` – Combination of private + protected.

| Modifier              | This Assembly (Derived Type) | This Assembly (Other Type) | External Assembly (Derived Type) | External Assembly (Other Type) |
| -------------------- | ---------------------------- | -------------------------- | -------------------------------- | ------------------------------ |
| public               | yes                          | yes                        | yes                              | yes                            |
| private              | no                           | no                         | no                               | no                             |
| protected            | yes                          | no                         | yes                              | no                             |
| internal             | yes                          | yes                        | no                               | no                             |
| protected (internal) | yes                          | yes                        | yes                              | no                             |
| private (internal)   | yes                          | no                         | no                               | no                             |

# Other Modifiers
- `virtual` – This member *may* be overridden in a derived type.  
- `abstract` – This type <u>must</u> be overridden in a derived type.  
  - It has no implementation.
  - It cannot be instantiated.
- `override` – This member provides a new implementation of the base type's `virtual` or `abstract` member.
- `sealed` – This type cannot be further overridden in a derived type.
  - Only overridden types can be sealed.

# Access Modifiers for Members
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

# `file` Modifier
Restricts top-level type's scope and visibility to the file in which it is declared.  
Declares a file-local type.  
Generally applied to types written by a source generator.  

`Classes.cs`:
```cs
// Only visible in Classes.cs
file class HiddenClass 
{
    // ...   
}
```

