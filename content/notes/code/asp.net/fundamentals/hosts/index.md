---
title: notes > code > asp.net > fundamentals > hosts
date: 2023-01-08T00:00:00-06:00
draft: false
---

# Hosts
<!-- TODO: hyperlink -->
See also:  Generic Host  
ASP.NET now uses a Generic Host.  The Web Host is provided only for backward compatibility.  
ASP.NET creates a `WebApplicationBuilder` and a `WebApplication` which eliminates the need for a Startup class.

The host encapsulates DI, Logging, Configuration, and IHostedService implementations.

# Create a Host with an IHostedService Implementation
## `CreateDefaultBuilder`
```csharp
await Host.CreateDefaultBuilder(args)
    .ConfigureServices(services =>
    {
        services.AddHostedService<SampleHostedService>();
    })
    .Build()
    .RunAsync();
```
CreateDefaultBuilder:
- Sets content root to `GetCurrentDirectory`
- Loads host configuration from env vars (prefixed with `DOTNET_`) then command line args
- Loads app configuration (`appsettings.json` —> `appsettings.{Enviornment}.json` —> User secrets (in `Development` environment) —> Env vars —> command line args)
- Adds logging providers:  `Console`, `Debug`, `EventSource`, `EventLog` (Windows only)
- Enables scope validation and dependency validation if environment == `Development`

## `ConfigureWebHostDefaults`
For an HTTP workload, call `ConfigureWebHostDefaults` instead of `ConfigureServices`:
```cs
await Host.CreateDefaultBuilder(args)
    .ConfigureWebHostDefaults(webBuilder =>
    {
        webBuilder.UseStartup<Startup>();
    })
    .Build()
    .RunAsync();
```
ConfigureWebHostDefaults:
- Loads host configuration from env vars (prefixed with `ASPNETCORE_`) 
- Sets Kestrel as the web server and configures it
- Adds Host Filtering middleware
- Adds Forwarded Headers middleware if `ASPNETCORE_FORWARDEDHEADERS_ENALED` == true
- Enables IIS integration

# IHostEnvironment
Inject `IHostEnvironment` into a class to get information about `ApplicationName`, `EnvironmentName`, and `ContentRootPath.`

Web apps implement `IWebHostEnvironment` which inherits `IHostEnvironment` and adds the `WebRootPath.`

# Host Configuration
Host configuration is for the properties of `IHostEnvironment.`
Available from `HostBuliderContext.Configuration` inside `ConfigureAppConfiguration` method.
- After `ConfigureAppConfiguration` method, `HostBuliderContext.Configuration` is set to the app configuration.

Call `ConfigureHostConfiguration` on `IHostBuilder`:
```cs
Host.CreateDefaultBuilder(args)
    .ConfigureHostConfiguration(hostConfig =>
    {
        hostConfig.SetBasePath(Directory.GetCurrentDirectory());
        hostConfig.AddJsonFile("hostsettings.json", optional: true);
        hostConfig.AddEnvironmentVariables(prefix: "PREFIX_");
        hostConfig.AddCommandLine(args);
    });
```
# App Configuration
Call `ConfigureAppConfiguration` on `IHostBuilder.`
Available at `HostBuilderContext.Configuration` and as a service from DI.

# Host Settings for All App Types
All of these settings can be set in env vars with `DOTNET_` or `ASPNETCORE_` prefixes:
| Key | Default | Env  | Alternate way to set |
|-----|---------|------|----------------------|
| `applicationName` (string) | Name of app assembly | `PREFIX_APPLICATIONNAME` | Env var |
| `contentRoot` (string) | Folder of app assembly | `PREFIX_CONTENTROOT` | `UseContentRoot` on `IHostBuilder` |
| `environment` (string) | Production | `PREFIX_ENVIRONMENT` | `UseEnvironment` <br> Can be any value; `Development` and `Staging` are common. |
| `shutdownTimeoutSeconds` (int) | 5 seconds | `PREFIX_SHUTDOWNTIMEOUTSECONDS` | configure `HostOptions` <br> Sets timeout for `StopAsync` |
| `hostBuilder:reloadConfigOnChange` (bool) | true | `PREFIX_hostBuilder:reloadConfigOnChange` | EnvVar |

