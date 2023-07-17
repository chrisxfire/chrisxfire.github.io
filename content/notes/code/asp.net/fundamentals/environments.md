---
title: notes > code > asp.net > fundamentals > environments
date: 2023-01-13T00:00:00-06:00
draft: false
weight: 1
---

# Overview
ASP.NET reads the following env vars to determine the environment:
- `DOTNET_ENVIRONMENT`
- `ASPNETCORE_ENVIRONMENT` — the default when `WebApplication.CreateBuilder` is used, which is part of the default template.  This will override `DOTNET_ENVIRONMENT`.
	
# `IHostEnvironment.EnvironmentName`
- The `launchSettings.json` file sets `ASPNETCORE_ENVIRONMENT` to `Development` on the local machine.
- Set to `Production` if `ASPNETCORE_ENVIRONMENT` and `DOTNET_ENVIRONMENT` have not been set.

# Setting Environment From Command Line
`dotnet run --environment Production`

# `launchSettings.json`
Set in `Properties/launchSettings.json` and defines launch profiles.
- Is used only on the local development machine
- Is not deployed
- Contains profile settings

`launchSettings.json`
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
    "EnvironmentsSample": { // A profile
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

# Selecting Profiles From Command Line
`dotnet run --launch-profile "profile-name"`
