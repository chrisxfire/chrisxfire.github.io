---
title: 2. action return types
date: 2023-08-15T00:00:00-06:00
draft: false
weight: 2
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/action-return-types?view=aspnetcore-7.0)]  

There are four options for return types for web API controller action methods:
1. Specific type
2. `IActionResult`
3. `ActionResult<T>`
4. `HttpResults`

# Specific Type
Use when there are no known conditions against which to safeguard.

## Considerations for Specific Types `IEnumerable<T>` or `IAsyncEnumerable<T>`
ASP.NET Core buffers the result of actions that return `IEnumerable<T>` before writing them to the response:
```cs
[HttpGet("syncsale")]
public IEnumerable<Product> GetOnSaleProducts()
{
    var products = _productContext.Products.OrderBy(p => p.Name).ToList();

    foreach (var product in products)
        if (product.IsOnSale)
            yield return product;
}
```

Consider using `IAsyncEnumerable<T>` when asynchronous iteration is needed:
```cs
[HttpGet("asyncsale")]
public async IAsyncEnumerable<Product> GetOnSaleProductsAsync()
{
    var products = _productContext.Products.OrderBy(p => p.Name).AsAsyncEnumerable();

    await foreach (var product in products)
        if (product.IsOnSale)
            yield return product;
}
```

# `IActionResult`
Use when multiple `ActionResult` return types are possible. For example, consider that when model validation fails, an HTTP 400 response is returned.

`ActionResult` types represent various HTTP status codes. Any class deriving from `ActionResult` (like `BadRequestResult`, `NotFoundResult`, `OkObjectResult`, etc) is a valid return type.

In this action, `[ProducesResponseType]` is used to indicate that it can return two ActionResult derivatives: `NotFoundResult` or `OkObjectResult`:
```cs
[HttpGet("{id}")]
[ProducesResponseType(StatusCodes.Status200OK, Type = typeof(Product))]
[ProducesResponseType(StatusCodes.Status404NotFound)]
public IActionResult GetById_IActionResult(int id)
{
    var product = _productContext.Products.Find(id);
    return product == null 
    ? NotFound() // same as NotFoundResult(); HTTP 404
    : Ok(product); // same as OkObjectResult(product); HTTP 200
}
```

## `ActionResult<T>`
Like `IActionResult`, `ActionResult<T>` enables returning a type deriving from `ActionResult` or returning a specific type. It offers these benefits vs `IActionResult`:
- Omitting the `Type` property of `[ProducesResponseType]` attribute (ie: `[ProducesResponseType(200)]` instead of `[ProducesResponseType(200, Type = typeof(Product))]`)
- Convert both `T` and `ActionResult` to `ActionResult<T>` via implicit cast operators.

# `HttpResults` (`IResult`)
`HttpResults` can be used in both minimal APIs and controller-based APIs and are useful when sharing code between the two.  

The `Microsoft.AspNetCore.Http.HttpResults` namespace contains types that implement the `IResult` interface. `HttpResults` can be returned by calling `IResult.ExecuteAsync` or helper methods on the static `Results` class. It <o>does not</o> support content negotiation.

Example:
```cs
[HttpPost]
[Consumes(MediaTypeNames.Application.Json)]
[ProducesResponseType(typeof(Product), StatusCodes.Status201Created)]
[ProducesResponseType(StatusCodes.Status400BadRequest)]
public async Task<IResult> CreateAsync(Product product)
{
    if (product.Description.Contains("XYZ Widget"))
    {
        return Results.BadRequest();
    }

    _productContext.Products.Add(product);
    await _productContext.SaveChangesAsync();

    var location = Url.Action(nameof(GetById), new { id = product.Id }) ?? $"/{product.Id}";
    return Results.Created(location, product);
}
```

## `Result<T>`
Like `HttpResults`, `Result<T>` can be used when sharing code between minimal and controller-based APIs. Compared to `HttpResults`, all `[ProducesResponseType]` attributes can be excluded. 

Additionally, when multiple `IResult` return types are needed, prefer returning `Result<TResult1, TResult2>` over `IResult` because generic union types automatically retain endpoint metadata.

The static `TypedResults` class returns concrete `IResult` implementations.

Example:
```cs
[HttpGet("{id}")]
public Results<NotFound, Ok<Product>> GetById(int id)
{
    var product = _productContext.Products.Find(id);
    return product == null ? TypedResults.NotFound() : TypedResults.Ok(product);
}
```

# Web API Conventions   
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/web-api/advanced/conventions?view=aspnetcore-7.0

Web API conventions are a substitute for decorating actions with `[ProducesResponseType]`. They define the most common return types and status codes returned from a specific type of action and identify actions that deviate from that standard.

Conventions work by applying attributes behind the scenes.  

Default conventions are in `Microsoft.AspNetCore.Mvc.DefaultApiConventions` namespace.

## Applying Web API Conventions
Each action must be associated with *exactly one* convention. Conventions can be applied to actions, controllers (to all actions in the controller), or assemblies (to all controllers in the assembly).

Here, the `Put` convention is applied to the `Update` action:
```cs
// PUT api/contactsconvention/{guid}
[HttpPut("{id}")]
[ApiConventionMethod(typeof(DefaultApiConventions), 
                     nameof(DefaultApiConventions.Put))]
public IActionResult Update(string id, Contact contact)
{
    var contactToUpdate = _contacts.Get(id);

    if (contactToUpdate == null) 
        return NotFound();

    _contacts.Update(contact);

    return NoContent();
}
```

This convention applies these attributes to the action:
```cs
[ProducesDefaultResponseType]
[ProducesResponseType(StatusCodes.Status204NoContent)]
[ProducesResponseType(StatusCodes.Status404NotFound)]
[ProducesResponseType(StatusCodes.Status400BadRequest)]
```

## Creating Custom Conventions
Custom conventions can be created.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/web-api/advanced/conventions?view=aspnetcore-7.0#create-web-api-conventions