---
title: "w3c logging"
date: 2023-05-14T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Middleware that writes log files in the [W3C standard format](https://www.w3.org/TR/WD-logfile.html).

<o>Caution</o>: W3C logging can reduce the performance of an app, especially when logging request/response bodies.  
<r>Warning</r>: W3C logging can potentially log personally identifiable information.

# Enabling
Call `UseW3Logging`:  

`Program.cs`  
```cs
var app = builder.Build();

app.UseW3CLogging();

app.UseRouting();
```

# Configuration
Call `AddW3CLogging`:

`Program.cs`
```cs
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddW3CLogging(logging =>
{
    // Log all W3C fields
    logging.LoggingFields = W3CLoggingFields.All;

    logging.AdditionalRequestHeaders.Add("x-forwarded-for");
    logging.AdditionalRequestHeaders.Add("x-client-ssl-protocol");
    logging.FileSizeLimit = 5 * 1024 * 1024;
    logging.RetainedFileCountLimit = 2;
    logging.FileName = "MyLogFile";
    logging.LogDirectory = @"C:\logs";
    logging.FlushInterval = TimeSpan.FromSeconds(2);
});
```