---
title: "notes > asp.net > api > overview"
date: 2023-05-04T00:00:00-06:00
draft: false
---

From Pluralsight/ASP.NET Core 6 Fundamentals
# Overview

# Routing
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

# ControllerBase Helper Methods
| Method      | Use when                                     | Returns  |
| ----------- | -------------------------------------------- | -------- |
| Ok()        | Request is good                              | HTTP 200 |
| BadRequest  | Request is malformed or missing a property   | HTTP 400 |
| NotFound()  | Client requests resource that does not exist | HTTP 404 |
| NoContent() | Request is good but no content to return     | HTTP 204 |

# Creating an API
## 1. Enable API Controller support
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

## 2. Create API Controllers
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