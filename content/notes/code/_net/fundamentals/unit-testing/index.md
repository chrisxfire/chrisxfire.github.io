---
title: notes > code > .net > fundamentals > unit testing
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

# Unit Testing with Xunit and Moq
Test methods created in Xunit must be public.

## Process
### 1. `dotnet new xunit`
### 2. `dotnet add project moq` (in xunit project)
### 3. In xunit project, add project reference to code project
### 4. Create the necessary mocks (like `PieRepository`, `CategoryRepository`) with `moq.Mock` static method:
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
### 5. Write the tests
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

### 6. Run the tests:  `dotnet test` or **Tests** > **Run All Tests**
