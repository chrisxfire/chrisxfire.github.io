---
title: unit testing with nunit
date: 2023-10-22T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-nunit)  
> See also: https://docs.nunit.org/articles/nunit/intro.html

NUnit unit tests are created with `dotnet new nunit -o TestProjectName`.

Note: NUnit still uses `Setup` and `Teardown` methods, which is no longer considered best practice.

# nunit attributes
see inline comments.

```cs
using NUnitFramework; 

namespace Prime.UnitTests.Services;

[TestFixture] // Declares a class that contains unit tests.
public class PrimeService_IsPrimeShould
{
    private PrimeService _primeService;

    [SetUp] // Equivalent to a test class constructor.
    public void SetUp()
    {
        _primeService = new PrimeService();
    }

    [Test] // Declares a test method.
    public void IsPrime_InputIs1_ReturnFalse()
    {
        var result = _primeService.IsPrime(1);

        Assert.IsFalse(result, "1 should not be prime");
    }

    // The values of the TestCase attributes are passed to the value parameter of this test method.
    [TestCase(-1)]
    [TestCase(0)]
    [TestCase(1)]
    public void IsPrime_ValuesLessThan2_ReturnFalse(int value)
    {
        var result = _primeService?.IsPrime(value);

        Assert.IsFalse(result, $"{value} should not be prime");
    }
}
```

See [here](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) for a complete code sample.