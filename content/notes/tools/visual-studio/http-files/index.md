---
title: http files
date: 2023-08-29T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/test/http-files?view=aspnetcore-8.0

<g>Availability</g>: ASP.NET Core 8? (documentation is unclear), Visual Studio 2022 v17.6+

HTTP files in Visual Studio allow you to create HTTP requests. You can use the editor to create and send requests and view responses.

# File Format
The sequence is important:
1. Variables
2. HTTP request
3. Headers (optional)
4. Body (optional)

The request must be in the format `HTTP_METHOD URL HTTP_VERSION` where `HTTP_VERSION` is optional and is one of `HTTP/1.1` `HTTP/2` `HTTP/3`.

```
# this is a comment
// this is a comment
@hostname=localhost
@port=44320
// Variables are access with double curly braces:
GET https://{{hostname}}:{{port}}/weatherforecast 
```

## Headers
Headers must immediately follow the request with no additional spacing:
```
GET https://localhost:7220/weatherforecast
Date: Wed, 27 Apr 2023 07:28:00 GMT

###

GET https://localhost:7220/weatherforecast
Cache-Control: max-age=604800
Age: 100

###
```

## Body
The request body can be added after a blank line following the headers:
```
POST https://localhost:7220/weatherforecast
Content-Type: application/json
Accept-Language: en-US,en;q=0.5

{
    "date": "2023-05-10",
    "temperatureC": 30,
    "summary": "Warm"
}

###
```

## Multiple requests
Multiple requests can be delimited via `###`:
```
GET https://localhost:7220/weatherforecast

###

GET https://localhost:7220/weatherforecast?date=2023-05-11&location=98006

###

GET https://localhost:7220/weatherforecast HTTP/3

###
```

# Usage
- **Add** > **New Item** > ASP.NET Core > General > **HTTP File**
- Save the file
- Click the green "run" arrow.  The response pulls up next to the request:  
<img alt="A screenshot of the Visual Studio HTTP file experience" src="image.png" width="50%" height="50%">

## With Endpoints Explorer
- View > Other Windows > Endpoints Explorer
- Right-click a request > **Generate Request**

If an `.http` file with the project name as the file name exists, the request is added to that file.  
Otherwise, an `.http` file is created with the project name as the file name, and the request is added to that file.