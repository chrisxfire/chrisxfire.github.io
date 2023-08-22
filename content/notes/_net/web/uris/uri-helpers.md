---
title: uri helpers
date: 2023-08-22T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Various classes for working with URIs.

## `Microsoft.AspNetCore.Http.QueryString`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.http.querystring?view=aspnetcore-7.0

"Provides correct handling for QueryString value when needed to reconstruct a request or redirect URI string."

## `Microsoft.AspNetCore.Http.Extensions.QueryBuilder`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.http.extensions.querybuilder?view=aspnetcore-7.0

"For constructing a query string."
- Adding onto an existing query string
- Constructing a `QueryString` from a `QueryBuilder`

## `Microsoft.AspNetCore.Http.Extensions.UriHelper`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.http.extensions.urihelper?view=aspnetcore-7.0

"For constructing encoded URIs for use in headers and other URIs."
- Combining URI components into an absolute or relative URI
- Encoding URIs

## `Microsoft.AspNetCore.Mvc.Routing.UrlHelper`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.mvc.routing.urlhelper?view=aspnetcore-7.0

"An implementation of IUrlHelper that contains methods to build URLs for ASP.NET MVC within an application."
- Requires an `ActionContext` from the current request

## `Microsoft.AspNetCore.WebUtilities.QueryHelpers`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.webutilities.queryhelpers?view=aspnetcore-7.0

"Methods for parsing and manipulating query strings."
- Add a query string to a URI
- Parse a query string into its component key/value pairs

## `System.Uri`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/system.uri?view=net-7.0#remarks)

"Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI."
- Checking schema
- Escaping/un-escaping data

## `System.UriBuilder`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/system.uribuilder?view=net-7.0

Constructing and modifying URIs for the `Uri` class.
- Properties for each component of a URI

## `System.Web.HttpUtility`
> Documentation: https://learn.microsoft.com/en-us/dotnet/api/system.web.httputility?view=net-7.0

"Provides methods for encoding and decoding URLs when processing Web requests. This class cannot be inherited."
- Encoding/decoding HTML
- Encoding/decoding URLs
- Encoding a JavaScript string
- `ParseQueryString` into a `NameValueCollection`
