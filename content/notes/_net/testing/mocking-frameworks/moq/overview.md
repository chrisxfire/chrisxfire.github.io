---
title: overview
date: 2023-10-30T00:00:00-06:00
draft: true
weight: -1
---

# Overview
> Documentation: https://github.com/devlooped/moq/wiki/Quickstart

Moq is a simple, minimalistic mocking framework.

# Installation
```powershell
dotnet add package Moq
```

In test project:
```cs
using Moq;
```

# Usage
Assuming this interface:
```cs
public interface IFoo
{
    Bar Bar { get; set; }
    string Name { get; set; }
    int Value { get; set; }
    bool DoSomething(string value);
    bool DoSomething(int number, string value);
    Task<bool> DoSomethingAsync();
    string DoSomethingStringy(string value);
    bool TryParse(string value, out string outputValue);
    bool Submit(ref Bar bar);
    int GetCount();
    bool Add(int value);
}

public class Bar 
{
    public virtual Baz Baz { get; set; }
    public virtual bool Submit() { return false; }
}

public class Baz
{
    public virtual string Name { get; set; }
}
```

# Setting up Mocks
Set up the mock with `Setup()` and combine it with `Returns()` (if they return a value) or `Throws()` (if they throw an exception):
```cs
var mock = new Mock<IFoo>();
```

To access the mocked object:
```cs
IFoo foo = mock.Object;
```

## Setting up Mocks of Methods
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

## Matching Method Arguments
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

### A Delegate
When `Add()` is called with a `Func<int>`, it should return `true`:
```cs
mock.Setup(foo => foo.Add(It.Is<int>(i => i % 2 == 0))).Returns(true); 
```

### A Range of Values
When `Add()` is called with any integer [0, 10], it should return `true`:
```cs
mock.Setup(foo => foo.Add(It.IsInRange<int>(0, 10, Range.Inclusive))).Returns(true); 
```

### Match a Regex
When `DoSomethingStringy()` is called with a Regex that matches pattern `"[a-d]+"`, it should return `"foo"`:
```cs
mock.Setup(x => x.DoSomethingStringy(It.IsRegex("[a-d]+", RegexOptions.IgnoreCase))).Returns("foo");
```

# Setting up Mocks of Properties
```cs
mock.Setup(foo => foo.Name).Returns("bar");
```

## Mocking Property Hierarchies
Also known as *recursive mocks*:
```cs
mock.Setup(foo => foo.Bar.Baz.Name).Returns("baz");
```

## Mocking a Class That Sets a Property When Invoked
Set up a call to the setter of the mocked type's `Name` property:
```cs
mock.SetupSet(foo => foo.Name = "foo");
```

Verify the setter:
```cs
mock.VerifySet(foo => foo.Name = "foo");
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



// access invocation arguments when returning a value
mock.Setup(x => x.DoSomethingStringy(It.IsAny<string>()))
		.Returns((string s) => s.ToLower());
// Multiple parameters overloads available

// lazy evaluating return value
var count = 1;
mock.Setup(foo => foo.GetCount()).Returns(() => count);


// async methods (see below for more about async):
mock.Setup(foo => foo.DoSomethingAsync().Result).Returns(true);