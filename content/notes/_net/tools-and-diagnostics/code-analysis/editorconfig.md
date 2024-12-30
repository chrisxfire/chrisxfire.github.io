---
title: editorconfig
date: 2022-11-17T15:45:22-0700
draft: false
weight: 1
---

# overview
EditorConfig is a cross-platform file format for defining code styles.

# file format
- EditorConfig files consist of *preambles* (the lines that precede the first section), *section names* (between brackets), and *sections* (which run from the beginning of the section header to the beginning of the next section header).
- Comments start with `;` or `#`
  - No inline comments

## Section Headers are enclosed in `[ ]`
- No non-whitespace characters outside brackets
- May contain characters and whitespace between brackets
- Path separators are always `/`

## sections
Key-Value Pairs are of format `key=value`

## globs
| Character      | Matches                           |
| -------------- | --------------------------------- |
| `*`            | any string except `/`             |
| ``             | any string                        |
| `?`            | any single character except `/`   |
| `[seq]`        | any single character in *seq*     |
| `[!seq]`       | any single character not in *seq* |
| `{s1, s2, s3}` | any of these strings              |
| `{1..5}`       | any digit 1 through 5             |

## properties
### Widely-supported Properties
| Property                   | Definition                                               | Possible values                                        |
| -------------------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| `indent_style`             | The indentation style                                    | `tab`, `space`                                         |
| `indent_size`              | The size of indentation                                  | *integer*, `tab`                                       |
| `tab_width`                | Width of a single tabstop                                | *integer*                                              |
| `end_of_line`              | Line ending file format                                  | `lf`, `crlf`, `cr`                                     |
| `charset`                  | File character encoding                                  | `latin1`, `utf-8`, `utf-16be`, `utf16-le`, `utf-8-bom` |
| `trim_trailing_whitespace` | Whether whitespace is removed from EOL                   | `true`, `false`                                        |
| `insert_final_newline`     | Whether a file should end in a newline                   | `true`, `false`                                        |
| `root`                     | Identify the root editorconfig (must be set in preamble) | `true`, `false`                                        |

### limited properties
| Property          | Definition                                  | Possible values |
| ----------------- | ------------------------------------------- | --------------- |
| `max_line_length` | Force hard line wrapping after n characters | *integer*, `off` |

For any property, a value of `unset` removes the effect of that property, even if it was set before.

# editorconfig in visual studio
- EditorConfig settings take precedence over global Visual Studio text editor settings.
- The formatting of existing code is not changed unless Code Cleanup is run (for all settings) or Format Document is run (for whitespace settings only).

## creating
Project > **Add New Item** > **editorconfig**
- editorconfig File (default) comes pre-populated with two items.
- editorconfig File (.NET) comes pre-populated with .NET code style rules.

## applying
EditorConfig files are searched for in the current directory and all parent directories until the root file is found or the root of the filesystem is reached.

To quickly find editorconfig files, use `dir .editorconfig /s`

## disable editorconfig
**Tools** > *Options* > **Text Editor** > uncheck **Follow project coding conventions**

# Code Style & Code Quality Rules
EditorConfig can also express code style and quality rules.
- [Code style language rules - .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/language-rules)
- [Code quality rules overview - .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/)

This format is only understood by Visual Studio while coding, not the compiler:  
`dotnet_style_readonly_field = true:suggestion`

This format is understood by the compiler at build time:  
`dotnet_diagnostic.ruleID.severity = severity-level`

## [Severity Levels](https://learn.microsoft.com/en-us/visualstudio/code-quality/use-roslyn-analyzers?view=vs-2022#configure-severity-levels)
| Severity (Solution Explorer) | Severity (EditorConfig file) | Build-time behavior                                                                Editor behavior                                                                        |
| ---------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Error                        | error                        | Violations appear as*Errors*in the Error List and in command-line build output, and cause builds to fail.                                                                 | Offending code is underlined with a red squiggle and marked by a small red box in the scroll bar.     |
| Warning                      | warning                      | Violations appear as*Warnings*in the Error List and in command-line build output, but don't cause builds to fail.                                                         | Offending code is underlined with a green squiggle and marked by a small green box in the scroll bar. |
| Info                         | suggestion                   | Violations appear as*Messages*in the Error List, and not at all in command-line build output.                                                                             | Offending code is underlined with a gray squiggle and marked by a small gray box in the scroll bar.   |
| Hidden                       | silent                       | Non-visible to user.                                                               Non-visible to user. The diagnostic is reported to the IDE diagnostic engine, however. |
| None                         | none                         | Suppressed completely.                                                             Suppressed completely.                                                                 |
| Default                      | default                      | Corresponds to the default severity of the rule. To determine what the default value for a rule is, look in the Properties window.                                        | Corresponds to the default severity of the rule.                                                      |

# sample editorconfig files
- Roslyn's editorconfig: [roslyn/.editorconfig at main · dotnet/roslyn (github.com)](https://github.com/dotnet/roslyn/blob/main/.editorconfig)
- .NET runtime's editorconfig: [runtime/.editorconfig at main · dotnet/runtime (github.com)](https://github.com/dotnet/runtime/blob/main/.editorconfig)

# suppressing editorconfig violations
`#pragma warning disable CAXXXX`

# analyzerconfig
[Configuration files for code analysis rules - .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/configuration-files#global-analyzerconfig)  
Like EditorConfig, but project-level configuration options.  
Use when you have project files outside the project folder.  

# see also
- [EditorConfig](https://editorconfig.org/)  
- [EditorConfig Specification — EditorConfig Specification 0.15.0 documentation (editorconfig-specification.readthedocs.io)](https://editorconfig-specification.readthedocs.io/)  
- [EditorConfig Properties · editorconfig/editorconfig Wiki (github.com)](https://github.com/editorconfig/editorconfig/wiki/EditorConfig-Properties) 
