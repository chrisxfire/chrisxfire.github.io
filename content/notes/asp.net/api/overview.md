---
title: overview
date: 2023-05-04T00:00:00-06:00
draft: false
weight: -1
---

# Abstract
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/apis?view=aspnetcore-7.0

## Two Approaches
In ASP.NET Core, APIs can be built with the *controller-based* approach or the *minimal API* approach:
- Controller-based
  - Controllers are classes that derive from `ControllerBase`.
  - Take dependencies via constructor injection or property injection.
- Minimal APIs 
  - Hide the host class and focus on building APIs via extension methods that take functions as lambda expressions.
  - Take dependencies via accessing the service provider.

Minimal APIs do not support:
- Model binding (via `IModelBinder`, `IModelBinderProvider`); a custom binding shim can be used
- Validation (via `IModelValidator`)
- [Application parts](https://learn.microsoft.com/en-us/aspnet/core/mvc/advanced/app-parts?view=aspnetcore-7.0) or [application model](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/application-model?view=aspnetcore-7.0)
- View rendering (recommendation: use Razor Pages)
- `JsonPatch`
- `OData`

In the sample code below, both approaches use this class:  
`WeatherForecast.cs`
```cs
namespace APIWithControllers;

public class WeatherForecast
{
    public DateOnly Date { get; set; }

    public int TemperatureC { get; set; }

    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);

    public string? Summary { get; set; }
}
```

### Controller-based Example
`Program.cs`
```cs
namespace APIWithControllers;

public class Program
{
    public static void Main(string[] args)
    {
        var builder = WebApplication.CreateBuilder(args);

        builder.Services.AddControllers();
        var app = builder.Build();

        app.UseHttpsRedirection();

        app.MapControllers();

        app.Run();
    }
}
```

`Controllers/WeatherForecastController.cs`
```cs
using Microsoft.AspNetCore.Mvc;

namespace APIWithControllers.Controllers;
[ApiController]
[Route("[controller]")]
public class WeatherForecastController : ControllerBase
{
    private static readonly string[] Summaries = new[]
    {
        "Freezing", "Bracing", "Chilly", "Cool", "Mild", "Warm", "Balmy", "Hot", "Sweltering", "Scorching"
    };

    private readonly ILogger<WeatherForecastController> _logger;

    public WeatherForecastController(ILogger<WeatherForecastController> logger)
    {
        _logger = logger;
    }

    [HttpGet(Name = "GetWeatherForecast")]
    public IEnumerable<WeatherForecast> Get()
    {
        return Enumerable.Range(1, 5).Select(index => new WeatherForecast
        {
            Date = DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
            TemperatureC = Random.Shared.Next(-20, 55),
            Summary = Summaries[Random.Shared.Next(Summaries.Length)]
        })
        .ToArray();
    }
}
```

### Minimal API Example
`Program.cs`
```cs
namespace APIWithControllers;

public class Program
{
    public static void Main(string[] args)
    {
        var builder = WebApplication.CreateBuilder(args);

        builder.Services.AddControllers();
        var app = builder.Build();

        app.UseHttpsRedirection();

        app.MapControllers();

        app.Run();
    }
}
```


# From Pluralsight/ASP.NET Core 6 Fundamentals
## Routing
ASP.NET Core APIs generally use attribute-based routing:
```cs
[Route("api/[controller]")]
[ApiController] // indicates this type and all derived types are used to serve HTTP responses
// accessible via /api/controller-name
public class PieController : ControllerBase // an API Controller without View support; includes Action Result helper methods
{
    private readonly IPieRepository _pieRepository;
    
    [HttpGet]
    // triggered via GET /api/pie
    public IActionResult GetAll()
    {
    }
    
    [HttpGet("{id}")]
    // triggered via GET /api/pie/<int>
    public IActionResult GetById(int id)
    {
    }
}
```

## ControllerBase Helper Methods
| Method        | Use when                                     | Returns  |
| ------------- | -------------------------------------------- | -------- |
| `Ok()`        | Request is good                              | HTTP 200 |
| `BadRequest`  | Request is malformed or missing a property   | HTTP 400 |
| `NotFound()`  | Client requests resource that does not exist | HTTP 404 |
| `NoContent()` | Request is good but no content to return     | HTTP 204 |

## Creating an API
### 1. Enable API Controller support
`Program.cs`
```cs
// enable support for MVC Controllers:
builder.Services.AddControllers() // not needed if AddControllersWithViews() is called
                    .AddJsonOptions(options =>
                    {
                // when responses are serialized, they may trigger an infinite loop without this option:
                        options.JsonSerializerOptions.ReferenceHandler = ReferenceHandler.IgnoreCycles;
                    });
…
// add controllers to the middleware pipeline:
app.MapControllers(); // not needed if MapDefaultControllerRoute() is called
```

### 2. Create API Controllers
`/Controllers/SearchController.cs` or `/Controllers/Api/SearchControllers.cs`
```cs
[Route("api/[controller]")]
[ApiController] // indicates this type and all derived types are used to serve HTTP responses
public class SearchController : ControllerBase // an API Controller without View support; includes Action Result helper methods
{
    private readonly IPieRepository _pieRepository;

    public SearchController(IPieRepository pieRepository)
    {
        _pieRepository = pieRepository;
    }

    [HttpGet]
    public IActionResult GetAll()
    {
        var allPies = _pieRepository.AllPies;

        return Ok(allPies); // allPies will be converted into JSON
    }

    [HttpGet("{id}")]
    public IActionResult GetById(int id)
    {
        return !_pieRepository.AllPies.Any(p => p.PieId == id)
            ? NotFound()
            : Ok(_pieRepository.AllPies.Where(p => p.PieId == id));
    }
    
    [HttpPost]
    public IActionResult SearchPies([FromBody] string searchQuery) // indicates searchQuery will be provided in body of HTTP POST request
    {
        IEnumerable<Pie> pies = new List<Pie>();

        if (!string.IsNullOrEmpty(searchQuery))
            pies = _pieRepository.SearchPies(searchQuery);

        return new JsonResult(pies); // JsonResult formats pies object as JSON; could also have used Ok() method
    }
}
```
