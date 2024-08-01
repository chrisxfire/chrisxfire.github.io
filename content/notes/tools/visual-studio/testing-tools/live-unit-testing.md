---
title: live unit testing
date: 2023-09-27T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/visualstudio/test/live-unit-testing-intro?view=vs-2022)]  
<g>Availability</g>: Visual Studio 2022 Enterprise Edition 

Live Unit Testing executes unit tests automatically and in real time as code changes are made. 
It works with unit tests created in test projects (see [Notes on Unit Testing](../../../../../notes/_net/testing/unit-testing))

# Enabling
Pre-requisites:
1. A .NET Core or .NET Framework project
2. A Unit Test project

To enable live unit testing: **Test** > **Live Unit Testing** > **Start**  
Visual studio will then rebuild the project and start Live Unit Test, which automatically runs all tests.

# Configuration
The first time Live Unit Testing is started, a setup wizard runs. This setup wizard can be run again at
**Test** > **Live Unit Testing** > **Configure Live Unit Testing for Solution**.

The following aspects can be configured:
* *Repository root* — The folder that will be copied to create the workspace (a copy of the original repository). 
This should be the root folder of the repository (usually where the solution file sits).
* *Workspace root* — The folder where Live Unit Testing keeps a clone of the repository. Defaults to user home directory.

The next page of the wizard is for the *lutignore* file.

## Lutignore
The *lutignore* file is a Live Unit Test ignore file that uses the same format as *gitignore*. It should include rules that
match the folders and files generated during build so they are not copied into the workspace.

## More Configuration
See **Test** > **Live Unit Testing** > **Options**.

# Customizing Builds for Live Unit Testing
Builds can be customized with overrides and test dependencies. See [this documentation](https://learn.microsoft.com/en-us/visualstudio/test/live-unit-testing?view=vs-2022#customize-your-build-for-live-unit-testing).
