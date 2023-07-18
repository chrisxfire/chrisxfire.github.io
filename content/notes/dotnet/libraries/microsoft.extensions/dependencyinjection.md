---
title: notes > .net > libraries > microsoft.extensions > dependencyinjection
date: 2022-08-23T16:03:38-0600
draft: false
weight: 1
---
# Dependency Injection with Generic Host & Default HostBuilder
## Example With a Hosted Service
```cs
public class Program 
{
    public static async Task Main(string[] args) 
    {
        await Host.CreateDefaultBuilder(args)
        // Set the ContentRoot to the path of the executing assembly:
            .UseContentRoot(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location))
            .ConfigureServices((hostContext, services) => 
            {
            services
            .AddHostedService<ConsoleService>();
            // IHostedService has full access to the DI container:
            .AddSingleton<IWeatherService, WeatherService>();

            services.AddOptions<WeatherSettings>()
            .Bind(hostContext.Configuration.GetSection("Weather"));
        })
        .RunConsoleAsync();
    }
}

internal sealed class ConsoleHostedService : IHostedService
{
    private int? _exitCode;
    private readonly ILogger _logger;
    private readonly IHostApplicationLifetime _appLifetime;
    private readonly IWeatherService _weatherService;

    public ConsoleHostedService(
        ILogger<ConsoleHostedService> logger,
        IHostApplicationLifetime appLifetime,
        IWeatherService weatherService)
    {
        _logger = logger;
        _appLifetime = appLifetime;
        _weatherService = weatherService;
    }

    public Task StartAsync(CancellationToken cancellationToken)
    {
        _appLifetime.ApplicationStarted.Register(() =>
        {
            Task.Run(async () =>
            {
                try
            {
                IReadOnlyList<int> temperatures = _weatherService.GetFiveDayTemperaturesAsync();
                _exitCode = 0;
            }
            catch (Exception ex)
            {
                _exitCode = 1;
            }
            finally
            {
                // Stop the application once the work is done
                _appLifetime.StopApplication();
            }
            });
        });

    return Task.CompletedTask;
    }

    public Task StopAsync(CancellationToken cancellationToken)
    {
        // Optionally, you can set the exit code here:
        Environment.ExitCode = _exitCode.GetValueOrDefault(-1);

        return Task.CompletedTask;
    }
}
```
`WeatherService.cs`
```cs
internal sealed class WeatherService : IWeatherService
{
    private readonly ILogger<WeatherService> _logger;
    private readonly IOptions<WeatherSettings> _weatherSettings;

    public WeatherService(ILogger<WeatherService> logger, IOptions<WeatherSettings> weatherSettings)
    {
        _logger = logger;
        _weatherSettings = weatherSettings;
    }

    public async Task<IReadOnlyList<int>> GetFiveDayTemperaturesAsync(CancellationToken cancellationToken)
    {
        _logger.LogInformation("Fetching weather...");

        // Simulate some network latency
        await Task.Delay(2000, cancellationToken);

        int[] temperatures = new[] { 76, 76, 77, 79, 78 };
        if (_weatherSettings.Value.Unit.Equals("C", StringComparison.OrdinalIgnoreCase))
        {
            for (int i = 0; i < temperatures.Length; i++)
            {
                temperatures[i] = (int)Math.Round((temperatures[i] - 32) / 1.8);
            }
        }

        _logger.LogInformation("Fetched weather successfully");
        
        return temperatures;
    }
}
```
`WeatherSettings.cs`
```cs
internal sealed class WeatherSettings
{
    public string Unit { get; set; }
}
```

`appsettings.Json`
```json
{
    "Logging": 
    {
        "LogLevel": 
        {
            "Default": "Debug",
            // Avoid logging lifetime events
            "Microsoft.Hosting.Lifetime": "Warning",
            // Avoid logging Host internal events
            "Microsoft.Extensions.Hosting.Internal.Host": "Warning"
        }
    },
    "Weather": 
    {
        "Unit": "C"
    }
}
```
