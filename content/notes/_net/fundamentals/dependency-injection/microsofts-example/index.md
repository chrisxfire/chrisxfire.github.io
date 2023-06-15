---
title: notes > .net > fundamentals > dependency injection > microsofts example
date: 2022-08-26T07:34:23-0600
draft: false
---
# Dependent Service Implementation Example
```cs
public class MessageWriter 
{
    public void WriteMessage(string message) =>
    Console.WriteLine($"MessageWriter.WriteMessage called. Message: {message}");
}
```
If a class creates an instance of `MessageWriter` then, `MessageWriter` becomes a dependency of that class:
```cs
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```
`Worker` creates, and directly depends on, `MessageWriter`. This is problematic because:
- To replace `MessageWriter` with another implementation, you must also modify `Worker`.
- If `MessageWriter` has dependencies, they must also be configured in `Worker`.
- The implementation is difficult to unit test.

Dependency Injection addresses these problems by:
- Using an interface or base class to abstract the dependency implementation.
- Registering the dependency in a service container.
  - In .NET, this is IServiceProvider.
  - Services are typically registered at app startup and appended to an IServiceCollection.
  - Once all services are added, BuildServiceProvider is used to create the service container.
- Injecting the service into the constructor of the class where it is used.

# Non-Dependent Service Implementation Example
Consider this implementation instead:
```cs
`IMessageWriter.cs`:
public interface IMessageWriter 
{
    void Write(string message);
}

// The concrete type `MessageWriter` implements this interface:
public class MessageWriter : IMessageWriter 
{
    public void Write(string message) => Console.WriteLine($"Message: {message}");
}
```
`Worker.cs`:
```cs
public class Worker : BackgroundService 
{
    private readonly IMessageWriter _messageWriter;
    // This is *injection* of the *dependency*. The dependency is injected into the constructor of the class
    // where it's used:
    public Worker(IMessageWriter messageWriter) => _messageWriter = messageWriter;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken) 
    {
        while (!stoppingToken.IsCancellationRequest)
        {
            _messageWriter.Write($"Worker service running.");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```
`Program.cs`:
```cs
var builder = Host.CreateDefaultBuilder(args); // The HostBuilder with a default configuration.

builder.ConfigureServices(
    services =>
    services
    // Add the worker as a hosted service:
    .AddHostedService<Worker>()
    // Add the IMessageWriter interface as a scoped service with a corresponding concrete class:
    .AddScoped<IMessageWriter, MessageWriter>());

var host = builder.Build();

host.Run();
```

Notes:
- The `Worker` services does not create an instance of `MessageWriter`. The instance is created by the DI container.
- The DI container also disposes of this instance when it is no longer used.
- Because the worker service uses the interface, not the concrete type, this makes it easy to change the implementation that the controller uses without modifying the controller.

If another implementation of `IMessageWriter`, say, `LoggingMessageWriter`, were created…
`IMessageWriter.cs`:
```cs
public class LoggingMessageWriter : IMessageWriter 
{
    private readonly ILogger<LoggingMessageWriter> _logger;

    // This method depends on `ILogger<T>` (which is a framework-provided service), so it is injected into its
    // constructor. The service is automatically registered with CreateDefaultBuilder.
    public LoggingMessageWriter(ILogger<LoggingMessageWriter> logger) =>
    _logger = logger;

    public void Write(string message) =>
    _logger.LogInformation(message);
}
```

…the ConfigureServices method would simply have to register this new implementation:
`Program.cs`:
```cs
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
    .ConfigureServices((_, services) =>
    services.AddHostedService<Worker>()
    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```
