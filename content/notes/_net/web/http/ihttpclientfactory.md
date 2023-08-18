---
title: ihttpclientfactory
date: 2022-07-22T09:36:06-0600
draft: false
weight: 1
---

# Problems with HttpClient
- `HttpClient` implements `IDisposable`, but when the object gets disposed of, the underlying socket is not immediately released. This can lead to [socket exhaustion](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).
- When using a shared instances of `HttpClient` in long-running processes, the if instantiated as a singleton or static object, `HttpClient` will fail to [handle DNS changes](https://github.com/_net/runtime/issues/18348).

# Overview
`IHttpClientFactory` offers these benefits:
- Supports DI. Injected `HttpClient` instances are Scoped.
- A central location for naming and configuring `HttpClient` objects.
- Also implements `IHttpMessageHandlerFactory`.  Manages the caching and lifetime of the underlying `HttpClientHandler` instances.
- Works with `Polly`-based middleware.
- Documentation: https://learn.microsoft.com/en-us/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests?source=recommendations
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-7.0

# Requirements
```powershell
dotnet add package Microsoft.Extensions.Http
```

# Basic Usage
This is a good way to refactor an existing app. No impact on how HttpClient is used. Replace occurrences of where HttpClient instances are created with calls to `CreateClient`.  

`Program.cs`
```cs
// ...
builder.Services.AddHttpClient();
builder.Services.AddTransient<TodoService>();
// ...
using IHost host = builder.Build();
```

`TodoService.cs`
```cs
public class TodoService 
{
    private readonly IHttpClientFactory _httpClientFactory = null!;
    private readonly ILogger<TodoService> _logger = null!;

    public TodoService(
        IHttpClientFactory httpClientFactory,
        ILogger<TodoService> logger) => (_httpClientFactory, _logger) = (httpClientFactory, logger);

    public async Task<Todo[]> GetUserTodosAsync(int userId)
    {
        // Create the client
        using HttpClient client = _httpClientFactory.CreateClient();
        
        try
        {
            // Make HTTP GET request
            // Parse JSON response deserialize into Todo types
            Todo[]? todos = await client.GetFromJsonAsync<Todo[]>(
                $"https://jsonplaceholder.typicode.com/todos?userId={userId}",
                new JsonSerializerOptions(JsonSerializerDefaults.Web));

            return todos ?? Array.Empty<Todo>();
        }
        catch (Exception ex)
        {
            _logger.LogError("Error getting something fun to say: {Error}", ex);
        }

        return Array.Empty<Todo>();
}
```

# Named Clients
In the *named client* approach, `IHttpClientFactory` is injected into services.  `HttpClient` instances are created by calling `CreateClient`.

Use when:
- The app requires many distinct uses of `HttpClient`.
- The `HttpClient`s have a different configuration.

`appsettings.json`
```json
{
    "TodoHttpClientName": "JsonPlaceholderApi"
}
```

`Program.cs`:
```cs
string? httpClientName = builder.Configuration["TodoHttpClientName"];
ArgumentException.ThrowIfNullOrEmpty(httpClientName);

builder.Services.AddHttpClient(
    httpClientName,
    client =>
    {
        // Set the base address of the named client.
        client.BaseAddress = new Uri("https://jsonplaceholder.typicode.com/");

        // Add a user-agent default request header.
        client.DefaultRequestHeaders.UserAgent.ParseAdd("dotnet-docs");
    });
```

## Creating a Named Client
Each time CreateClient is called, a new instance of HttpClient is created and the configuration action is called.
```cs
// Create a named client with CreateClient:
public sealed class TodoService
{
    private readonly IHttpClientFactory _httpClientFactory = null!;
    private readonly IConfiguration _configuration = null!;
    private readonly ILogger<TodoService> _logger = null!;

    public TodoService(
        IHttpClientFactory httpClientFactory,
        IConfiguration configuration,
        ILogger<TodoService> logger) => (_httpClientFactory, _configuration, _logger) = 
          (httpClientFactory, configuration, logger);

    public async Task<Todo[]> GetUserTodosAsync(int userId)
    {
        // Create the client
        string? httpClientName = _configuration["TodoHttpClientName"];
        using HttpClient client = _httpClientFactory.CreateClient(httpClientName ?? "");

        try
        {
            // Make HTTP GET request
            // Parse JSON response deserialize into Todo type
            Todo[]? todos = await client.GetFromJsonAsync<Todo[]>(
                $"todos?userId={userId}",
                new JsonSerializerOptions(JsonSerializerDefaults.Web));

            return todos ?? Array.Empty<Todo>();
        }
        catch (Exception ex)
        {
            _logger.LogError("Error getting something fun to say: {Error}", ex);
        }

        return Array.Empty<Todo>();
    }
}
```

# Typed Clients
In the *typed client* approach, typed clients are transient objects usually injected into services.  They:
- Provide the same capabilities as named clients but do not require strings as names.
- Provide IntelliSense and compiler help.
- Provide a single location to configure and interact with a particular `HttpClient`:
  - ie: A single backend endpoint.

<o>Do not use typed clients in singleton services.</o>

```cs
public sealed class TodoService : IDisposable
{
    private readonly HttpClient _httpClient = null!;
    private readonly ILogger<TodoService> _logger = null!;

    public TodoService(
        HttpClient httpClient,
        ILogger<TodoService> logger) =>
        (_httpClient, _logger) = (httpClient, logger);

    public async Task<Todo[]> GetUserTodosAsync(int userId)
    {
        try
        {
            // Make HTTP GET request
            // Parse JSON response deserialize into Todo type
            Todo[]? todos = await _httpClient.GetFromJsonAsync<Todo[]>(
                $"todos?userId={userId}",
                new JsonSerializerOptions(JsonSerializerDefaults.Web));

            return todos ?? Array.Empty<Todo>();
        }
        catch (Exception ex)
        {
            _logger.LogError("Error getting something fun to say: {Error}", ex);
        }

        return Array.Empty<Todo>();
    }

    public void Dispose() => _httpClient?.Dispose();
}
```
In `Program.cs`:
```cs
HostApplicationBuilder builder = Host.CreateApplicationBuilder(args);

builder.Services.AddHttpClient<TodoService>(
    client =>
    {
        // Set the base address of the typed client.
        client.BaseAddress = new Uri("https://jsonplaceholder.typicode.com/");

        // Add a user-agent default request header.
        client.DefaultRequestHeaders.UserAgent.ParseAdd("dotnet-docs");
    });
```

# Sending Requests
An example HTTP POST request:
```cs
public async Task CreateItemAsync(Item item)
{
    using StringContent json = new(
        JsonSerializer.Serialize(item, new JsonSerializerOptions(JsonSerializerDefaults.Web)),
        Encoding.UTF8,
        MediaTypeNames.Application.Json);

    using HttpResponseMessage httpResponse =
        await _httpClient.PostAsync("/api/items", json);

    httpResponse.EnsureSuccessStatusCode();
}
```

# More Documentation:
- https://learn.microsoft.com/en-us/dotnet/core/extensions/httpclient-factory#httpclient-lifetime-management
- https://learn.microsoft.com/en-us/dotnet/core/extensions/httpclient-factory#configure-the-httpmessagehandler
- https://learn.microsoft.com/en-us/dotnet/core/extensions/httpclient-factory#using-ihttpclientfactory-together-with-socketshttphandler
