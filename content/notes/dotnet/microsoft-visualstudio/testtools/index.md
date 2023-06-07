---
title: "notes > dotnet > microsoft visualstudio > testtools"
date: 2022-04-08T14:52:24-0600
draft: false
---

# Unit Tests
```cs
using Microsoft.VisualStudio.TestTools.UnitTesting; // The unit testing framework.
using LearnMyCalculatorApp; // The namespace of the app being tested.

[TestClass]
public class CalculatorTests
{
    [TestMethod]
    public void CalculatorNullTest()
    {
        var calculator = new Calculator();
        Assert.IsNotNull(calculator); // Test by using assertions.
    }
}

// Assuming the Calculator class has an Add(int, int) method, this is a test for it:
[TestMethod]
public void AddTest()
{
    // Arrange
    var calculator = new Calculator();

    // Act
    var actual = calculator.Add(1, 1);
    var subtractActual = calculator.Subtract(actual, 1) == 1;

    // Assert
    Assert.IsNotNull(calculator);
    Assert.AreEqual(2, actual); // Check if two objects or values are equal.
    Assert.IsTrue(subtractActual);
    StringAssert.Contains(actual.ToString(), "2"); // Check if the string contains the substring.
}
```

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
`
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

# Mocking
Isolate your test by mocking parts of your code that don't affect the test outcome. This is useful when your code cannot be further modularized or you do not want to rewrite it so.

Frameworks: 
- [MOQ](https://github.com/Moq/moq4/wiki/Quickstart)
- [Microsoft Fakes](https://docs.microsoft.com/en-us/visualstudio/test/isolating-code-under-test-with-microsoft-fakes) (requires VS Enterprise) 
  - ([full tutorial](https://docs.microsoft.com/en-us/visualstudio/test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing))