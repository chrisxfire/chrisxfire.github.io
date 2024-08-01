---
title: code coverage tooling
date: 2023-10-22T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-code-coverage?tabs=windows)]  

Types of code coverage tools:
* DataCollectors — monitor test execution and collect information about test runs. Part of [VSTest](https://github.com/microsoft/vstest); built into Visual Studio.
* Report generators — use data collected by DataCollectors to generate (often HTML-formatted) reports.
  * [ReportGenerator](https://github.com/danielpalme/ReportGenerator)
* [Coverlet](https://github.com/coverlet-coverage/coverlet) — a cross-platform code-coverage tool for .NET. An alternative to VSTest.
  * xUnit integrates with Coverlet.
* [dotnet-coverage](https://learn.microsoft.com/en-us/dotnet/core/additional-tools/dotnet-coverage)