---
title: best practices
date: 2023-10-22T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices)  

Use these best practices when developing unit tests.

## avoid dependencies in unit tests
Use dependency injection and the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle).

## naming tests
Tests should have a 3-part name: {MethodBeingTested}{ScenarioToTest}{ExpectedBehavior}. Consider:

<r>Bad</r>:

```cs
[Fact]
public void Test_Single() { /* ... */ }
```

<g>Good</g>:

```cs
public void Add_SingleNumber_ReturnsSameNumber() { /* ... */ }
```

## Arrange, Act, Assert
1. *Arrange* the objects by creating them and setting them up as necessary.
2. *Act* on an object.
3. *Assert* that something is expected.

Consider:
```cs
[Fact]
public void Add_EmptyString_ReturnsZero()
{
    // Arrange
    var stringCalculator = new StringCalculator();

    // Act
    var actual = stringCalculator.Add("");

    // Assert
    Assert.Equal(0, actual);
}
```

## Avoid Multiple 'Act's
One act per test makes it clear which act is failing and ensures the test is only focused on a single case.

## write minimally passing tests
The input to the unit test should be the simplest possible input that verifies the expected behavior.  
For example, use 0 as input to some method instead of some other number when 0 would verify the behavior of that method.

## avoid magic strings
Use constants instead.  
<r>Bad</r>:

```cs
[Fact]
public void Add_BigNumber_ThrowsException()
{
    var stringCalculator = new StringCalculator();

    Action actual = () => stringCalculator.Add("1001");

    Assert.Throws<OverflowException>(actual);
}
```

<g>Good</g>:

```cs
[Fact]
void Add_MaximumSumResult_ThrowsOverflowException()
{
    var stringCalculator = new StringCalculator();
    const string MAXIMUM_RESULT = "1001";

    Action actual = () => stringCalculator.Add(MAXIMUM_RESULT);

    Assert.Throws<OverflowException>(actual);
}
```

## avoid logic and flow control
Avoid `if`, `while`, `for`, `switch`, etc, to avoid introducing bugs in a unit test. If logic is required,
consider splitting up the test into multiple tests.

## prefer helper methods over setup and teardown methods
This improves readability and avoids sharing state between tests.

<r>Bad</r>:

```cs
private readonly StringCalculator stringCalculator;

public StringCalculatorTests()
{
    stringCalculator = new StringCalculator();
}

[Fact]
public void Add_TwoNumbers_ReturnsSumOfNumbers()
{
    // This instance of StringCalculator is from shared state in the test class:
    var result = stringCalculator.Add("0,1");

    Assert.Equal(1, result);
}
```

<g>Good</g>:

```cs
private StringCalculator CreateDefaultStringCalculator()
{
    return new StringCalculator();
}

[Fact]
public void Add_TwoNumbers_ReturnsSumOfNumbers()
{
    // Uses a helper method to create a StringCalculator:
    var stringCalculator = CreateDefaultStringCalculator();

    var actual = stringCalculator.Add("0,1");

    Assert.Equal(1, actual);
}
```

## validate private methods by unit testing public methods
Since private methods are an implementation detail, the only result that matters is whether the public method
that uses the private method validates.

## stub static references
Consider the scenario where production code includes calls to static references (like `DateTime.Now`):
```cs
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
        return price / 2;

    else
        return price;
}
```

To solve for this, wrap the code that needs to be controlled in an interface and have the production code
depend on that interface:
```cs
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
        return price / 2;
    
    else
        return price;
}
```

The test suite can now be created:
```cs
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```