---
title: "notes > asp.net > reading > architecting modern web apps > working with data"
date: 2023-04-14T00:00:00-06:00
draft: false
---

# EF Core vs. Micro-ORM (Dapper)
EF Core abstracts SQL from the developer, but also has more overhead due to translating LINQ expressions to SQL and change tracking on entities.  Dapper is more lightweight and focuses on performance.

## Comparison
### EF Core  
&nbsp;    
```cs
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}
```
&nbsp;  
### Dapper  
&nbsp;    
```cs
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```
&nbsp;  
# SQL vs NoSQL
Relational databases (like SQL) map objects to tables and rows.  
NoSQL databases (like MongoDB or Azure Cosmos DB) serialize an object graph and store the result.  

## NoSQL
- Benefits:  
	- Simplicity
	- Performance
	- No locks or transactions allows for easy scaling across many machines
- Drawbacks
	- Address, and its associated Country, might be serialized as part of many stored objects.  An update to Address and/or Country would require all such objects to be updated rather than a single row.  
&nbsp;  
# Entity Framework (for relational databases)  
An object-relational mapper to persist objects to and from a data source.

## DbContext
This class contains properties representing collections of entities your application will work with.  
Its constructor must accept a DbContextOptions<T> and pass this to the base constructor.  Example from eShopOnWeb:  
&nbsp;    
```cs
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }

    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```  
&nbsp;  
## Configuring  
Add `CatalogContext` to the DI container and configure it to use a SQL Server database with a connection string defined in Configuration:  
&nbsp;    
```cs
builder.Services.AddDbContext<CatalogContext>(
    options => options.UseSqlServer(
        builder.Configuration.GetConnectionString("DefaultConnection")));
```
&nbsp; 
### Use the in-memory database:
&nbsp;    
```cs
builder.Services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```
&nbsp;  
## CRUD Operations on Data
To retrieve data, access the appropriate property and use LINQ to filter the result:  
&nbsp;  
```cs
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem { // Projects the result onto a SelectListItem type
        Value = b.Id, Text = b.Name })
    .ToListAsync(); // Execute the query immediately
```
&nbsp;  
Add an entity to persistence:  
&nbsp;    
```cs
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();
```
&nbsp;    
Update an entity in persistence:  
&nbsp;    
```cs
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();
```
&nbsp;  
Remove an entity from persistence:  
&nbsp;    
```cs
var brandToDelete = _context.Find<CatalogBrand>(2); // uses an alternate syntax for Find than above
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```
&nbsp;  
## Fetching Related Data
When EF Core retrieves an entity, it populates the properties that are stored with that entity in the database.  However, navigation properties, such as lists of related entities, are not populated and may be set to null.  To include these properties, use eager loading, which is done with the Include extension method on the query:  
&nbsp;    
```cs
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```
&nbsp;  
You can include subrelationships with ThenInclude.  EF Core executes this as a single query.  You can also use an overload of the Include extension method and pass a dot-separated string:  
&nbsp;    
```cs
.Include("Items.Products")
```

You can specify the sahpe of the data to be returned including which properties to populate:  
```cs
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```
&nbsp;  
Aside from eager loading, two other approaches are explicit loading and lazy loading.  Both should be avoided in web apps.  See https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications.

## Encapsulating Data
Domain models often expose collection navigation properties as publicly accessible list types.  This allows collaborators to manipulate the collection's contents.  To solve, expose read-only access to related collections and explicitly provide methods defining ways for clients to manipulate them:  
&nbsp;    
```cs
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly(); // The exposed IReadOnlyCollection wraps the underlying type.

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
    var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
    if (existingItem == null)
    {
        _items.Add(new BasketItem()
        {
        CatalogItemId = catalogItemId,
        Quantity = quantity,
        UnitPrice = unitPrice
        });
    }
    
    else 
    existingItem.Quantity += quantity;
    }
}
```
&nbsp;  
And tell EF Core to use the backing field:  
&nbsp;    
```cs
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```
&nbsp;  
You can also encapsulate data by using value objects for types that lack identity and are only distinguished by properties:  
&nbsp;    
```cs
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```
&nbsp;  
Consider that the `ShipToAddress` property is of type `Address.`  `Address` is a value object with several other properties (`Street`, `City`, etc).  EF Core maps the `Order` object to its table with one column per Address property and prefixes each column name with the name of the property.  The `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City.`  

# [Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/work-with-data-in-asp-net-core-apps#execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts)

# Other Persistence Options
4 Types of Azure Storage  
&emsp;1. Blob Storage — for unstructured text or binary data (object storage)  
&emsp;2. Table Storage — for structured datasets accessible via row keys  
&emsp;3. Queue Storage — for reliable queue-based messaging  
&emsp;4. File Storage — for shared file access between Azure VMs and on-prem apps  

# Caching
Caching is storing a copy of data on the server (or another more easily-queried data store).
ASP.NET Core supports response caching (caching entire pages) and data caching (more granular caching behavior).
Avoid implementing caching logic in your data access logic or your user interface (separation of concerns).  Encapsulate caching in its own classes and use configuration to manage its behavior.

## Response Caching
### First level of response caching
Adds HTTP headers that instruct clients and proxy servers to cache responses, but does not cache anything on the server itself.
Add the ResponseCache attribute to individual controllers or actions:  
&nbsp;  
```cs
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View(); // Adds this header to the response:  Cache-Control: public,max-age=60
}
```

### Second level of response caching
Cache responses on the server.  
Reference `Microsoft.AspNetCore.ResponseCaching` and add the Response Caching middleware:  
&nbsp; 
```cs
builder.Services.AddResponseCaching();

// other code omitted, including building the app

app.UseResponseCaching();
```
&nbsp;  
This will automatically cache responses based on a set of conditions.  
- By default, 200 (OK) responses via GET and HEAD methods are cached.  
&nbsp;  
More information:  https://learn.microsoft.com/en-us/aspnet/core/performance/caching/middleware#conditions-for-caching  
&nbsp;  
## Data Caching
You can cache the results of individual data queries.  Use either in-memory caching or a distributed cache.

Reference `Microsoft.Extensions.Caching.Memory` and add support for in-memory caching:  
&nbsp;  
```cs
builder.Services.AddMemoryCache();
builder.Services.AddMvc();

Request IMemoryCache via dependency injection to access the cache:
public class SomeClass {
    private readonly IMemoryCache _cache;
    
    public SomeClass(IMemoryCache cache) {
        _cache = cache;
    }
}
```
&nbsp;  
## Avoiding Stale Caches
When data has changed at the source but an out-of-date version remains in the cache, the cache is stale.  
This is avoided by:  
1. Using small cache durations (like 60 seconds)
2. Proactively removing cache entries when the data they contain is updated: `_cache.Remove(cacheKey);`  
&nbsp;  
If many different cache entries depend on a particular set of data, it may be useful to create dependencies between the entries using a `CancellationChangeToken`.  This allows you to expire multiple caches at once:  
&nbsp;  
```cs
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey, itemToCache, new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```
&nbsp;  
#   Getting Data to Blazor WASM Apps
This is generally done through web API endpoints.  See the BlazorAdmin project in eShopOnWeb.

