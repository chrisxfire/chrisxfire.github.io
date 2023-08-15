---
title: making http requests
date: 2023-01-11T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-7.0

See [Problems with HttpClient]({{< ref "../../_net/web/http/ihttpclientfactory#problems-with-httpclient" >}})

# Via `IHttpClientFactory` 
Register `IHttpClientFactory` in the DI container:
```cs {hl_lines=3}
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHttpClient();
```

Inject an `IHttpClientFactory`:
```cs {hl_lines=[3,5]}
public class BasicModel : PageModel
{
    private readonly IHttpClientFactory _httpClientFactory;

    public BasicModel(IHttpClientFactory httpClientFactory) => _httpClientFactory = httpClientFactory;

    public IEnumerable<GitHubBranch>? GitHubBranches { get; set; }

    public async Task OnGet()
    {
        var httpRequestMessage = new HttpRequestMessage(
            HttpMethod.Get,
            "https://api.github.com/repos/_net/AspNetCore.Docs/branches")
        {
            Headers =
            {
                { HeaderNames.Accept, "application/vnd.github.v3+json" },
                { HeaderNames.UserAgent, "HttpRequestsSample" }
            }
        };

        var httpClient = _httpClientFactory.CreateClient();
        var httpResponseMessage = await httpClient.SendAsync(httpRequestMessage);

        if (httpResponseMessage.IsSuccessStatusCode)
        {
            using var contentStream = await httpResponseMessage.Content.ReadAsStreamAsync();
            
            GitHubBranches = await JsonSerializer.DeserializeAsync<IEnumerable<GitHubBranch>>(contentStream);
        }
    }
}
```
# Named clients
Use when app requires many distinct uses of `HttpClient`, or many `HttpClients` have different configurations.

## Creating
```cs
builder.Services.AddHttpClient("GitHub", httpClient =>
{
    httpClient.BaseAddress = new Uri("https://api.github.com/");

    // using Microsoft.Net.Http.Headers;
    // The GitHub API requires two headers.
    httpClient.DefaultRequestHeaders.Add(HeaderNames.Accept, "application/vnd.github.v3+json");
    httpClient.DefaultRequestHeaders.Add(HeaderNames.UserAgent, "HttpRequestsSample");
});
```

## Using
Each time `CreateClient` is called, a new instance of `HttpClient` is created and the configuration action is called:

```cs
public class NamedClientModel : PageModel
{
    private readonly IHttpClientFactory _httpClientFactory;
    public NamedClientModel(IHttpClientFactory httpClientFactory) => _httpClientFactory = httpClientFactory;
    public IEnumerable<GitHubBranch>? GitHubBranches { get; set; }

    public async Task OnGet()
    {
        var httpClient = _httpClientFactory.CreateClient("GitHub");
        var httpResponseMessage = await httpClient.GetAsync("repos/_net/AspNetCore.Docs/branches");

        if (httpResponseMessage.IsSuccessStatusCode)
        {
            using var contentStream = await httpResponseMessage.Content.ReadAsStreamAsync();
            
            GitHubBranches = await JsonSerializer.DeserializeAsync<IEnumerable<GitHubBranch>>(contentStream);
        }
    }
}
```

# Typed clients
Work like named clients without the need to use strings as keys.  Provides IntelliSense and compiler help.
Use for a single backend endpoint or to encapsulate logic dealing with an endpoint.
```cs
public class GitHubService
{
    private readonly HttpClient _httpClient;

    public GitHubService(HttpClient httpClient) // Typed clients accept an HttpClient in their constructor
    {
        _httpClient = httpClient;

        _httpClient.BaseAddress = new Uri("https://api.github.com/");

        // using Microsoft.Net.Http.Headers;
        // The GitHub API requires two headers.
        _httpClient.DefaultRequestHeaders.Add(HeaderNames.Accept, "application/vnd.github.v3+json");
        _httpClient.DefaultRequestHeaders.Add(HeaderNames.UserAgent, "HttpRequestsSample");
    }

    public async Task<IEnumerable<GitHubBranch>?> GetAspNetCoreDocsBranchesAsync() =>
        await _httpClient.GetFromJsonAsync<IEnumerable<GitHubBranch>>("repos/_net/AspNetCore.Docs/branches");
}
```
Instead of configuring in the typed client's constructor as above, configuration can be supplied during registration:
```cs
builder.Services.AddHttpClient<GitHubService>(httpClient =>
{
    httpClient.BaseAddress = new Uri("https://api.github.com/");
    // ...
});
```
Register the typed client with DI:
```cs
builder.Services.AddHttpClient<GitHubService>(); // Registered as a transient service
```
## Injecting and consuming
```cs
public class TypedClientModel : PageModel
{
    private readonly GitHubService _gitHubService;
    public TypedClientModel(GitHubService gitHubService) =>_gitHubService = gitHubService;
    public IEnumerable<GitHubBranch>? GitHubBranches { get; set; }

    public async Task OnGet()
    {
        try
        {
            GitHubBranches = await _gitHubService.GetAspNetCoreDocsBranchesAsync();
        }
        catch (HttpRequestException)
        {
            // ...
        }
    }
}
```
# Outgoing request middleware
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-7.0#outgoing-request-middleware

