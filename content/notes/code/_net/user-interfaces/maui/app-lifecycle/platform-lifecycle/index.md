---
title: notes > code > .net > user interfaces > maui > app lifecycle > platform lifecycle
date: 2022-10-09T19:43:58-0600
draft: false
---

# Platform Lifecycle Events
Namespace: `Microsoft.Maui.LifecycleEvents`
- .NET MAUI uses delegates that are invoked in response to a platform lifecycle event being raised.
- You can create handlers for these delegates.

# [Android](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/app-lifecycle#android)
Each delegate has an identically named extension method used to register a handler for that delegate.

## Responding to Android Lifecycle Delegates
Call `ConfigureLifecycleEvents` method on `MauiAppBuilder` object in `CreateMauiApp` method of `MauiProgram` class:
```cs
using Microsoft.Maui.LifecycleEvents;

namespace PlatformLifecycleDemo 
{
    public static class MauiProgram 
    {
        public static MauiApp CreateMauiApp() 
        {
            var builder = MauiApp.CreateBuilder();
            builder
            .UseMauiApp<App>()
            .ConfigureLifecycleEvents(events => 
            {
                #if ANDROID
                events.AddAndroid(android => android
                .OnActivityResult((activity, requestCode, resultCode, data) => LogEvent("OnActivityResult", requestCode.ToString()))
                .OnStart((activity) => LogEvent("OnStart"))
                .OnCreate((activity, bundle) => LogEvent("OnCreate"))
                .OnBackPressed((activity) => LogEvent("OnBackPressed"))
                .OnStop((activity) => LogEvent("OnStop")));
                #endif

                static void LogEvent(string eventName, string type = null) 
                {
                    System.Diagnostics.Debug.WriteLine($"Lifecycle event: {eventName}{(type == null ? string.Empty : $" ({type})")}");
                }
            });

            return builder.Build();
        }
    }
}
```

# [iOS](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/app-lifecycle#ios)
Each delegate has an identically named extension method used to register a handler for that delegate.

## Responding to iOS Lifecycle Delegates
Call `ConfigureLifecycleEvents` method on `MauiAppBuilder` object in `CreateMauiApp` method of `MauiProgram` class. Then on the `ILifecycleBuilder` object, call `AddiOS` method and specify the `Action` that registeres handlers for the required delegates:
```cs
using Microsoft.Maui.LifecycleEvents;

namespace PlatformLifecycleDemo 
{
    public static class MauiProgram 
    {
        public static MauiApp CreateMauiApp() 
        {
            var builder = MauiApp.CreateBuilder();
            builder
            .UseMauiApp<App>()
            .ConfigureLifecycleEvents(events => 
            {
                #if IOS
                events.AddiOS(ios => ios
                .OnActivated((app) => LogEvent("OnActivated"))
                .OnResignActivation((app) => LogEvent("OnResignActivation"))
                .DidEnterBackground((app) => LogEvent("DidEnterBackground"))
                .WillTerminate((app) => LogEvent("WillTerminate")));
                #endif
                static void LogEvent(string eventName, string type = null) 
                {
                    System.Diagnostics.Debug.WriteLine($"Lifecycle event: {eventName}{(type == null ? string.Empty : $" ({type})")}");
                }
            });

            return builder.Build();
        }
    }
}
```
# [Windows](https://learn.microsoft.com/en-us/dotnet/maui/fundamentals/app-lifecycle#windows)
.NET MAUI exposes some native Windows messages as a lifecycle event via the `OnPlatformMessage` delegate. This delegate includes the `WindowsPlatformMessageEventArgs` object, which includes a `uint MessageId` property.  
- More information: [Window Messages (Get Started with Win32 and C++) - Win32 apps | Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/learnwin32/window-messages) and [Window Notifications - Win32 apps | Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/winmsg/window-notifications)

## Responding to Windows Lifecycle Delegates
Call `ConfigureLifecycleEvents` method on `MauiAppBuilder` object in `CreateMauiApp` method of `MauiProgram` class. Then on the `ILifecycleBuilder` object, call `AddWindows` method and specify the `Action` that registers handlers for the required delegates:
```cs
using Microsoft.Maui.LifecycleEvents;

namespace PlatformLifecycleDemo 
{
    public static class MauiProgram 
    {
        public static MauiApp CreateMauiApp() 
        {
            var builder = MauiApp.CreateBuilder();
            builder
            .UseMauiApp<App>()
            .ConfigureLifecycleEvents(events => 
            {
                #if WINDOWS
                events.AddWindows(windows => windows
                .OnActivated((window, args) => LogEvent("OnActivated"))
                .OnClosed((window, args) => LogEvent("OnClosed"))
                .OnLaunched((window, args) => LogEvent("OnLaunched"))
                .OnLaunching((window, args) => LogEvent("OnLaunching"))
                .OnVisibilityChanged((window, args) => LogEvent("OnVisibilityChanged"))
                .OnPlatformMessage((window, args) => 
                {
                    if (args.MessageId == Convert.ToUInt32("0x02E0")) 
                    {
                        // DPI has changed
                    }
                }));
                #endif
                
                static void LogEvent(string eventName, string type = null) 
                {
                    System.Diagnostics.Debug.WriteLine($"Lifecycle event: {eventName}{(type == null ? string.Empty : $" ({type})")}");
                }
            });

            return builder.Build();
        }
    }
}
```

## Retrieving the Window Object
Platform code can retrieve the app's Window object:
```cs
using Microsoft.Maui.LifecycleEvents;

namespace PlatformLifecycleDemo 
{
    public static class MauiProgram 
    {
        public static MauiApp CreateMauiApp() 
        {
            var builder = MauiApp.CreateBuilder();
            builder
            .UseMauiApp<App>()
            .ConfigureLifecycleEvents(events => 
            {
                #if WINDOWS
                events.AddWindows(windows => windows
                .OnClosed((window, args) => 
                {
                    IWindow appWindow = window.GetWindow();
                }));
                
                #endif
            });

            return builder.Build();
        }
    }
}
```
