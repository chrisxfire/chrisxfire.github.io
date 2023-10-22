---
title: unit testing with xunit
date: 2023-10-22T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-dotnet-test
> See also: https://xunit.net/#documentation

xUnit unit tests are created with `dotnet new xunit -o TestProjectName`.

# xUnit Attributes
## `Fact`
Used to declare a test method that is run by the test runner:
```cs
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services;

public class PrimeService_IsPrimeShould
{
    [Fact]
    public void IsPrime_InputIs1_ReturnFalse()
    {
        var primeService = new PrimeService();
        bool result = primeService.IsPrime(1);

        Assert.False(result, "1 should not be prime");
    }
}
```

## `Theory` and `InlineData`
These attributes work together to test multiple values. Instead of the above `IsPrime_InputIs1_ReturnFalse` method, consider:
```cs
namespace Prime.UnitTests.Services;

public class PrimeService_IsPrimeShould
{
    private readonly PrimeService _primeService;

    public PrimeService_IsPrimeShould() // <-- Test class constructor
    {
        _primeService = new PrimeService();
    }

    [Theory]
    [InlineData(-1)]
    [InlineData(0)]
    [InlineData(1)]
    // These attributes pass the values in the InlineData attributes to the value parameter of the test method:
    public void IsPrime_ValuesLessThan2_ReturnFalse(int value)
    {
        var result = _primeService.IsPrime(value);

        Assert.False(result, $"{value} should not be prime");
    }
}
```

See [here](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) for a complete code sample.
