---
title: RestSharp
date: 2021-11-28T07:42:25-0700
draft: false
---
# [RestSharp](https://restsharp.dev/getting-started/)
Make sync/async calls to remote resources over HTTP.  
Does not support HTTP/2.

# Installation
```powershell
dotnet add package restsharp
```

# Libraries
```cs
using RestSharp;
using RestSharp.Authenticators;
```

# Basic
```cs
var client = new RestClient("https://api.twitter.com/1.1");
client.Authenticator = new HttpBasicAuthenticator("username", "password");

var request = new RestRequest("statuses/home_timeline.json", DataFormat.Json);

var response = client.Get(request);Returns an IRestResponse instance.
// or var response = client.Get<*type*>(request); // To deserialize into .NET classes.
```

# Asynchronous
```cs
var client = new RestClient("https://api.twitter.com/1.1");
client.Authenticator = new HttpBasicAuthenticator("username", "password");

var request = new RestRequest("statuses/home_timeline.json", DataFormat.Json);

var timeline = await client.GetAsync<HomeTimeline>(request, cancellationToken);cancellationToken is optional.
```

# Content Type
```cs
var request = new RestRequest("address/update")
// The Content-Type and DataFormat are added automatically:
    .AddJsonBody(updatedAddress); // Or AddXmlBody()

var response = await client.PostAsync<AddressUpdateResponse>(request);
```

Deserialization is automatic. The `Accept` header is only needed if the response is to be deserialized manually.

# Responses
## `IRestResponse`
Both `Execute` or `ExecuteAsync` return an `IRestResponse` instance.

### Properties
- `ContentType`
- `Content`  The response content as a string.
- `ErrorException` - If the request failed, contains the exception.
- `ErrorMessage` If the request failed, contains the error message.
- `IsSuccessfulBoolean` if the request succeeded.
- `StatusCode` The response's HTTP status code.

## `IRestResponse<T>`
Returned from `Execute<T>` and `ExecuteAsync<T>`.

### Properties
Same as `IRestResponse`, but also includes `T<Data>` The deserialized response.

`Get<T>` and `GetAsync<T>` return a deserialized response.  
When using these extension methods, set `IRestClient.ThrowAnyError = true` and wrap in a try/catch block.

# Serialization
## JSON
JSON serialization is handled by a simplistic serializer forked from *SimpleJson*.

<o>Known Issue</o>  
*SimpleJson* doesn't use the UTC time zone. Set the date format manually:  
```cs
client.UseSerializer( () => new JsonSerializer { DateFormat = "yyyy-MM-ddTHH:mm:ss.FFFFFFFZ" } );
```

## System.Text.Json
This serializer is available via a separate package:
```powershell
dotnet add package RestSharp.Serializers.SystemTextJson
```
```cs
client.UseSystemTextJson();
```

## XML
RestSharp uses a built-in XML serializer.
To use `DotNetXmlSerializer` (which uses `System.Xml.Serialization`):
```cs
client.UseDotNetXmlSerializer();
```

# Working With Files
This gist uses a `Stream` to avoid memory buffering.  Use when retrieving large amount of data that is immediately written to disk:
```cs
var tempFile = Path.GetTempFileName();
using var writer = File.OpenWrite(tempFile);

var client = new RestClient(baseUrl);
var request = new RestRequest("Assets/LargeFile.7z");

request.ResponseWriter = responseStream =>
{
    using (responseStream)
    {
        responseStream.CopyTo(writer);
    }
};
var response = client.DownloadData(request);
```

# [Authenticators](https://restsharp.dev/usage/authenticators.html#authenticators)

# [Request Parameters](https://restsharp.dev/usage/parameters.html#request-parameters)

# [Error Handling](https://restsharp.dev/usage/exceptions.html)