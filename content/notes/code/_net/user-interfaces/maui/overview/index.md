---
title: notes > code > .net > user interfaces > maui > overview
date: 2022-09-17T17:04:25-0600
draft: false
---

# Overview
- Multi-platform Application User Interface.
- Generates native code for the target device.
- MAUI leverages WinUI 3 (via Windows App SDK) for Windows apps.
- Documentation: https://learn.microsoft.com/en-us/dotnet/maui/
- Documentation: https://dotnet.microsoft.com/apps/maui

<img src="overview-1.png" style="width:6.625in;height:2.91667in" />
 
# Cross-Platform
- Each supported platform (iOS, Android, macOS, Windows) has its own set of APIs.
- There are also cross-platform APIs (phone dialer, device info, file system, geolocation, etc) that can be used which covers all platforms.
- .NET for iOS — AOT compilation to produce an ARM binary (.app)
- .NET for Android — JIT, AOT, Hybrid options (.apk)
- .NET for macOS — leverages Mac Catalyst
- .NET for Windows — leverages WinUI 3

# Web
Blazor Hybrid (Blazor + .NET MAUI) — Share Razor components with a .NET MAUI App.  
<img src="overview-2.png" style="width:6.56667in;height:2.5in" />
 
# UI
In MAUI, UI's can be created in XAML or C#.

# Handlers
MAUI uses handlers to carry out UI operations:  
<img src="overview-3.png" style="width:5.95833in;height:3.56667in" />