`IHttpClientFactory` enables you to build an outgoing request middleware.
In this pattern, handlers are defined for each named client.

## Creating a Delegating Handler
Two steps:  
1. Inherit `DelegatingHandler`  
2. Override `SendAsync`  
```cs
public class ValidateHeaderHandler : DelegatingHandler
{
    protected override async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken cancellationToken)
    {
        if (!request.Headers.Contains("X-API-KEY"))
            return new HttpResponseMessage(HttpStatusCode.BadRequest) =>
                Content = new StringContent("The API key header X-API-KEY is required.")

        return await base.SendAsync(request, cancellationToken);
    }
}
```

# `HttpClient` and `HttpMessageHandler` Lifetimes
With `IHttpClientFactory`, an `HttpMessageHandler` is created per named client.  The factory:
- Manages handler lifetimes
- Pools handler instances (allowing for it to be reused if not expired)
- Tracks and disposes resources used by `HttpClient` instances

The default handler lifetime is two minutes.  To override, for each named client:
```cs
builder.Services.AddHttpClient("HandlerLifetime").SetHandlerLifetime(TimeSpan.FromMinutes(5));

Configuring HttpMessageHandler
Use the ConfigurePrimaryHttpMessageHandler extension method:
builder.Services.AddHttpClient("ConfiguredHttpMessageHandler")
    .ConfigurePrimaryHttpMessageHandler(() => new HttpClientHandler
    {
        AllowAutoRedirect = true,
        UseDefaultCredentials = true
    });
```
## Cookies
The pooled `HttpMessageHandler` instances results in `CookieContainer` objects being shared.
For apps that require cookies, either:
1. Disable automatic cookie handling
2. Avoid using `IHttpClientFactory`

To disable automatic cookie handling:
```cs
builder.Services.AddHttpClient("NoAutomaticCookies")
			 .ConfigurePrimaryHttpMessageHandler(() => new HttpClientHandler { UseCookies = false });
```
# Logging
Clients created with `IHttpClientFactory` log messages for all requests.

## Header Propagation Middleware
This middleware propagates HTTP headers from incoming requests to the outgoing HttpClient requests.

To use:
1. Install `Microsoft.AspNetCore.HeaderPropagation` package
2. Configure `HttpClient` and the middleware pipeline:
```cs
// Add services to the container.
builder.Services.AddControllers();

builder.Services.AddHttpClient("PropagateHeaders").AddHeaderPropagation();

builder.Services.AddHeaderPropagation(options => { options.Headers.Add("X-TraceId"); });

var app = builder.Build();

// Configure the HTTP request pipeline.
app.UseHttpsRedirection();
app.UseHeaderPropagation();
app.MapControllers();
```

# From PluralSight
## Via `HttpClient` (From Pluralsight/ASP.NET Core 6 Blazor Fundamentals)
### Configuring
`Program.cs`
```cs
builder.Services.AddScoped(sp => 
    new HttpClient() 
    {
        BaseAddress = new Uri("http://*some-api-endpoint*")
    });
```
### Using
`SomeComponent.razor.cs`
```cs
// In a Razor component, you must use the [Inject] attribute instead of the constructor dependency injection approach:
[Inject]
public HttpClient HttpClient { get; set; }
// ...
protected override async Task OnInitializedAsync()
{
    Employees = await Httpclient.GetFromJsonAsync<Employee[]>("api/employee");
}
```

## Via `IHttpClientFactory` (From Pluralsight/ASP.NET Core 6 Blazor Fundamentals)
### Configuring
```posh
dotnet add package microsoft.extensions.http
```

`Program.cs`
```cs
// the AddHttpClient extension method is what brings in support for IHttpClientFactory
builder.Services.AddHttpClient<IEmployeeDataService, EmployeeDataService>(client => 
    client.BaseAddress = new Uri("https://localhost:44340/"));
```

### Using
`EmployeeDataService.cs`
```cs
public class EmployeeDataService : IEmployeeDataService
{
    private readonly HttpClient _httpClient;

    public EmployeeDataService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }
}
```