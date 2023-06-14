---
title: notes > .net > winui 3 > winui 3
date: 2022-12-09T19:58:34-0700
draft: false
---
# [WinUI](https://www.microsoft.com/windows/apps/desktop)
Windows UI library — the native UI framework of Windows 10/11
- Build desktop applications with C# or C++
- Part of the Windows App SDK

# Overview
- UI is defined in XAML; logic is defined in C#
- Uses MVVM pattern via data binding between UI and UI logic

# Creating a WinUI Project
Visual Studio > *Project Type* > **WinUI** > **Blank App, Packaged (single project)** or **Blank App, Packaged with Windows Application Packaging Project** (two projects)

# Bootstrapper API
Set `<WindowsPackageType>None</WindowsPackageType>` project file property to cause auto-initializer to locate and load an appropriate Windows App SDK version.
