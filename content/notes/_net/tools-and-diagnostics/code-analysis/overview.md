---
title: overview
date: 2023-09-07T00:00:00-06:00
draft: false
weight: -1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/overview

Roslyn Analyzers inspect C#/VB code for style, quality, maintainability, design, and other issues.  They are made up of code analysis rules.  These rules work together with Visual Studio.

Code analysis rules consist of:
* *Code style* analysis rules 
  * Diagnostic ID prefix `IDExxxx
  * Built into Visual Studio and (since .NET 5) the .NET SDK 
  * Configured in text editor options or EditorConfig file
* *Code quality* analysis rules 
  * Diagnostic ID prefix `CAxxxx`
  * Included (since .NET 5) in .NET SDK
* External analyzers — StyleCop, Roslynator, XUnit Analyzers, Sonar Analyzer, etc

# Configuration
> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/configuration-options

Code analysis rules can be configured.

## Severity
Each code analysis rule (both code quality and code style) has a severity level:
| Solution Explorer | EditorConfig | Editor behavior          | Build behavior |
| ----------------- | ------------ | ------------------------ | -------------- |
| Error             | `error`      | Red squiggly underline   | Build fails    |
| Warning           | `warning`    | Green squiggly underline | Build warning  |
| Info              | `suggestion` | Grey squiggly underline  | Build messages |
| Hidden            | `silent`     | Non-visible              | N/A            |
| None              | `none`       | Completely suppressed    | Varies         |

Hidden (`silent`) means Visual Studio will still show a code fix if available. None (`none`) means Visual Studio will never show a code fix. 

Severity can be configured via an EditorConfig file where it takes precedence over rule sets (*deprecated*) and Solution Explorer.  

### Severity Scope
For a single analyzer rule:
* `dotnet_diagnostic.RULE_ID.severity=SEVERITY`  

<o>Note</o>: IDE code-style analyzer rules use a different syntax: `dotnet_style_NAME_OF_RULE=OPTION:SEVERITY`

For a category of analyzer rules: 
* `dotnet_analyzer_diagnostic.category-RULE_CATEGORY.severity=SEVERITY`
* [See here](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/categories) for all categories.

For all analyzer rules: 
* `dotnet_analyzer_diagnostic.severity=SEVERITY`

For multiple analyzer rules, precedence is *Individual rule by ID > Category > All analyzer rules*.

## Analysis Mode
Each project has an *analysis mode*. This mode determines the set of analysis rules that are enabled. It is configured with the `<AnalysisMode>` MSConfig property:
| Setting       | Description                                                                                                                                                      |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `None`        | All rules disabled                                                                                                                                               |
| `Default`     | The rules enabled in the `Default` mode are listed [here](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/overview?tabs=net-7#enabled-rules) |
|               |
| `Minimum`     | More aggressive than `Default`                                                                                                                                   |
| `Recommended` | More aggressive than `Minimum`                                                                                                                                   |
| `All`         | All rules enabled                                                                                                                                                |

In .NET 6+, you can enable a category of rules via the `<AnalysisModeCATEGORY>` MSBuild property.  [See here](https://learn.microsoft.com/en-us/dotnet/core/project-sdk/msbuild-props#analysismodecategory) for more information.

In .NET 6+, Analysis Mode can be replaced with Analysis Level. This is configured differently. [See here](https://learn.microsoft.com/en-us/dotnet/core/project-sdk/msbuild-props#analysislevel) for more information.

<o>Note</o>: `AnalysisMode` and `AnalysisLevel` take precedence over any configuration in `.editorconfig`.

## Excluding Generated Code
Automatically generated code files, like designer-generated files, can be excluded from code analysis.

> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code

## Configuration Files
> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/configuration-files
Code analysis rule configurations are stored in one of two configuration files:
1. EditorConfig files (file or folder-based configuration options)
2. Global AnalyzerConfig file (project-level configuration)

### EditorConfig
EditorConfig files apply to specific source files or folders. This example applies to all `.cs` files in the current folder, including subfolders:
```ini
[*.cs] # The section header determines what files these rules apply to
<option_name> = <option_value>
```

See [notes on EditorConfig]({{< ref "./editorconfig" >}}).

### AnalyzerConfig
> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/configuration-files#global-analyzerconfig

## Suppressing Warnings
Code analyzer warnings can be suppressed in several ways.

> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/suppress-warnings

# Code Quality Rules (`CAxxxx`)
These rules inspect code for security, performance, design and other issues. 

[See here] for a full list of rules(https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/quality-rules/#index-of-rules).

## Options
Code quality rules have options that can be configured besides severity.  
[See here](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/code-quality-rule-options#options) for a list of options.

To configure an option for all rules:  
* `dotnet_code_quality.OPTION_NAME=OPTION_VALUE`

To configure an option for a category of rules:  
* `dotnet_code-quality.RULE_CATEGORY.OPTION_NAME=OPTION_VALUE`

# Code Style Rules (`IDExxx`)
Code style rules consist of [language rules](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/language-rules), [formatting rules](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0055), and [naming rules](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/naming-rules).  These rules enable a consistent code style across a codebase. They can be defined in EditorConfig or in Visual Studio via **Options > Text Editor > C# > Code Style > General**.

[See here] for a full list of rules(https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/#index).

# Preventing Rule Updates
By default, code analysis rules are updated as you upgrade to newer versions of the .NET SDK. This behavior can be suppressed.

> Documentation: https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/overview?tabs=net-7#latest-updates