---
title: overview
date: 2023-10-22T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/)]  

Unit testing:
* reduces the amount of time needed to perform *functional* tests, which require running the application and performing a series of steps.
* protects against regression.
* serves as executable documentation.
* helps ensure code is less coupled.

Good unit tests are fast (run in milliseconds), isolated (have no dependencies), repeatable (always return the same results), 
self-checking (identify whether they pass or fail), and timely (shouldn't take a disproportionately long time to write).

# Mock vs Fake vs Stub
* *Fake* — a generic term for either a mock or stub object.
* *Mock* — a fake object that decides whether or not a unit test has passed or failed. It starts out as a fake until it is asserted
against. 
* *Stub* — a controllable replacement for an existing dependency. They start out as fakes.

Consider:
```cs
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Above, this a *stub*, even though it is referred to as a *mock*. It's a stub because an Order is only being passed in to create 
a Purchase, which is the system under test.

Instead of the above, consider:
```cs
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

The class `MockOrder` is renamed to `FakeOrder`, and so it can be used as either a mock or a stub. Above, stubOrder is not asserted
against, which is what makes it a stub.

# Mocking
Isolate your test by mocking parts of your code that don't affect the test outcome. This is useful when your code cannot be further modularized or you do not want to rewrite it so.

Frameworks: 
- [MOQ](https://github.com/Moq/moq4/wiki/Quickstart)
- [Microsoft Fakes](https://docs.microsoft.com/en-us/visualstudio/test/isolating-code-under-test-with-microsoft-fakes) (requires VS Enterprise) 
  - ([full tutorial](https://docs.microsoft.com/en-us/visualstudio/test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing))

Test methods created in XUnit must be public.

# Order of Unit Tests [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/order-unit-tests?pivots=mstest)]  

MSTest unit tests are automatically ordered alphabetically by test name. See documentation for ordering of other tests in other testing frameworks.

# Running Subsets of Unit Tests [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/selective-unit-tests?pivots=mstest)]  

MSTest unit tests can be assigned categories and/or priorities which allow them to be filtered. See documentation for running subsets of unit tests
in other testing frameworks.

# Testing Published Output [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-published-output)]  

Use `dotnet vstest TestProject.dll`.

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