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

# Unit Testing with XUnit and Moq
1. `dotnet new XUnit`
2. `dotnet add project moq` (in XUnit project)
3. In XUnit project, add project reference to code project
4. Create the necessary mocks (like `PieRepository`, `CategoryRepository`) with `moq.Mock` static method:
    ```cs
    public class RepositoryMocks 
    {
        public static Mock<IPieRepository> GetPieRepository()
        {
            var pies = new List<Pie>()
            {
                new Pie() { … },
                …
            }

            var mockPieRepository = new Mock<IPieRepository>();

            // Mock _pieRepository.AllPies call
            mockPieRepository.Setup(repo => repo.AllPies).Returns(pies);

            // Mock _pieRepository.PiesOfTheWeek call
            mockPieRepository.Setup(repo => repo.PiesOfTheWeek).Returns(pies.Where(p => p.IsPieOfTheWeek));

            // Mock _pieRepository.GetPieById(int) call by confirming the parameter is an int and returning pies[0]:
            mockPieRepository.Setup(repo => repo.GetPieById(It.IsAny<int>())).Returns(pies[0]);

            return mockPieRepository;
        }
    }
    ```
5. Write the tests
    ```cs
    public class PieControllerTests
    {
    [Fact] // define this method as a fact that should be run by the test runner
    public void List_EmptyCategory_ReturnAllPies()
    {
        // arrange:
        var mockPieRepository = RepositoryMocks.GetPieRepository();
        var mockCategoryRepository = RepositoryMocks.GetCategoryRepository();

        var mockPieController = new PieController(mockPieRepository.Object, mockCategoryRepository.Object);

        // act:
        var result = mockPieController.List("");

        // assert:
        // assert that the return value is of type ViewResult
        var viewResult = Assert.IsType<ViewResult>(result);

        // assert that the passed in viewmodel is of type PieListViewModel
        var pieListViewModel = Assert.IsAssignableFrom<PieListViewModel>(viewResult.ViewData.Model);

        // assert there are exactly 10 pies in the PieListViewModel
        Assert.Equal(10, pieListViewModel.Pies.Count());
    }
    }
    ```

6. Run the tests:  `dotnet test` or **Tests** > **Run All Tests**
