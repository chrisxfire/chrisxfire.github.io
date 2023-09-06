---
title: code analysis
date: 2023-09-06T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/visualstudio/code-quality/roslyn-analyzers-overview?view=vs-2022
> Documentation: https://learn.microsoft.com/en-us/visualstudio/code-quality/use-roslyn-analyzers?view=vs-2022

Roslyn Analyzers inspect C#/VB code for style, quality, maintainability, design, and other issues.  They are made up of analyzer rules called *diagnostics*.

Analyzers consist of:
* *Code style* analyzers — Diagnostic ID prefix `IDExxxx`; built into Visual Studio and (since .NET 5) the .NET SDK; configured in text editor options or EditorConfig file
* *Code quality* analyzers — Diagnostic ID prefix `CAxxxx`; included (since .NET 5) in .NET SDK
* External analyzers — StyleCop, Roslynator, XUnit Analyzers, Sonar Analyzer, etc

# Severity
Each analyzer has a severity level:
| Solution Explorer | EditorConfig | Editor behavior          |
| ----------------- | ------------ | ------------------------ |
| Error             | `error`      | Red squiggly underline   |
| Warning           | `warning`    | Green squiggly underline |
| Info              | `suggestion` | Grey squiggly underline  |
| Hidden            | `silent`     | Non-visible              |
| None              | `none`       | Completely suppressed    |

Hidden (`silent`) means Visual Studio will still show a code fix if available. None (none) means Visual Studio will never show a code fix. 

## Configuring Severity
Severity can be configured via an EditorConfig file where it takes precedence over rule sets (*deprecated*) and Solution Explorer.  

For a single analyzer rule:
* In an EditorConfig file, use this syntax: `dotnet_diagnostic.RULE_ID.severity=SEVERITY`  

<o>Note</o>: IDE code-style analyzer rules use a different syntax: `dotnet_style_NAME_OF_RULE=OPTION:SEVERITY`

For multiple analyzer rules:
* For a category of analyzer rules: `dotnet_analyzer_diagnostic.category-RULE_CATEGORY.severity=SEVERITY`
* For all analyzer rules: `dotnet_analyzer_diagnostic.severity=SEVERITY`

For multiple analyzer rules, precedence is Individual rule by ID > Category > All analyzer rules.