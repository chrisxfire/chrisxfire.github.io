---
title: notes > code > .net > libraries > system.net.http > ihttpclientfactory
date: 2022-07-22T09:36:06-0600
draft: false
---
[Make HTTP requests using IHttpClientFactory in ASP.NET Core | Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-6.0#consumption-patterns)

Benefits:
- Also implements `IHttpMessageHandlerFactory`.
- A central location for naming and configuring `HttpClient` objects.
- Works with `Polly`-based middleware.
- Supports DI. Injected `HttpClient` instances are Scoped.

# Basic Usage
This is a good way to refactor an existing app. No impact on how HttpClient is used. Replace occurrences of where HttpClient instances are created with calls to `CreateClient`.

```cs
public class SomeClass 
{
  private readonly IHttpClientFactory _httpClientFactory;

  public SomeClass(IHttpClientFactory httpClientFactory) => _httpClientFactory = httpClientFactory;

  public async Task OnGet() 
  {
    var httpRequestMessage = new HttpRequestMessage(HttpMethod.Get,"https://api.github.com/repos/dotnet/AspNetCore.Docs/branches")
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

# Named Clients
Use when:
- The app requires many distinct uses of `HttpClient`.
- The `HttpClient`s have a different configuration.

In `Program.cs`:
```cs
// Create a configuration named "GitHub":
builder.Services.AddHttpClient("GitHub", httpClient =>
{
  httpClient.BaseAddress = new Uri("https://api.github.com/");
  // using Microsoft.Net.Http.Headers;
  // The GitHub API requires two headers.
  httpClient.DefaultRequestHeaders.Add(HeaderNames.Accept, "application/vnd.github.v3+json");
  httpClient.DefaultRequestHeaders.Add(HeaderNames.UserAgent, "HttpRequestsSample");
});
```

## Creating a Named Client
Each time CreateClient is called, a new instance of HttpClient is created and the configuration action is called.
```cs
// Create a named client with CreateClient:
public async SomeMethod() 
{
  var httpClient = _httpClientFactory.CreateClient("GitHub");
  // …
}
```

# Typed Clients
- Provide the same capabilities as named clients but do not require strings as names.
- Provide IntelliSense and compiler help.
- Provide a single location to configure and interact with a particular HttpClient:
  - ie: A single backend endpoint.

```cs
public class GitHubService
{
  private readonly HttpClient _httpClient;
  // Typed clients accepts an HttpClient parameter in its constructor:
  public GitHubService(HttpClient httpClient)
  {
    _httpClient = httpClient;

    _httpClient.BaseAddress = new Uri("https://api.github.com/");

    // using Microsoft.Net.Http.Headers;
    // The GitHub API requires two headers.
    _httpClient.DefaultRequestHeaders.Add(HeaderNames.Accept, "application/vnd.github.v3+json");
    _httpClient.DefaultRequestHeaders.Add(HeaderNames.UserAgent, "HttpRequestsSample");
  }

  public async Task<IEnumerable<GitHubBranch>?> GetAspNetCoreDocsBranchesAsync() =>
    await _httpClient.GetFromJsonAsync<IEnumerable<GitHubBranch>>("repos/dotnet/AspNetCore.Docs/branches");
}
```
In `Program.cs`:
```cs
// Register the GitHubService typed client class:
bulder.Services.AddHttpClient<GitHubService>().AddTypedClient<GitHubService>();
// The above creates an instance of HttpClient, an instance of GitHubService, and passes the aforementioned HttpClient to its constructor.

Alternatively, configure a typed client during registration in Program.cs:
builder.Services.AddHttpClient<GitHubService>(httpClient =>
{
  httpClient.BaseAddress = new Uri("https://api.github.com/");
  // ...
});
```
