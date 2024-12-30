---
title: url matching
date: 2023-04-20T00:00:00-06:00
draft: false
weight: 1
---

# overview
An incoming request comes in.  Routing matches the incoming request to an endpoint:
- It sets an `Endpoint` and routes values to a request feature on the `HttpContext` from the current request:
    - `HttpContext.GetEndpoint` returns the endpoint
    - `HttpRequest.RouteValues` returns the collection of route values

URL matching is part of routing and operates in a configurable set of phases:
1. Process the URL path against a set of endpoints and their route templates; return a list of ALL matches  
    2. Remove matches that fail with route constraints applied; return the remaining matches  
        3. Remove matches that fail the set of `MatcherPolicy` instances; return the remaining matches  
            4. Use EndpointSelector to make a final decision from the preceding list  

The `EndpointSelector` choses the highest priority endpoint (based on RouteEndpoint.Order and route template precedence) as the best match.

Use `RouteEndpoint.Order` only when necessary to avoid ambiguity.  Prefer to trust `EndpointSelector` logic.

# Route Template Precedence [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#route-template-precedence-and-endpoint-selection-order)]  

Assigns each route template a value based on how specific the route is.  Logic:
- Templates with more segments are more specific
- A segment with literal text is more specific than a parameter segment
- A parameter segment with a constraint is more specific than one without
- A complex segment is as specific as a parameter segment with a constraint
- Catch-all parameters are least specific

# URL Generation [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#url-generation-concepts)]  

The process by which routing creates a URL path based on a set of route values.  This enables separation of endpoints and the URLs that access them.

# Route Template [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#route-templates)]  

Tokens within `{}` are route parameters that are bound if the route is matched.  Route parameters MUST be separate by a literal value:
- `{controller=Home}{action=Index}` is NOT a valid route.
	
Escape `{` with `{{`.

## Catch-all parameters
Given the route `{ path = "my/path" }`:
- The route `foo/{*path}` generates `foo/my%2Fpath`.
- The route `foo{/**path}` generates `foo/my/path`.

Given the template `files/{filename}.{ext?}`
- Both `/files/myFile.txt` and `/files/myFile` will match even though `/files/myFile` does not have a dot at the end.

## complex segments
Complex segments are processed by matching up literal delimiters from right to left.  The match is non-greedy.  
Assume the route template `/a{b}c{d}` and the URL path `/abcd`:
- Searching right to left, the first literal found is `c`
- Everything to the right of that (`d`) is now matched to the route parameter `{d}`
- Searching continues.  The next literal, `a`, is found.
- The value to the right (`b`) is now matched to the route parameter `{b}`

If the above URL path was `/aabcd` instead, it would not match because after `b` is matched to route parameter `{b}`, no route template remains to match the remaining `a`.

# Routing with Special Characters [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#routing-with-special-characters)]  

Route parameters are not always URL-encoded.  See [this GitHub issue](https://github.com/.net/aspnetcore/issues/11544).

# Route Constraints [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#route-constraints)]  

Route constraints are used to disambiguate similar routes.  Do not use route constraints for input validation.  Invalid input would result in an HTTP/404 Not Found and instead should result in HTTP/400 Bad Request.

Route constraints are of the format `{parameter:constraint(contraint-argument1, …}`  
Example: `blog/{article:minlength(10)}`

Multiple constraints can be applied to a single parameter:

Route constraints include `int`, `bool`, `datetime`, `decimal`, `double`, `float`, `guid`, `long`, `minlength(string)`, `maxlength(string)`, `length(string)`, `min(int)`, `max(int)`, `range(int min, int max)`, `alpha`, `regex(expression)` and `required`.

Note:  when using the regex constraint, ASP.NET Core automatically passes a timeout and adds `RegexOptions.IgnoreCase | RegexOptions.Compiled | RegexOptions.CultureInvariant` to the call.

## custom route constraints
These can be created by implementing `IRouteConstraint`.  
See also:  https://github.com/.net/aspnetcore/tree/main/src/Http/Routing/src/Constraints

# route parameter transformers
Transformers transform a parameter's value when generating links and matching actions and pages to URLs.  They execute when generating a link.

## example
A custom slugify parameter transformer:  
Route pattern `blog\{article:slugify}` with `Url.Action(new { article = "MyTestArticle" })` generates `blog\my-test-article`.

## implementation
```cs
public class SlugifyParameterTransformer : IOutboundParameterTransformer
{
    public string? TransformOutbound(object? value)
    {
        if (value is null)
        {
            return null;
        }

        return Regex.Replace(
            value.ToString()!,
                "([a-z])([A-Z])",
            "$1-$2",
            RegexOptions.CultureInvariant,
            TimeSpan.FromMilliseconds(100))
            .ToLowerInvariant();
    }
}
```
Parameter transformers are configured using `ConstraintMap` in `Program.cs`:  
```cs
builder.Services.AddRouting(options =>
    options.ConstraintMap["slugify"] = typeof(SlugifyParameterTransformer));
```
# URL Generation Reference [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0#url-generation-reference)]  
