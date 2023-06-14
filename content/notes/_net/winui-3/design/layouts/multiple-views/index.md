---
title: notes > .net > winui 3 > design > layouts > multiple views
date: 2023-01-02T20:53:42-0700
draft: false
---
# Overview
Multiple views allow independent parts of apps to be viewed in separate windows.  
When implemented, the taskbar shows each window separately.

## APIs
[Windows.UI.ViewManagement Namespace - Windows UWP applications | Microsoft Learn](https://learn.microsoft.com/en-us/uwp/api/windows.ui.viewmanagement)  
[Windows.UI.WindowManagement namespace (microsoft.com)](https://learn.microsoft.com/en-us/uwp/api/windows.ui.windowmanagement)  

# Windowing Hosts
## `CoreWindow` / `ApplicationView`
- A 1:1 pairing of a thread and a window the app uses to display content
- Main view is always hosted in `ApplicationView`; content in a secondary window can be hosted in an `ApplicationView` or `AppWindow`
- Not the preferred technique

## [AppWindow](https://learn.microsoft.com/en-us/windows/apps/design/layout/app-window)
- Preferred technique (Windows 10 1903+)
- Operates on the same UI thread it is created from
