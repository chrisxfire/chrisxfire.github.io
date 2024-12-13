---
title: unit testing with mstest
date: 2023-10-22T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-mstest)]   [[Documentation](https://learn.microsoft.com/en-us/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests?view=vs-2022  )  
> See also: https://github.com/microsoft/testfx/blob/main/docs/README.md  

MSTest unit tests are created with `dotnet new mstest -o TestProjectName`.

# MSTest Attributes
## `TestClass` and `TestMethod`
The `TestClass` attribute declares a class that contains unit tests and, optionally, initialization or cleanup methods.
The `TestMethod` attribute declares a test method. Test methods must:
  - be `public void` or `public Task` or `public async Task`
  - be parameterless 

Unit tests projects can contain other classes that do not have the `[TestClass]` attribute, and test classes can contain 
other methods that do not have the `[TestMethod]` attribute. Test methods can call these other classes and methods.

```cs
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services;

[TestClass]
public class PrimeService_IsPrimeShould
{
    private readonly PrimeService _primeService;

    public PrimeService_IsPrimeShould()
    {
        _primeService = new PrimeService();
    }

    [TestMethod]
    public void IsPrime_InputIs1_ReturnFalse()
    {
        bool result = _primeService.IsPrime(1);

        Assert.IsFalse(result, "1 should not be prime");
    }
}
```

## `DataRow`
The values of the `DataRow` attributes are passed to the `value` parameter of the test method:
```cs
[TestMethod]
[DataRow(-1)]
[DataRow(0)]
[DataRow(1)]
public void IsPrime_ValuesLessThan2_ReturnFalse(int value)
{
    var result = _primeService.IsPrime(value);

    Assert.IsFalse(result, $"{value} should not be prime");
}
```

The number and types of arguments to the attribute must match the test method signature:
```cs
[TestClass]
public class TestClass
{
    [TestMethod]
    // Setting the DisplayName property modifies the display name in Visual Studio and in loggers:
    [DataRow(1, "message", true, 2.0), DisplayName="Functional Case FC01"]
    public void TestMethod1(int i, string s, bool b, float f) {}
    
    [TestMethod]
    [DataRow(new string[] { "line1", "line2" })]
    public void TestMethod2(string[] lines) {}

    [TestMethod]
    [DataRow(null)]
    public void TestMethod3(object o) {}

    [TestMethod]
    [DataRow(new string[] { "line1", "line2" }, new string[] { "line1.", "line2." })]
    public void TestMethod4(string[] input, string[] expectedOutput) {}
}
```

Also, `params` can be used to capture multiple inputs of `DataRow`:
```cs
[TestMethod]
[DataRow(1, 2, 3, 4)]
public void TestMethod(params int[] values) {}
```

## Attributes for Initialization and Cleanup
Unless otherwise noted, all methods marked with these attributes:
- Must be `static void` or `static Task` or `static async Task`
- Can appear only once
- Must be in a `TestClass`

| Attribute              | When is method called                                             | Parameters  | Comments                                                                                                                                                                                                                                      |
| ---------------------- | ----------------------------------------------------------------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[AssemblyInitialize]` | Right after assembly is loaded                                    | TestContext | N/A                                                                                                                                                                                                                                           |
| `[AssemblyCleanup]`    | Right before assembly is unload                                   | N/A         | N/A                                                                                                                                                                                                                                           |
| `[ClassInitialize]`    | Right before the class is loaded but after the static constructor | TestContext | N/A                                                                                                                                                                                                                                           |
| `[ClassCleanup]`       | Right after the class is unloaded                                 | N/A         | N/A                                                                                                                                                                                                                                           |
| `[TestInitialize]`     | Right before the test is started                                  | N/A         | More suitable for long or async initializations than the class initializer. <br /> Always called after the class constructor and always called for each test, including each data row of data-driven tests. <br /> May appear more than once. |
| `[TestCleanup]`        | Right after the test is finished                                  | N/A         | More suitable for long or async cleanups than the class cleanup. <br /> Always called just before the `Dispose{Async}` and always called for each test, including each data row of data-driven tests. <br /> May appear more than once.       |

```cs
[TestClass]
public class MyTestClass
{
    [AssemblyInitialize]
    public static void AssemblyInitialize(TestContext testContext) { }

    [AssemblyCleanup]
    public static void AssemblyCleanup() { }

    [ClassInitialize]
    public static async Task ClassInitialize(TestContext testContext) { }

    [ClassCleanup]
    public static async Task ClassCleanup() { }

    [TestInitialize]
    public async Task TestInitialize() { }

    [TestCleanup]
    public async Task TestCleanup() { }
}
```

## `TestContext` Class
These attributes appear in the Visual Studios Properties window of a particular test method. They are not meant to be
accessed through the code of a unit test. They are used to provide metadata for the test:
- `OwnerAttribute`
- `DescriptionAttribute`
- `IgnoreAttribute`
- `PriorityAttribute`
- `TestPropertyAttribute`
- `WorkItemAttribute`

## `DeploymentItemAttribute`
For deployment items, without a custom output path, the copied files will be in the TestResults folder inside the project 
folder. `[DeploymentItem]` copies files or folders specified as deployment items to the deployment directory. It can be used
on `[TestClass]`'s or `[TestMethod]`'s:
```cs
[TestClass] 
[DeploymentItem(@"C:\classLevelDepItem.xml")]   // Copy file using some absolute path
public class UnitTest1
{
    [TestMethod]
    [DeploymentItem(@"..\..\methodLevelDepItem1.xml")]   // Copy file using a relative path from the dll output location
    [DeploymentItem(@"C:\DataFiles\methodLevelDepItem2.xml", "SampleDataFiles")]   // File will be added under a SampleDataFiles in the deployment directory
    public void TestMethod1()
    {
        string textFromFile = File.ReadAllText("classLevelDepItem.xml");
    }
}
```

## `PrivateObject` and `PrivateType`
When generating a unit test for a private method, a private accessor class is generated, which instantiates a 
`PrivateObject`. This is a wrapper class that uses reflection as part of the private accessor process.

`PrivateType` is used for calling private static methods (instead of private instance methods).

[More information](https://learn.microsoft.com/en-us/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests?view=vs-2022#classes-used-with-private-accessors).

# Unit Test Timeouts
MSTest unit tests can be configured with a timeout:
```cs
[TestMethod]
[Timeout(2000)]  // Milliseconds
// Or, for the maximum allowed time:
[Timeout(TestTimeout.Infinite)]
public void My_Test() { /*...*/ }
```

# Assert Classes [[Documentation](https://learn.microsoft.com/en-us/visualstudio/test/using-the-assert-classes?view=vs-2022)]  

`Microsoft.VisualStudio.TestTools.UnitTesting` contains [Assert](https://learn.microsoft.com/en-us/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert?view=visualstudiosdk-2022) 
classes to verify specific functionality. A unit test only reports correctness of the code's behavior if Assert statements are included. 

| Class                         | Use                                                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `CollectionAssert`            | Compare collections of objects <br /> Verify the state of a collection                                                                       |
| `StringAssert`                | Compare and examine strings <br /> ie: `Contains`, `Matches`, `StartsWith`                                                                   |
| `AssertFailedException`       | Thrown whenever a test fails. <br /> A failure is a test timeout, unexpected exception, or an assert statement that produces a Failed result |
| `AssertInconclusiveException` | Thrown whenever a test produces a result of Inconclusive. <br /> Added to tests not yet ready to be run (still being developed).             |
| `Assert.ThrowException`       | Asserts that an exception you expect to be thrown by a method is actually thrown                                                             |