# Host Settings for HTTP Workloads Only
Set via env vars with `DOTNET_` or `ASPNETCORE_` prefixes or extension methods on `IWebHostBuilder`:  

```cs
Host.CreateDefaultBuilder(args)
    .ConfigureWebHostDefaults(webBuilder =>
    {
        // ...
    });
```

| Key | Default | Env Var | Alternate way to set |
|-----|---------|---------|----------------------|
| `captureStartupErrors` (bool)<br>If `false`, errors during startup result in host exit| false<br>(unless running as Kestrel behind IIS) | `PREFIX_CAPTURESTARTUPERRORS` | `webBuilder.CaptureStartupErrors();` |
| `detailedErrors` (bool)<br>Capture detailed errors<br>Also enabled if environment == `Development` | `false` | `PREFIX_DETAILEDERRORS` | `webBuilder.UseSetting(WebHostDefaults.DetailedErrors Key, "true");` |
| `hostingStartupAssemblies` (string)<br>Semicolon-delimited string of startup assemblies to load on startup | (empty) | `PREFIX_HOSTINGSTARTUP`<br>`ASSEMBLIES` | `webBuilder.UseSetting(WebHostDefaults.HostingStartupAssembliesKey, "assembly1;assembly2");` |
| `hostingStartupExcludeAssemblies` (string) | (empty) | `PREFIX_HOSTING`<br>`STARTUPEXCLUDEASSEMBLIES` | `webBuilder.UseSetting(WebHostDefaults.HostingStartupExcludeAssembliesKey "assembly1;assembly2");` |
| `https_port` (string) | (empty) | `PREFIX_HTTPS_PORT` | `webBuilder.UseSetting("https_port", "8080");` |
| `preferHostingUrls` (bool)<br>Listen on URLs configured with `IServer`  | `true` | `PREFIX_PREFERHOSTINGURLs` | `webBuilder.PreferHostingUrls(true);` |
| `preventHostingStartup` (bool) | `false` | `PREFIX_PREVENTHOSTINGSTARTUP` | `webBuilder.UseSetting(WebHostDefaults.PreventHostingStartupKey, "true");` |
| `suppressStatusMessages` (bool)<br>Suppress hosting startup status messages. | `false` | `PREFIX_SUPRESSSTATUSMESSAGES` | `webBuilder.UseSetting(WebHostDefaults.SuppressStatusMessagesKey, "true");` |
| `urls` (string)<br>A list of IP addresses or host addresses with ports and<br>protocols that the server should listen on for requests. | string | `PREFIX_URLS` | `webBuilder.UseUrls("https://*:5000;http://localhost:5001;…");` |
| `webroot` (string)<br>The relative path to the app's static assets | `wwwroot` | `PREFIX_WEBROOT` | `webBuilder.UseWebRoot("public");` |


# Manage the Host Lifetime
Call these methods on `IHost`:
- `Run` — run the app and block the calling thread until host is shut down.
- `RunAsync` — run the app and return a Task that completes when cancellation token or shutdown is triggered.
- `RunConsoleAsync` — enable console support and waits for Ctrl + C / SIGINT or SIGTERM to shut down.
- `Start` — start the host synchronously.
- `StartAsync` — start the host and return a Task
 - `WaitForStartAsync` is called at the start of StartAsync.  Use to delay startup until signaled by an external event.
- `StopAsync` — stop the host within the provided timeout.
- `WaitForShutdown` — blocks the calling thread until shutdown is triggered.
- `WaitForShutdownAsync` — returns a Task that completes when shutdown is triggered and calls StopAsync.
