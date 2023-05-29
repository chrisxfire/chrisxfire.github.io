---
title: "notes > dotnet > core > null state static analysis"
date: 2022-11-19T08:48:52-0700
draft: false
---
# Attributes
`using System.Diagnostics.CodeAnalysis;`

These attributes help to fully describe the null-state of arguments and return values in your APIs.
Adding these attributes gives the compiler more information about the rules for an API.
These attributes do not enable more checks.

# Preconditions
The `AllowNull` and `DisallowNull` are used to specify that preconditions on variables may not match the nullable annotations on those variables.

## `AllowNull`
This attribute applies to arguments.
Use when:
- The general contract fro that variable is that it should not be null, so a non-nullable reference is desired.
- There are scenarios for a caller to pass null as the argument.

## `DisallowNull`
Use this attribute to specify that an argument of a nullable reference type should not be null.
Example: a property where null is the default value but clients can only set it to a non-null value.

Use when:
- The variable could be null, often when first instantiated
- The variable should not be explicitly set to null

# Postconditions
## `MaybeNull`
Use when a method may return null when an item isn't found.

## `NotNull`
Use when a generic method returns an instance of its type parameter, `T`.
This attribute can also be applied to parameters.

# Conditional Postconditions
## `NotNullWhen`
Use on a parameter when the arguments could equal null but are known to be not null in certain conditions.

Example use:
```cs
bool IsNullOrEmpty([NotNullWhen(false)] string? value) // Informs compiler that if the result is false, the method will not return null.
```
## NotNullIfNotNull
Consider:
```cs
string? GetToplevelDomainFromUrl(string? url) // This works, but requires callers to implement extra null checks.
```
Instead:
```cs
[return: NotNullIfNotNull(nameof(url))] // This contract says this method will not return null if the caller does not pass a null argument.
string? GetToplevelDomainFromUrl(string? url)
```