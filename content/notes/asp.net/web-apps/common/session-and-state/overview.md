---
title: overview
date: 2023-03-24T00:00:00-07:00
draft: false
weight: -1
---

# cookies
Cookies store data across requests.

Key points:
- The most durable form of persistence on the client
- Usually less than 4096 bytes
- Must be validated by the app
- [General Data Protection Regulation (GDPR) support in ASP.NET Core (microsoft.com)](https://learn.microsoft.com/en-us/aspnet/core/security/gdpr?view=aspnetcore-7.0)

# session state
Storage of user data while the user browses a web app.
- Backed by a cache (ephemeral)
- Critical user data should be stored in database and cached only as a performance optimization

Works by:
- Providing a cookie to the client that contains a session ID
- Session cookie is sent to the app w/each request and used by the app to fetch session data

Key points:
- Session cookie is specific to the browser
- Session cookie is deleted when the browser session expires or when `ISession.Clear` is called
- Expiration:
	- App retains session for 20 minutes (default) after last request
	- If client sent a cookie for an expired session, a new session is created w/same session cookie
- Empty sessions are not retained
- The session cooke is encrypted via `IDataProtector`
- Do not store sensitve data in session state

## configuring session state
Enable session middleware in `Program.cs`:
- Include an `IDistributedCache` memory cache ([Distributed caching in ASP.NET Core (microsoft.com)](https://learn.microsoft.com/en-us/aspnet/core/performance/caching/distributed?view=aspnetcore-7.0))
- Include a call to `AddSession` and `UseSession`

Example  
`Program.cs`
```cs
// …
builder.Services.AddDistributedMemoryCache();

builder.Services.AddSession(options =>
{
    options.IdleTimeout = TimeSpan.FromSeconds(10); // This is arbitrarily short
    options.Cookie.HttpOnly = true;
    options.Cookie.IsEssential = true;
});
// …
app.UseSession(); // AFTER UseRouting and BEFORE MapRazorPages and MapDefaultControllerRoute
// …
```

A new session (with a new session cookie) cannot be created after the app has started writing to the response stream.

## loading session state
Call `ISession.LoadAsync` to load session records from the underlying `IDistributedCache`.  
- If this call is not made before calling `TryGetValue`, `Set`, or `Remove` methods, it will be loaded synchronously.

## session options
Use `SessionOptions` to override session defaults:  
```cs
builder.Services.AddSession(options =>
{
    options.Cookie.Name = ".AdventureWorks.Session";
        // How long a session can be idle before its contents are abandoned in server's cache
    options.IdleTimeout = TimeSpan.FromSeconds(10); 
    options.Cookie.IsEssential = true;
});
```

## set and get session values
Session state is accessed via `HttpContext.Session` (an `ISession` implementation).  
`ISession` has extension methods in `Microsoft.AspNetCore.Http`.

Getting a Session Value — Razor Pages
```html
@page
@using Microsoft.AspNetCore.Http
@model IndexModel
<!-- ... -->
Name: @HttpContext.Session.GetString(IndexModel.SessionKeyName)
```

Getting a Session Value — MVC
```cs
public class IndexModel : PageModel
{
    public const string SessionKeyName = "_Name";
    public const string SessionKeyAge = "_Age";

    private readonly ILogger<IndexModel> _logger;

    public IndexModel(ILogger<IndexModel> logger) { _logger = logger; }

    public void OnGet()
    {
        if (string.IsNullOrEmpty(HttpContext.Session.GetString(SessionKeyName)))
        {
            HttpContext.Session.SetString(SessionKeyName, "The Doctor");
            HttpContext.Session.SetInt32(SessionKeyAge, 73);
        }
        var name = HttpContext.Session.GetString(SessionKeyName);
        var age = HttpContext.Session.GetInt32(SessionKeyAge).ToString();

        _logger.LogInformation("Session Name: {Name} and Age: {Age}", name, age);
    }
}
```

## serialization
Session data must be serialized to enable a distributed cache scenario.  
`ISession` extension methods (in `Web.Extensions`) can serialize strings and integers.  
Complex types require another mechanism, such as JSON.

Example — Serializing:
```cs
public static class SessionExtensions
{
    public static void Set<T>(this ISession session, string key, T value)
    {
        session.SetString(key, JsonSerializer.Serialize(value));
    }

    public static T? Get<T>(this ISession session, string key)
    {
        var value = session.GetString(key);
        return value == null ? default : JsonSerializer.Deserialize<T>(value);
    }
}
```

Example — Get & Set a serializable object via SessionExtensions
```cs
using Microsoft.AspNetCore.Mvc.RazorPages;
using Web.Extensions;    // SessionExtensions

namespace SessionSample.Pages
{
    public class Index6Model : PageModel
    {
        const string SessionKeyTime = "_Time";
        public string? SessionInfo_SessionTime { get; private set; }
        private readonly ILogger<Index6Model> _logger;

        public Index6Model(ILogger<Index6Model> logger)
        {
            _logger = logger;
        }

        public void OnGet()
        {
            var currentTime = DateTime.Now;

            // Requires SessionExtensions from sample.
            if (HttpContext.Session.Get<DateTime>(SessionKeyTime) == default)
                HttpContext.Session.Set<DateTime>(SessionKeyTime, currentTime);
            
            _logger.LogInformation("Current Time: {Time}", currentTime);
            _logger.LogInformation("Session Time: {Time}", HttpContext.Session.Get<DateTime>(SessionKeyTime));

        }
    }
}
```

# tempdata
A property that stores data until the next request.  
Available in both Razor Pages and MVC.

## example
A page that creates a customer:
```cs
public class CreateModel : PageModel
{
    private readonly RazorPagesContactsContext _context;

    public CreateModel(RazorPagesContactsContext context) { _context = context;     }

    public IActionResult OnGet() { return Page(); }

    [TempData]
    public string Message { get; set; }

    [BindProperty]
    public Customer Customer { get; set; }

    public async Task<IActionResult> OnPostAsync()
    {
        if (!ModelState.IsValid)
            return Page();

        _context.Customer.Add(Customer);
        await _context.SaveChangesAsync();
        Message = $"Customer {Customer.Name} added";

        return RedirectToPage("./IndexPeek");
    }
}
```

A page that displays the TempData message:
```html
@page
@model IndexModel

<h1>Peek Contacts</h1>

@{
    if (TempData.Peek("Message") != null)
        <h3>Message: @TempData.Peek("Message")</h3>
}
<!-- ... -->
```

At the end of this request, `TempData["Message"]` is NOT deleted because `Peek` is used.  
Similarly, `Keep` can be used to also persist the data without peeking it.  
If TempData was simply viewed via `TempData["Message"]`, it would have been deleted.

## tempdata providers
There is a cookie `TempData` provider and session Tem`pData provider. The cookie `TempData` provider (the default) uses its own cookie provider. It is encrypted, encoded, and chunked. It is not compressed—compressing encrypted data can lead to security vulnerabilities.

### choosing a provider
Use the cookie-based `TempData` provider is if:
- the app uses `TempData` sparingly or for data amounts <= 500 bytes
- the app runs on a server farm

Use the session-based `TempData` provider if:
- the app already uses session state, or
- the app uses `TempData` frequently or for data amounts > 500 bytes

To use the session `TempData` provider:
```cs
builder.Services.AddRazorPages()
                .AddSessionStateTempDataProvider();
```
or
```cs
builder.Services.AddControllersWithViews()
                .AddSessionStateTempDataProvider();
```

# HttpContext.Items
`HttpContext.Items` is a collection used to store data while processing a single request.  The collection is emptied after the request is processed.  

Example
```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

ILogger logger = app.Logger;

app.Use(async (context, next) =>
{
    // context.Items["isVerified"] is null
    logger.LogInformation($"Before setting: Verified: {context.Items["isVerified"]}");
    context.Items["isVerified"] = true;
    await next.Invoke();
});

app.Use(async (context, next) =>
{
    // context.Items["isVerified"] is true
    logger.LogInformation($"Next: Verified: {context.Items["isVerified"]}");
    await next.Invoke();
});

app.MapGet("/", async context => { await context.Response.WriteAsync($"Verified: {context.Items["isVerified"]}"); });

app.Run();
```

Use an object as the item key to avoid a key collision.  This is mostly used for middleware that's shared between apps:
```cs
public class HttpContextItemsMiddleware
{
    private readonly RequestDelegate _next;
    public static readonly object HttpContextItemsMiddlewareKey = new();

    public HttpContextItemsMiddleware(RequestDelegate next) => _next = next;

    public async Task Invoke(HttpContext httpContext)
    {
        httpContext.Items[HttpContextItemsMiddlewareKey] = "K-9";
        await _next(httpContext);
    }
}

public static class HttpContextItemsMiddlewareExtensions
{
    public static IApplicationBuilder 
        UseHttpContextItemsMiddleware(this IApplicationBuilder app) =>
            return app.UseMiddleware<HttpContextItemsMiddleware>();
}
```

# other mechanisms
Query Strings — Data can be passed from one request to another by adding it to the next request's query string.  This has risks.  
Hidden Fields — Data can be saved in hidden form fields and posted back on the next request.  This has risks.  
Caching — Data can be cached for responses or application-wide.  

