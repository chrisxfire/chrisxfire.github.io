---
title: notes > code > .net > namespaces > system.diagnostics.codeanalysis
date: 2023-07-15T00:00:00-06:00
draft: false
---

# Overview
Classes used to analyze code for conformance to coding conventions.
| Class                                   | Description                                                                                                                                                                 |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `AllowNullAttribute`                    | Specifies that null is allowed as an input even if the corresponding type disallows it.                                                                                     |
| `ConstantExpectedAttribute`             | Indicates that the specified method parameter expects a constant.                                                                                                           |
| `DisallowNullAttribute`                 | Specifies that null is disallowed as an input even if the corresponding type allows it.                                                                                     |
| `DoesNotReturnAttribute`                | Specifies that a method that will never return under any circumstance.                                                                                                      |
| `DoesNotReturnIfAttribute`              | Specifies that the method will not return if the associated Boolean parameter is passed the specified value.                                                                |
| `DynamicallyAccessedMembersAttribute`   | Indicates that certain members on a specified Type are accessed dynamically, for example, through System.Reflection.                                                        |
| `DynamicDependencyAttribute`            | States a dependency that one member has on another.                                                                                                                         |
| `ExcludeFromCodeCoverageAttribute`      | Specifies that the attributed code should be excluded from code coverage information.                                                                                       |
| `MaybeNullAttribute`                    | Specifies that an output may be null even if the corresponding type disallows it.                                                                                           |
| `MaybeNullWhenAttribute`                | Specifies that when a method returns ReturnValue, the parameter may be null even if the corresponding type disallows it.                                                    |
| `MemberNotNullAttribute`                | Specifies that the method or property will ensure that the listed field and property members have values that aren't null.                                                  |
| `MemberNotNullWhenAttribute`            | Specifies that the method or property will ensure that the listed field and property members have non-null values when returning with the specified return value condition. |
| `NotNullAttribute`                      | Specifies that an output is not null even if the corresponding type allows it. Specifies that an input argument was not null when the call returns.                         |
| `NotNullIfNotNullAttribute`             | Specifies that the output will be non-null if the named parameter is non-null.                                                                                              |
| `NotNullWhenAttribute`                  | Specifies that when a method returns ReturnValue, the parameter will not be null even if the corresponding type allows it.                                                  |
| `RequiresAssemblyFilesAttribute`        | Indicates that the specified member requires assembly files to be on disk.                                                                                                  |
| `RequiresDynamicCodeAttribute`          | Indicates that the specified method requires the ability to generate new code at runtime, for example through System.Reflection.                                            |
| `RequiresUnreferencedCodeAttribute`     | Indicates that the specified method requires dynamic access to code that is not referenced statically, for example, through System.Reflection.                              |
| `SetsRequiredMembersAttribute`          | Specifies that this constructor sets all required members for the current type, and callers do not need to set any required members themselves.                             |
| `StringSyntaxAttribute`                 | Specifies the syntax used in a string.                                                                                                                                      |
| `SuppressMessageAttribute`              | Suppresses reporting of a specific code analysis rule violation, allowing multiple suppressions on a single code artifact. Does not apply to compiler diagnostics.          |
| `UnconditionalSuppressMessageAttribute` | Suppresses reporting of a specific rule violation, allowing multiple suppressions on a single code artifact.                                                                |
| `UnscopedRefAttribute`                  | Used to indicate a byref escapes and is not scoped                                                                                                                          | . |

# StringSyntaxAttribute
Attribute to indicate what kind of syntax is expected in a string.

For example, you can specify that a string parameter expects a regular expression by attributing the parameter with `[StringSyntax(StringSyntaxAttribute.Regex)]`.