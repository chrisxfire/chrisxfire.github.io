---
title: static files
date: 2023-01-11T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0)  

Static files are stored in the web root directory `CONTENT_ROOT/wwwroot`.  Change with `UseWebRoot.`  Serve with `UseStaticFiles.`

## Serve Static Files in the Web Root
Static files are accessible via a path relative to the web root.  If you create `wwwroot/images/` and add `SomeImage.jpg`, 
- access via URL at `https://hostname/images/SomeImage.jpg`
- and via markup:  `<img src="~/images/MyImage.jpg" class="img" alt="My image" />`

## Serve Static Files Outside of the Web Root
Use `UseStaticFiles` and pass `StaticFileOptions`:
```cs
app.UseStaticFiles(new StaticFileOptions 
{ 
	FileProvider = new PhysicalFileProvider(Path.Combine(builder.Environment.ContentRootPath, "SomeDirectory")), // The new static files directory
	RequestPath = "/StaticFiles" // The static files directory, SomeDirectory, is exposed via the /StaticFiles URI segment.
});
```
Static files can be reached
- via URL at `https://hostname/StaticFiles/…`
- via markup:  `<img src="~/StaticFiles/images/red-rose.jpg" class="img" alt="A red rose" />`
	
## Set HTTP Response Headers
Use `StaticFileOptions`:
```cs
// Make static files publicly available in the local cache for one week via the Cache-Control header:
var cacheMaxAgeOneWeek = (60 * 60 * 24 * 7).ToString(); 
app.UseStaticFiles(new StaticFileOptions
{
    OnPrepareResponse = ctx =>
    {
        ctx.Context.Response.Headers.Append("Cache-Control", $"public, max-age={cacheMaxAgeOneWeek}");
    }
});
```
# Static file authorization [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#static-file-authorization)]  

# Directory browsing [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#directory-browsing)]  

# Serve default documents [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#serve-default-documents)]  

# `FileExtensionContentTypeProvider` [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#fileextensioncontenttypeprovider)]  

# Non-standard content types [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#non-standard-content-types)]  

# Serve files from multiple locations [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#serve-files-from-multiple-locations)]  

# Serve files outside `wwwroot` by updating `IWebHostEnvironment.WebRootPath` [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0#serve-files-outside-wwwroot-by-updating-iwebhostenvironmentwebrootpath)]  
