---
title: "notes > asp.net > web apps > mvc > routing"
date: 2023-03-21T00:00:00-06:00
draft: false
---

# Overview
MVC Controllers use Routing middleware to match a URL of an incoming request to and map them to actions.

Route templates are defined in `Program.cs`, describe how URL paths are matched to actions, and are used to generate URLs for links which are typically returned in responses.

# To Use Controllers
Call `MapControllers` to map attribute routed Controllers.
Call `MapControllerRoute` or `MapAreaControllerRoute` to map both conventionally routed Controllers and attribute routed Controllers.

# Conventional Routing
Conventional routing is typically used with Controllers and Views.

## Creating
Conventional routes are typically created in one place in the application, like the middleware pipeline.
The default conventional route:
```cs
app.MapControllerRoute(
    name: "default", // The route's name
    pattern: "{controller=Home}/{action=Index}/{id?}"); // The route template
```

The route name is used only for URL generation and has no impact on matching.

The convenience method `app.MapDefaultControllerRoute()` replaces the above because it uses the `DefaultControllerRoute`.
The `DefaultControllerRoute` is very common:  `{controller=Home}/{action=Index}/{id?}`

For a URL like `/Products/Details/5`:
The route template tokenizes the route path as follows: `{ controller = Products, action = Details, id = 5 }`

If the app has a controller named `ProductsController` and an action named `Details`, a match exists:
```cs
public class ProductsController : Controller
{
    public IActionResult Details(int id) => ControllerContext.MyDisplayRouteInfo(id);
}
```
Tool to display route information: [NuGet Gallery | Rick.Docs.Samples.RouteInfo 1.0.0.8](https://www.nuget.org/packages/Rick.Docs.Samples.RouteInfo)

## Multiple Conventional Routes
Add more calls to `MapControllerRoute` or `MapAreaControllerRoute`:
```cs
app.MapControllerRoute(name: "blog",
                pattern: "blog/{*article}",
                defaults: new { controller = "Blog", action = "Article" });

// Matches URL paths /Blog, /Blog/Article, /Blog/any-string

app.MapControllerRoute(name: "default",
               pattern: "{controller=Home}/{action=Index}/{id?}");
```

## Conventional Routing Order
Conventional routing is order-dependent based on the order in which they are invoked.  Routes with areas should be placed earlier as they are more specific.  Greedy routes should be placed later in the definition.

## Ambiguous Actions
When more than one action matches a route, the actions are ambiguous.  Routing attempts to choose the best candidate.  If it cannot, it will throw an `AmbiguousMatchException` listing the multiple matched endpoints.

# Attribute Routing
Attribute routes are applied to controllers and actions directly rather than in the middleware pipeline.  
Attribute routing is used with REST APIs to model the app's functionality as a set of resources represented by HTTP verbs.  
It allows for precise control of which route templates apply to each action.  

`app.MapControllers()` is called in `Program.cs` to map attribute routed controllers.
```cs
public class HomeController : Controller
{
    [Route("")]
    [Route("Home")]
    [Route("Home/Index")]
    [Route("Home/Index/{id?}")]
    public IActionResult Index(int? id) => ControllerContext.MyDisplayRouteInfo(id);

    [Route("Home/About")]
    [Route("Home/About/{id?}")]
    public IActionResult About(int? id) => ControllerContext.MyDisplayRouteInfo(id);
}
```

## Token Replacement
Use token replacement attributes on actions to match URLs dynamically:
```cs
[Route("")]
[Route("Home")]
[Route("[controller]/[action]")]
public IActionResult Index() => ControllerContext.MyDisplayRouteInfo();
```
Or on classes:
```cs
[Route("[controller]/[action]")]
public class HomeController : Controller
{
    // Route templates applied to an action that start with "/" or "~/" do not get combined with
    // route templates applied to a controller:
    [Route("~/")]
    [Route("/Home")]
    [Route("~/Home/Index")]
    public IActionResult Index() => ControllerContext.MyDisplayRouteInfo();
}
```

## [HTTP Verb Templates](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#verb6)
These are both HTTP verb templates and route templates:
- `[HttpGet]`
- `[HttpPost]`
- `[HttpPut]`
- `[HttpDelete]`
- `[HttpHead]`
- `[HttpPatch]`

## Attribute Routing with HTTP Verb Attributes
Assuming:
```cs
[Route("api/[controller]")]
[ApiController]
public class Test2Controller : ControllerBase
{
    [HttpGet]   // GET /api/test2
    public IActionResult ListProducts() => ControllerContext.MyDisplayRouteInfo();

    // Because {id} is included here, id is appended to the template on the controller, so this action's template is api/[controller]/"{id}
    [HttpGet("{id}")]   // GET /api/test2/xyz
    public IActionResult GetProduct(string id) => ControllerContext.MyDisplayRouteInfo(id);
    
    // The :int portion of this template contstrains the id route values to strings that can be converted to integers.
    [HttpGet("int/{id:int}")] // GET /api/test2/int/3
    public IActionResult GetIntProduct(int id) => ControllerContext.MyDisplayRouteInfo(id);
    
    // For /api/test2/int2/abc, model binding would fail and this would return HTTP/400 Bad Request
    [HttpGet("int2/{id}")]  // GET /api/test2/int2/3
    public IActionResult GetInt2Product(int id) => ControllerContext.MyDisplayRouteInfo(id);
}
```

Here, for URL path `/products3`, `ListProducts` runs when the verb is GET; `CreateProduct` runs when it is POST:
```cs
[HttpGet("/products3")]
public IActionResult ListProducts() => ControllerContext.MyDisplayRouteInfo();

[HttpPost("/products3")]
public IActionResult CreateProduct(MyProduct myProduct) => ControllerContext.MyDisplayRouteInfo(myProduct.Name);
```

Here, the `id` attribute is required:
```cs
[HttpGet("/products2/{id}", Name = "Products_List")]
public IActionResult GetProduct(int id) => ControllerContext.MyDisplayRouteInfo(id);
```

## Attribute Route Ordering
Attribute routes can configure an `Order` property.  
All framework-provided routes include `Order`.  
Setting `Order = -1` runs the route before routes that don't set an order.  
Setting `Order = 1` runs the route after default route ordering.

## [Token Replacement in Route Templates](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#token-replacement-in-route-templates-controller-action-area)

## [Multiple Attribute Routes](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#multiple-attribute-routes)

## [Attribute Route Optional Parameters/Default Values/Constraints](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#specifying-attribute-route-optional-parameters-default-values-and-constraints)

## [IRouteTemplateProvider](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#custom-route-attributes-using-iroutetemplateprovider)

## [Customize Route Attributes in Application Model](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#use-application-model-to-customize-attribute-routes)

# [URL Generation and Ambient Values](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/routing?view=aspnetcore-7.0#url-generation-and-ambient-values)

# [Areas](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/areas?view=aspnetcore-7.0)
