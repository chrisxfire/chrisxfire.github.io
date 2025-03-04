---
title: overview
date: 2023-08-03T00:00:00-06:00
draft: false
weight: -1
---

# abstract
> https://docs.microsoft.com/en-us/dotnet/core/extensions/dependency-injection-guidelines
> https://scottlilly.com/c-design-patterns-the-dependency-injection-pattern/
> https://auth0.com/blog/dependency-injection-in-dotnet-core/

*Dependency Injection* is a design pattern used to achieve Inversion of Control between classes and their dependencies.
*A dependency* is an object that another object depends on.

# ioc container
- Implements `IServiceProvider`
- Dependencies managed by this container are called *services*.
- `Microsoft.Extensions.DependencyInjection.IServiceCollection`.

## functions of the ioc container
- Registration — mapping a type to a class so that the IoC can create the correct dependency instance.
- Resolution — resolving dependencies by creating an object and injecting it into the requesting class.
- Disposition — managing the dependency's lifetime.

# two types of services
There are two types of services: 
1. *Framework-provided services* — provided by the .NET framework:
    | Service Type                                                                                                                                                               | Lifetime  |
    | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
    | [Microsoft.Extensions.DependencyInjection.IServiceScopeFactory](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.dependencyinjection.iservicescopefactory) | Singleton |
    | [IHostApplicationLifetime](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostapplicationlifetime)                                              | Singleton |
    | [Microsoft.Extensions.Logging.ILogger<TCategoryName>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.logging.ilogger-1)                                  | Singleton |
    | [Microsoft.Extensions.Logging.ILoggerFactory](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.logging.iloggerfactory)                                     | Singleton |
    | [Microsoft.Extensions.ObjectPool.ObjectPoolProvider](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.objectpool.objectpoolprovider)                       | Singleton |
    | [Microsoft.Extensions.Options.IConfigureOptions<TOptions>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.options.iconfigureoptions-1)                   | Transient |
    | [Microsoft.Extensions.Options.IOptions<TOptions>](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.options.ioptions-1)                                     | Singleton |
    | [System.Diagnostics.DiagnosticListener](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.diagnosticlistener)                                                 | Singleton |
    | [System.Diagnostics.DiagnosticSource](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.diagnosticsource)                                                     | Singleton |
2. *Application services* — services created by the developer; must be registered explicitly.

# adding dependencies
Use the `Add` method to register generic dependencies (application services):
```cs
public void ConfigureServices(IServiceCollection services) {
    services.Add(new ServiceDescriptor(typeof(ILog), new MyLogger()));
}
```
# service lifetimes
Services can be registered with one of these lifetimes: *Transient*, *Scoped*, *Singleton*

## transient
- DI container returns new instance of the service each time it is requested.
- Register services with AddTransient.
- In apps that process requests, transient services are disposed of at the end of the request.

## scoped
- In a web app, DI container returns same instance of service for multiple requests within the scope of a single HttpRequest (returns different instances across multiple HttpRequests).
- Register services with AddScoped.
- In apps that process requests, scoped services are disposed of at the end of the request.
- In EF Core, AddDbContext registers `DbContext` types with a scoped lifetime.

## singleton
- DI container returns the same instance of the service for all requests.
- All subsequent requests of the service from the DI container use the same instance.
- Register services with AddSingleton.
- The DI container disposes of Singleton lifetime services automatically. Services should never be disposed by code that resolved the service from the container.
- In apps that process requests, singleton services are disposed when the app is shutdown. Consider memory use.

## tryadd
Use TryAddLifetime to register the service only if there isn't already an implementation registered.

# service registration methods
Services can be registered the following ways:
<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 13%" />
<col style="width: 21%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Method</strong></th>
<th><p><strong>Automatic</strong></p>
<p><strong>object</strong></p>
<p><strong>disposal</strong></p></th>
<th><p><strong>Multiple</strong></p>
<p><strong>implementations</strong></p></th>
<th><strong>Pass args</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Add{<em>LIFETIME</em>}&lt;{<em>SERVICE</em>}, {<em>IMPLEMENTATION</em>}&gt;()</p>
<p></p>
<p>Example:</p>
<p><mark>services.AddSingleton&lt;IMyDep, MyDep&gt;();</mark></p></td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr class="even">
<td><p>Add{<em>LIFETIME</em>}&lt;{<em>SERVICE</em>}&gt;(sp =&gt; new {<em>IMPLEMENTATION</em>})</p>
<p></p>
<p>Examples:</p>
<p><mark>services.AddSingleton&lt;IMyDep&gt;(sp =&gt; new MyDep());</mark></p>
<p><mark>services.AddSingleton&lt;IMyDep&gt;(sp =&gt; new MyDep(99));</mark></p></td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td><p>Add{<em>LIFETIME</em>}&lt;{<em>IMPLEMENTATION</em>}&gt;()</p>
<p></p>
<p>Example:</p>
<p><mark>services.AddSingleton&lt;MyDep&gt;();</mark></p></td>
<td>Yes</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="even">
<td><p>AddSingleton&lt;{<em>SERVICE</em>}&gt;(new {<em>IMPLEMENTATION</em>})</p>
<p></p>
<p>Examples:</p>
<p><mark>services.AddSingleton&lt;IMyDep&gt;(new MyDep());</mark></p>
<p><mark>services.AddSingleton&lt;IMyDep&gt;(new MyDep(99));</mark></p></td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td><p>AddSingleton(new {<em>IMPLEMENTATION</em>})</p>
<p></p>
<p>Examples:</p>
<p><mark>services.AddSingleton(new MyDep());</mark></p>
<p><mark>services.AddSingleton(new MyDep(99));</mark></p></td>
<td>No</td>
<td>No</td>
<td>Yes</td>
</tr>
</tbody>
</table>

# dependency injection chaining
This is common.
Each requested dependency in turn requests its own dependencies.
The DI container resolves the dependencies in a graph and returns the fully resolved *service*. This is an *object graph*.

# constructor injection
Constructors can accept arguments that are not provided by DI, but the arguments must assign default values.
Services resolved by `IServiceProvider` or `ActivatorUtilities` require a public constructor.

# multiple constructor discovery
When a type has more than one constructor, the service provider determines which constructor to use.
The constructor with the most parameters where the types are DI-resolvable is selected.

For example, if logging has been added and is resolvable from the service provider, but FooService and BarService are not, the highlighted constructor is chosen:
```cs
public class ExampleService 
{
    public ExampleService() { }

    public `ExampleService(ILogger<ExampleService> logger)` 
    { // omitted for brevity
    }

    public ExampleService(FooService fooService, BarService barService) 
    { // omitted for brevity
    }
}
```
If there is ambiguity when discovering constructors, an exception is thrown.

# disposal of services
The DI container disposes services itself. Services resolved from the container must never be disposed by the developer.
