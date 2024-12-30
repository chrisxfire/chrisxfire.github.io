---
title: integration testing
date: 2023-11-05T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0)  

Integration tests confirm that two or more app components work together to produce an expected result, possibly including every component required to fully process a request.
They test the app's infrastructure including database, file system, network appliances, and the request-response pipeline. They use the app's actual components instead of mocks
or fakes. 

<g>Tip</g>: Separate unit tests from integration tests in separate projects.

In ASP.NET integration tests:
* The test project has a reference to the system under test.
* The test project creates a test web host for the SUT and uses a test server client to handle requests and responses with the SUT.
* Reference `Microsoft.AspNetCore.Mvc.Testing` to provide:
  * Copies the dependencies file (`.deps`) from the SUT into the test project's `/bin` directory.
  * Set the content root to the SUT's project root.
  * Provide a `WebApplicationFactory` to bootstrap the SUT with a `TestServer`.
* Reference `Microsoft.NET.Sdk.Web`
* Follow this pattern:
  * *Initialize*
    * The SUT's web host is configured.
      * In this step, a different database or perhaps different app settings may be used.
    * A test server client is created that submits requests to the app.
  * *Arrange* — The test app prepares a request.
  * *Act* — The client submits the request and receives a response.
  * *Assert* — The actual response is compared to the expected response.

## razor pages app tests vs mvc app tests
Tests of these two apps are the same — the only thing that differs is how the tests are named.

# example 
> Sample code: https://github.com/dotnet/AspNetCore.Docs.Samples/tree/main/test/integration-tests/IntegrationTestsSample

This example uses xUnit.

```cs
// Inheriting from IClassFixture defines the class as containing tests in xUnit:
public class BasicTests : IClassFixture<WebApplicationFactory<Program>>
{
    // WebApplicationFactory<TEntryPoint> creates a TestServer; TEntryPoint is the entry point for the SUT.
    // The WebApplicationFactory will also provide an HttpClient to the test method:
    private readonly WebApplicationFactory<Program> _factory;

    public BasicTests(WebApplicationFactory<Program> factory) => _factory = factory;

    [Theory]
    // Each of these pages will be tested in this test:
    [InlineData("/")]
    [InlineData("/Index")]
    [InlineData("/About")]
    [InlineData("/Privacy")]
    [InlineData("/Contact")]
    public async Task Get_EndpointsReturnSuccessAndCorrectContentType(string url)
    {
        // Arrange
        var client = _factory.CreateClient();

        // Act
        var response = await client.GetAsync(url);

        // Assert
        response.EnsureSuccessStatusCode(); // Status Code 200-299
        Assert.Equal("text/html; charset=utf-8", response.Content.Headers.ContentType.ToString());
    }
}
```

# antiforgery checks
There are two approaches for antiforgery checks:
1. Lower level approach: use Application Parts to inject a controller or Razor Page into the app to make JSON requests for the required values. See [this blog post](https://blog.martincostello.com/integration-testing-antiforgery-with-application-parts/) for details.
2. High level approach: use the [AngleSharp](https://anglesharp.github.io/) parser to conduct antiforgery checks and parsing the HTML. 

# webapplicationfactory
For tests with the default `WebApplicationFactory`, expose the implicit `Program` class by updating the SUT's project file:
```xml
<ItemGroup>
    <InternalsVisibleTo Include="MyTestProject" />
</ItemGroup>
```

## customizing webapplicationfactory
Web host configuration can also be created independently of the test classes by 
1. Inheriting `WebApplicationFactory` and overriding `ConfigureWebHost`:
    ```cs
    public class CustomWebApplicationFactory<TProgram> : WebApplicationFactory<TProgram> where TProgram : class
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            // This callback is executed after the SUT's Program.cs code is executed:
            builder.ConfigureServices(services =>
            {
                // Find the service descriptor for the database context and database connection and remove them:
                var dbContextDescriptor = services.SingleOrDefault(d => d.ServiceType == typeof(DbContextOptions<ApplicationDbContext>));

                services.Remove(dbContextDescriptor);

                var dbConnectionDescriptor = services.SingleOrDefault(d => d.ServiceType == typeof(DbConnection));

                services.Remove(dbConnectionDescriptor);

                // Create open SqliteConnection so EF won't automatically close it:
                services.AddSingleton<DbConnection>(container =>
                {
                    var connection = new SqliteConnection("DataSource=:memory:");
                    connection.Open();

                    return connection;
                });

                services.AddDbContext<ApplicationDbContext>((container, options) =>
                {
                    var connection = container.GetRequiredService<DbConnection>();
                    options.UseSqlite(connection);
                });
            });

            builder.UseEnvironment("Development");
        }
    }
    ```

2. Use the `CustomWebApplicationFactory` in test classes:
    ```cs
    public class IndexPageTests : IClassFixture<CustomWebApplicationFactory<Program>>
    {
        private readonly HttpClient _client;
        private readonly CustomWebApplicationFactory<Program> _factory;

        public IndexPageTests(CustomWebApplicationFactory<Program> factory)
        {
            _factory = factory;
            _client = factory.CreateClient(new WebApplicationFactoryClientOptions
            {
                // The HttpClient is prevented from following redirects. This allows tests to check the result of the
                // app's first response:
                AllowAutoRedirect = false
            });
        }
    ```
3. Here's a typical test:
    ```cs
    [Fact]
    public async Task Post_DeleteAllMessagesHandler_ReturnsRedirectToRoot()
    {
        // Arrange
        var defaultPage = await _client.GetAsync("/");
        var content = await HtmlHelpers.GetDocumentAsync(defaultPage);

        //Act
        var response = await _client.SendAsync(
            (IHtmlFormElement)content.QuerySelector("form[id='messages']"),
            (IHtmlButtonElement)content.QuerySelector("button[id='deleteAllBtn']"));

        // Assert
        Assert.Equal(HttpStatusCode.OK, defaultPage.StatusCode);
        Assert.Equal(HttpStatusCode.Redirect, response.StatusCode);
        Assert.Equal("/", response.Headers.Location.OriginalString);
    }
    ```

# other topics
## [Customizing the Client with WithWebHostBuilder](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#customize-the-client-with-withwebhostbuilder)

## [Using WebApplicationFactoryClientOptions](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#client-options)

## [Injecting Mock Services](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#inject-mock-services)

## [Mock Authentication](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#mock-authentication)

## [Setting the Environment](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#set-the-environment)

## [Integration Tests Sample](https://learn.microsoft.com/en-us/aspnet/core/test/integration-tests?view=aspnetcore-7.0#integration-tests-sample)