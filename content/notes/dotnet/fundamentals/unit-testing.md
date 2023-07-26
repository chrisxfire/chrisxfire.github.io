---
title: notes > .net > fundamentals > unit testing
date: 2023-05-04T00:00:00-06:00
draft: false
weight: 1
---

# C# Unit Testing Frameworks
- MS Test
- NUnit
- xUnit.net

# Process (Using Visual Studio)
Create a Testing project as a separate project from the main project:
```cs
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Project;		// This is the name of the project namespace.

namespace ProjectTests;	// This is the name of the project namespace + "Tests".

[TestClass]
public class UnitTest1 
{	
	[TestMethod]
	public void TestMethod1() 
    {
		var testInstance = ProjectClass();	// The name of the project class you are testing.
		var testResult = testInstance.ClassMethod(…);	// The name of the class method you are testing.
		Assert.AreEqual(expectedOutput, testResult, "Expect: expectedOutput\nActual: testResult");
	}
}
```

Run all tests.  VS opens Test Explorer window.

# Mocking
Isolate your test by mocking parts of your code that don't affect the test outcome. This is useful when your code cannot be further modularized or you do not want to rewrite it so.

Frameworks: 
- [MOQ](https://github.com/Moq/moq4/wiki/Quickstart)
- [Microsoft Fakes](https://docs.microsoft.com/en-us/visualstudio/test/isolating-code-under-test-with-microsoft-fakes) (requires VS Enterprise) 
  - ([full tutorial](https://docs.microsoft.com/en-us/visualstudio/test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing))

Test methods created in Xunit must be public.

## Unit Testing with Xunit and Moq
1. `dotnet new xunit`
2. `dotnet add project moq` (in xunit project)
3. In xunit project, add project reference to code project
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

# [Fluent Assertions](https://fluentassertions.com/)
Assert statements that are more human-readable.

```cs
using FluentAssertions;
// ...

[TestMethod]
public void AddTestFluentassertion()
{
    var calculator = new Calculator();
    var actual = calculator.Add(1, 1);

    // Non-fluent asserts:
    // Assert.AreEqual(actual, 2);
    // Assert.AreNotEqual(actual, 1);

    // Same asserts as what is commented out above, but using Fluent Assertions
    actual.Should().Be(2).And.NotBe(1);
}
```

# [Data-driven Tests](https://docs.microsoft.com/en-us/visualstudio/test/how-to-create-a-data-driven-unit-test)
AKA parameterized testing. Run the same test repeatedly with different parameters.  
```cs
[DataTestMethod]
[DataRow(1, 1, 2)]
[DataRow(2, 2, 4)]
[DataRow(3, 3, 6)]
[DataRow(0, 0, 1)] // The test run with this row fails
public void AddDataTests(int x, int y, int expected)
{
    var calculator = new Calculator();
    var actual = calculator.Add(x, y);
    Assert.AreEqual(expected, actual);
}
```