---
title: httpclient
date: 2021-11-11T09:41:47-0700
draft: false
weight: 1
---

# [HttpClient](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient?view=net-6.0)
`Object` –> `HttpMessageInvoker` –> `HttpClient`  

Sending HTTP requests and receiving HTTP responses via URI.
- `HttpClient` is intended to be instantiated once per application.
- `HttpClient` works only on async methods for its long-running APIs.
- Every `HttpClient` instance uses its own connection pool.

## Thread Safety
<r>Warning</r>:  `HttpClient` is **not thread safe**. However, all HTTP verb methods, except `Send()`, *are* thread safe.

## [Flaw](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)
When the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a socket exhaustion problem.

Mitigation: create `HttpClient` as a static object.

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

# Examples 
GET request example:
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

POST request example:
```cs
static readonly HttpClient client = new HttpClient();

static async Task<string> PostApi(HttpClient client, string url, HttpContent content) 
{
    var response = await client.PostAsync(url, content);
    string result = response.Content.ReadAsStringAsync().Result;
}
```

# HTTP/3
> [!IMPORTANT]
> Availability: .NET 6 (preview), .NET 7 (production)

HTTP/3 uses a different underlying transport (QUIC) than HTTP/2 and HTTP/1.1 (TCP).  Advantages:
- Faster response time for the first request (negotiates connections in fewer round trips)
- Lost packets only affect the requests where data has been lost (QUIC provides native multiplexing; HTTP/2 multiplexes multiple requests via a single TCP connection, so packet loss on the connection affects all requests)
- Support for transitioning between networks (WiFi and cellular, for example)
  - <o>Note</o>: `HttpClient` and Kestrel do not support network transitions as of .NET 7.

## `HttpClient` Settings for HTTP/3
There are two approaches:
1. Configure HTTP/3 by setting `HttpRequestMessage.Version` to `3.0`.
   * The disadvantage of this approach is that not all network infrastructure supports HTTP/3.
2. Set `HttpRequestMessage.Version` to `1.1`, and `HttpRequestMessage.VersionPolicy` to `HttpVersionPolicy.RequestVersionOrHigher`.
   * The advantage of this approach is that it supports HTTP/3 for network infrastructure that supports it.

## Platform Dependencies
.NET's implementation of HTTP/3 uses `MsQuic`.  The underlying platform must meet these requirements, otherwise HTTP/3 is disabled:
- Windows
  - Windows 11, Windows Server 2022
- Linux
  - OpenSSL 1.1
  - `libmsquic` (`sudo apt install libmsquic`)
- macOS
  - HTTP/3 is not supported on macOS.

## Using `HttpClient` with HTTP/3
```cs
// See https://aka.ms/new-console-template for more information
using System.Net;

using var client = new HttpClient
{
    DefaultRequestVersion =  HttpVersion.Version30,
    DefaultVersionPolicy = HttpVersionPolicy.RequestVersionExact
};

Console.WriteLine("--- localhost:5001 ---");

HttpResponseMessage resp = await client.GetAsync("https://localhost:5001/");
string body = await resp.Content.ReadAsStringAsync();

Console.WriteLine(
    $"status: {resp.StatusCode}, version: {resp.Version}, " +
    $"body: {body.Substring(0, Math.Min(100, body.Length))}");
```

## Testing HTTP/3 Clients
Use Cloudflare's test site: https://cloudflare-quic.com/
