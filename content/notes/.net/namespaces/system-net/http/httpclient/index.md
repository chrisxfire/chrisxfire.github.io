---
title: notes > .net > namespaces > system net > http > httpclient
date: 2021-11-11T09:41:47-0700
draft: false
---
# [HttpClient](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient?view=net-6.0)
`Object` –> `HttpMessageInvoker` –> `HttpClient`  

Sending HTTP requests and receiving HTTP responses via URI.
- `HttpClient` is intended to be instantiated once per application.
- `HttpClient` works only on async methods for its long-running APIs.
- Every `HttpClient` instance uses its own connection pool.

## Thread Safety
`HttpClient` is <r>not thread safe</r>. However, all HTTP verb methods, except `Send()`, are thread safe.

[Flaw](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)
1.  When the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a socket exhaustion problem.
2.  Long-running `HttpClient`s

Mitigation
1.  Create `HttpClient` as a static object.

# Construction
`HttpClient()` — Uses `HttpClientHandler` that is disposed when instance is destroyed.
- This concrete instance of `HttpClientHandler` has the sockets exhaustion and DNS problems mentioned in Flaw.
`HttpClient(HttpMessageHandler)` — Uses the specified handler.  
`HttpClient(HttpMessageHandler, Bool)` — Uses the specified handler. Specifies whether to destroy handler when instance is destroyed.

# Requests
`HttpClient` supports DELETE, GET, PATCH, POST, and PUT HTTP verbs.

Use the `Send()` methods for fine-grained control.  
These methods use the `HttpRequestMessage` type which include headers, the verb, content, and options.  

# Methods
- `CancelPendingRequests()`
- `Dispose()` — Release unmanaged resources; dispose of managed resources.  
- `GetAsync(URI)` — Send a GET request to URI.  
- `GetByteArrayAsync(URI)` — Send a GET request to URI; return response body as byte array.  
- `GetStreamAsync(URI)` — Send a GET request to URI; return response body as stream.  
- `GetStringAsync(URI)` — Send a GET request to URI; return response body as string.  
- `PostAsync(URI, content)` — Send a POST request to URI. content is HttpContent.  

# Properties
- `BaseAddress` — Get/set the URI.
- `DefaultRequestHeaders` — Get/set headers which should be sent with each request as HttpRequestHeaders object.
- `DefaultRequestVersion` — Get/set default HTTP version to use on each request.
- `Timeout` — Get/set request time out.

# Example: GET
```cs
static readonly HttpClient client = new HttpClient();

static async Task Main() 
{
    try
    {
        // Asynchronously, send a GET request to uri and return the response body as a string.
        string responseBody = await client.GetStringAsync(uri);

        Console.WriteLine(responseBody);
    }
    catch(HttpRequestException e) 
    {
    }
}
```

# Example: POST
```cs
static readonly HttpClient client = new HttpClient();

static async Task<string> PostApi(HttpClient client, string url, HttpContent content) 
{
    var response = await client.PostAsync(url, content);
    string result = response.Content.ReadAsStringAsync().Result;
}
```

# Example
```cs
public class GoodController : ApiController 
{
    private static readonly HttpClient HttpClient;

    static GoodController() 
    {
        HttpClient = new HttpClient();
    }
}
```
