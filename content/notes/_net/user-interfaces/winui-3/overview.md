---
title: overview
date: 2022-12-09T19:58:34-0700
draft: false
weight: -1
---

# [WinUI](https://learn.microsoft.com/en-us/windows/apps/desktop/)
Windows UI library — the native UI framework of Windows 10/11
- Build desktop applications with C# or C++
- Part of the Windows App SDK

# abstract
- UI is defined in XAML; logic is defined in C#
- Uses MVVM pattern via data binding between UI and UI logic

# creating a winui project
Visual Studio > *Project Type* > **WinUI** > **Blank App, Packaged (single project)** or **Blank App, Packaged with Windows Application Packaging Project** (two projects)

# bootstrapper api
Set `<WindowsPackageType>None</WindowsPackageType>` project file property to cause auto-initializer to locate and load an appropriate Windows App SDK version.
