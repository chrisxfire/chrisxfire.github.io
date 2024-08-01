---
title: overview
date: 2023-10-30T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://github.com/devlooped/moq/wiki/Quickstart)]  

Moq is a simple, minimalistic mocking framework.

# Installation
```powershell
dotnet add package Moq
```

In test project:
```cs
using Moq;

// If mocking a class with a protected member:
using Moq.Protected;
```

# Overview
## Assumptions
Assume this interface:
```cs
public interface IDateTimeProvider
{
	DayOfWeek DayOfWeek();
	string Name { get; set; }
}
```

Assume a concrete class with one method with two overloads:
```cs
public class RateCalculator
{
    public decimal GetPayRate(decimal baseRate)
    {
        return DateTime.Now.DayOfWeek == DayOfWeek.Sunday ?
			   baseRate * 1.25m :
			   baseRate;
    }
    public decimal GetPayRate(decimal baseRate, IDateTimeProvider dateTimeProvider)
    {
        return dateTimeProvider.DayOfWeek() == DayOfWeek.Sunday ?
			   baseRate * 1.25m :
			   baseRate;
    }
}
```

## Arrange
The `RateCalculator` is the system under test:
```cs
var rateCalculator = new RateCalculator();
```

Create a mock:
```cs
var dateTimeProviderMock = new Mock<IDateTimeProvider>();
```

*Instruct* the mock with Moq's `Setup()` method such that when its `DayOfWeek()` method is called, it returns `DayOfWeek.Sunday`:
```cs
dateTimeProviderMock.Setup(m => m.DayOfWeek()
                    .Returns(DayOfWeek.Sunday);
```

## Act
Call the instance of the system under test **with the mocked object** using the mock's `Object` property:
```cs
var actual = rateCalculator.GetPayRate(10.00m, dateTimeProviderMock.Object);
```

## Assert
Use Moq's `Verify()` method to verify that the mocked object's method ran, and then assert: 
```cs
dateTimeProviderMock.Verify(m => m.DayOfWeek(), Times.Once());

Assert.That(actual, Is.EqualTo(12.5m));
```

# Another Example
> Credit: https://docs.educationsmediagroup.com/unit-testing-csharp/moq/quick-glance-at-moq

Consider this service and interface:
```cs
public class Service
{
    private readonly IFoo _foo;

    public Service(IFoo foo) => _foo = foo ?? throw new ArgumentNullException(nameof(foo));

    public void Ping() => _foo.DoSomething("PING");
}

public interface IFoo
{
    bool DoSomething(string command);
}
```

The test:
```cs
[Test]
public void Ping_invokes_DoSomething()
{
    // ARRANGE
    // Get the mock:
    var mock = new Mock<IFoo>();

    // Set it up:
    mock.Setup(p => p.DoSomething(It.IsAny<string>())).Returns(true);
    
    // Get the system under test by invoking a new instance of the service and passing in the mock object:
    var sut = new Service(mock.Object);

    // ACT
    // Run the method being tested on the system under test:
    sut.Ping();

    // ASSERT
    mock.Verify(p => p.DoSomething("PING"), Times.Once());
}
```

# Verification
## Verifying Method Calls
Verify a method was called with a specific value:
```cs
mock.Verify(foo => foo.DoSomething("ping"));
```

Same as above but with a custom error message:
```cs
mock.Verify(foo => foo.DoSomething("ping"), "Always call DoSomething() with ping argument");
```

Verify the method was called at least once:
```cs
mock.Verify(foo => foo.DoSomething("ping"), Times.AtLeastOnce());
```

Verify the method was never called:
```cs
mock.Verify(foo => foo.DoSomething("ping"), Times.Never());
```

## Verifying Properties
Verify the setter was called with a specific value:
```cs
mock.VerifySet(foo => foo.Name = "foo");
```

Verify the setter was called, regardless of value:
```cs
mock.VerifySet(foo => foo.Name);
```

Verify the setter with an argument matcher:
```cs
mock.VerifySet(foo => foo.Value = It.IsInRange(1, 5, Range.Inclusive));
```

Verify the getter was called, regardless of value:
```cs
mock.VerifyGet(foo => foo.Name);
```

## Verifying Event Accessors
```cs
mock.VerifyAdd(foo => foo.FooEvent += It.IsAny<EventHandler>());
mock.VerifyRemove(foo => foo.FooEvent -= It.IsAny<EventHandler>());
```

## Verify No Other Invocations
Beyond those already verified:
```cs
mock.VerifyNoOtherCalls();
```

// access invocation arguments when returning a value
mock.Setup(x => x.DoSomethingStringy(It.IsAny<string>()))
		.Returns((string s) => s.ToLower());
