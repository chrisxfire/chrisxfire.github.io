---
title: call a web api
date: 2023-07-21T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Blazor WASM apps call web APIs using a preconfigured `HttpClient` service which is focused on <o>making requests back to the server of origin</o> (not a 3rd party API).  Create `HttpClient` service configurations manually for requests to other web APIs.
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/call-web-api?view=aspnetcore-7.0&pivots=webassembly

## Sending PATCH Requests
If sending HTTP PATCH requests, there are additional considerations beyond those listed in these notes.  
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/call-web-api?view=aspnetcore-7.0&pivots=webassembly#patch-as-json-patchasjsonasync

# Using the Preconfigured `HttpClient`
1. Add the HttpClient service to the DI container:  
    `Program.cs`
    ```cs
    builder.Services.AddScoped(sp => 
        new HttpClient
        {
            // The client's base address is set to the originating server's address:
            BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
        });
    ```
2. Inject required services:  
    `SomeComponent.razor`
    ```html
    @using System.Net.Http 
    <!-- For HttpClientJsonExtensions: -->
    @using System.Net.Http.Json 
    @inject HttpClient Http
    ```

3. Send requests from the component in the `OnInitializedAsync()` method after the component has finished initializing:
    `SomeComponent.razor`
    ```cs
    @code {
    private TodoItem[]? todoItems;

    protected override async Task OnInitializedAsync() => 
        todoItems = await Http.GetFromJsonAsync<TodoItem[]>("api/TodoItems");
    }
    ```

# Using the `IHttpClientFactory`
Instead of injecting a preconfigured `HttpClient`, `IHttpClientFactory` can be used instead, similar to [how it is used in other .NET apps](../../../../../_net/web/http/ihttpclientfactory).

Both named and typed clients are supported.

## Named Client Example  
`Program.cs`:
```cs
builder.Services.AddHttpClient("NAMED_CLIENT_NAME", client => 
    client.BaseAddress = new Uri(builder.HostEnvironment.BaseAddress));
```

`SomeComponent.razor`
```html
@inject IHttpClientFactory ClientFactory
<!-- ... -->
```
```cs
@code {
    // ...
    protected override async Task OnInitializedAsync()
    {
        var client = ClientFactory.CreateClient("NAMED_CLIENT_NAME");
        result = await client.GetFromJsonAsync<SomeModel[]>("SomeModel");
    }
}
```

## Typed Client Example
1. Add `Microsoft.Extensions.Http` to the app:
    ```powershell
    dotnet add package Microsoft.Extensions.Http
    ```
2. Create the typed client:  
    `SomeHttpClient.cs`
    ```cs
    public class SomeHttpClient
    {
        private readonly HttpClient http;
        private SomeModel[]? results;

        public SomeHttpClient(HttpClient http)
        {
            this.http = http;
        }
        public async Task<SomeModel[]> GetResultsAsync()
        {
            results = await http.GetFromJsonAsync<SomeModel[]>("/api/endpoint");

            return results ?? Array.Empty<SomeModel>();
        }
    }
    ```
3. Use the typed client:  
    `SomeComponent.razor`
    ```html
    @inject SomeHttpClient Http
    <!-- ... -->
    ```
    ```cs
    @code {
        private SomeModel[]? results;

        protected override async Task OnInitializedAsync()
        {
            results = await Http.GetResultsAsync();
        }
    }
    ```

# Fetch API Request Options
Blazor WASM's implementation of `HttpClient` uses Fetch API.  Fetch API can be configured with request-specific options via `HttpRequestMessage` extension methods:
| Extension Method                     | Use to...                                        |
| ------------------------------------ | ------------------------------------------------ |
| `SetBrowserRequestCache`             |                                                  |
| `SetBrowserRequestCredentials`       | ...include credentials in a cross-origin request |
| `SetBrowserRequestIntegrity`         |                                                  |
| `SetBrowserRequestMode`              |                                                  |
| `SetBrowserResponseStreamingEnabled` | ...enable support for response streaming         |

Additional options can be set via the generic [SetBrowserRequestOption](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.components.webassembly.http.webassemblyhttprequestmessageextensions.setbrowserrequestoption?view=aspnetcore-7.0) extension method.

# Cross-Origin Resource Sharing (CORS)
Browser security restricts a web page from making requests to a different domain than the one that served the web page.  This is called the *same-origin policy*.  <o>To make requests from the browser to an endpoint with a different origin (domain), the endpoint must enable CORS</o>.

Adjust the names and ports of `WithOrigins` as needed for the app:  
`Program.cs`
```cs
// ...
app.UseCors(policy => policy
    .WithOrigins("http://localhost:5000", "https://localhost:5001")
    .AllowAnyMethod()
    .WithHeaders(HeaderNames.ContentType);
// ...
```

See also: https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-7.0

# Testing a Web API
Blazor framework's reference source has `HttpClient` test assets: https://github.com/dotnet/aspnetcore/tree/main/src/Components/test/testassets/BasicTestApp/HttpClientTest
