---
title: environments
date: 2023-01-13T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/environments?view=aspnetcore-7.0)]  

ASP.NET reads the following environment variables to determine the environment:
1. `DOTNET_ENVIRONMENT`
2. `ASPNETCORE_ENVIRONMENT`

For `WebApplicationBuilder` (the default), `DOTNET_ENVIRONMENT` has precedence.  
For `WebHost` (`ConfigureWebHostDefaults`, `CreateDefaultBuilder`), `ASPNETCORE_ENVIRONMENT` has precedence.  
	
# `IHostEnvironment.EnvironmentName`
- The `launchSettings.json` file sets `ASPNETCORE_ENVIRONMENT` to `Development` on the local machine.
- Set to `Production` if `ASPNETCORE_ENVIRONMENT` and `DOTNET_ENVIRONMENT` have not been set.

# Setting Environment From Command Line
`dotnet run --environment Production`

# Development Environment
## `launchSettings.json`
The environment for local machine development can be set in `Properties/launchSettings.json`.
- Is used only on the local development machine
- Is not deployed
- Contains profile settings
- Environment values set in this file override values in the system environment

```json
{
  "iisSettings": {
    "windowsAuthentication": false,
    "anonymousAuthentication": true,
    "iisExpress": {
      "applicationUrl": "http://localhost:59481",
      "sslPort": 44308
    }
  },
  "profiles": {
    "EnvironmentsSample": { // A profile; since this one is listed first, it is used by default
      "commandName": "Project", // If command name is "Project", Kestrel is used as web server
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "https://localhost:7152;http://localhost:5105",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "IIS Express": { // Another profile
      "commandName": "IISExpress", // IISExpress is used as web server
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

## Selecting Profiles From Command Line
`dotnet run --launch-profile "profile-name"`
* <o>Note</o>: this approach *only* supports Kestrel profiles

# Production Environment
Common settings for production environment:
* Caching
* Client-side resources bundled, minified, and potentially served from CDN
* Diagnostic error pages disabled
* Friendly error pages enabled
* Production logging and monitoring

<o>Note</o>: If the environment is not set, *it defaults to production*.

# Set Environment with VS Code
The `commandName` property specifies the web server to launch: `IISExpress`, `IIS` (no web server launched; expects IIS to be available), or `Project`.

In Visual Studio Code, the environment variables can be set in `.vscode/launch.json`:
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": ".NET Core Launch (web)",
            "type": "coreclr",
            // Configuration omitted for brevity.
            "env": {
                "ASPNETCORE_ENVIRONMENT": "Development",
                "ASPNETCORE_URLS": "https://localhost:5001",
                "ASPNETCORE_DETAILEDERRORS": "1",
                "ASPNETCORE_SHUTDOWNTIMEOUTSECONDS": "3"
            },
            // Configuration omitted for brevity.
          }
```

# Set Environment with Environment Variables
For the current session:  
```powershell
$Env:ASPNETCORE_ENVIRONMENT = "Staging"
dotnet run --no-launch-profile # Must use no launch profile since launchSettings.json overrides environment variables
```

For all sessions globally:  
```powershell
[Environment]::SetEnvironmentVariable("ASPNETCORE_ENVIRONMENT", "Staging", "Machine")
dotnet run --no-launch-profile # Must use no launch profile since launchSettings.json overrides environment variables
```

# Set Environment in Code
```cs
var builder = WebApplication.CreateBuilder(new WebApplicationOptions
{
    EnvironmentName = Environments.Staging
}); 
// ...
```