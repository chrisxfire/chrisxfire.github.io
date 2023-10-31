---
title: overview
date: 2023-10-30T00:00:00-06:00
draft: true
weight: -1
---

# Introduction
> Documentation: https://github.com/devlooped/moq/wiki/Quickstart

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
Call the instance of the system under test with the mocked object using the mock's `Object` property:
```cs
var actual = rateCalculator.GetPayRate(10.00m, dateTimeProviderMock.Object);
```

## Assert
Use Moq's `Verify()` method to verify that the mocked object's method ran, and then assert: 
```cs
dateTimeProviderMock.Verify(m => m.DayOfWeek(), Times.Once());

Assert.That(actual, Is.EqualTo(12.5m));
```

# Instructing Mocks — Methods
When the `DoSomething()` method is called with argument `"ping"`, the method should return `true`:
```cs
mock.Setup(foo => foo.DoSomething("ping")).Returns(true);
```

## Methods with `out` and `ref` Parameters
`out` arguments:  
When `TryParse()` is called with argument `"ping"`, it should set the `out` parameter to `"ack"` and return `true`:
```cs
var outString = "ack";

// TryParse will return true, and the out argument will return "ack", lazy evaluated
mock.Setup(foo => foo.TryParse("ping", out outString)).Returns(true);
```

`ref` arguments:  
Only matches if the `ref` argument to the invocation is the same instance:
```cs
var instance = new Bar();

mock.Setup(foo => foo.Submit(ref instance)).Returns(true);
```

## Methods That Throw Exceptions
```cs
// throwing when invoked with specific parameters
mock.Setup(foo => foo.DoSomething("reset")).Throws<InvalidOperationException>();
mock.Setup(foo => foo.DoSomething("")).Throws(new ArgumentException("command"));
```

## Async Methods
Use the Task's `Result` property:
```cs
mock.Setup(foo => foo.DoSomethingAsync().Result).Returns(true);
```

## Instructing Mocks by Matching Method Arguments
### Any Value of type `T` for an Argument
When `DoSomething()` is called with any string argument, it should return `true`:
```cs
mock.Setup(foo => foo.DoSomething(It.IsAny<string>())).Returns(true);
```

### Any Value as `ref` Parameter
When `Submit()` is called with any `ref` parameter of type `Bar`, it should return `true`:
```cs
mock.Setup(foo => foo.Submit(ref It.Ref<Bar>.IsAny)).Returns(true);
```

### A Range of Values
When `Add()` is called with any integer [0, 10], it should return `true`:
```cs
mock.Setup(foo => foo.Add(It.IsInRange<int>(0, 10, Range.Inclusive))).Returns(true); 
```

### A Delegate
When `Add()` is called with a `Func<int>`, it should return `true`:
```cs
mock.Setup(foo => foo.Add(It.Is<int>(i => i % 2 == 0))).Returns(true); 
```

### A Regex
When `DoSomethingStringy()` is called with a regular expression that matches pattern `"[a-d]+"`, it should return `"foo"`:
```cs
mock.Setup(x => x.DoSomethingStringy(It.IsRegex("[a-d]+", RegexOptions.IgnoreCase))).Returns("foo");
```

# Instructing Mocks - Properties
When invoked, the type's `Name` property returns value `"bar"`:
```cs
mock.Setup(foo => foo.Name).Returns("bar");
```

## Hierarchies of Properties
Also known as *recursive mocks*:
```cs
mock.Setup(foo => foo.Bar.Baz.Name).Returns("baz");
```

## A Property Setter
Set up a call to the setter of the mocked type's `Name` property with a specific value:
```cs
mock.SetupSet(foo => foo.Name = "foo");
```

## Stub a Property (to automatically track its value)
Use `SetupProperty()` to start "tracking" the sets/gets on a property:
```cs
mock.SetupProperty(f => f.Name);

// alternatively, provide a default value for the stubbed property:
mock.SetupProperty(f => f.Name, "foo");
```

Once the property is stubbed, now you can:
```cs
IFoo foo = mock.Object;

// Assert that the initial value was stored:
Assert.Equal("foo", foo.Name);

// Assert that a new value set which changes the initial value:
foo.Name = "bar";
Assert.Equal("bar", foo.Name);
```

## Stubbing All Properties on a Mock
```cs
mock.SetupAllProperties();
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
// Multiple parameters overloads available

// lazy evaluating return value
var count = 1;
mock.Setup(foo => foo.GetCount()).Returns(() => count);


// async methods (see below for more about async):
mock.Setup(foo => foo.DoSomethingAsync().Result).Returns(true);