---
title: configuring mocks — methods
date: 2023-10-31T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Credit: https://docs.educationsmediagroup.com/unit-testing-csharp/moq
> Credit: https://softchris.github.io/pages/dotnet-moq.html#creating-our-first-mock

Mocks are configured using the `Setup()` and `Returns()` methods. This configuration, also known as *instruction*, tells the mock to answer with a certain response
if a method or property is called.

Some test examples below use this system:
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

And are arranged like this:
```cs
var mock = new Mock<IFoo>();
mock.Setup(p => p.DoSomething(It.IsAny<string>())).Returns(true);
var sut = new Service(mock.Object);
```

# Configuring Method Calls
When the `DoSomething()` method is called with argument `"ping"`, the method should return `true`:
```cs
mock.Setup(mock => mock.DoSomething("ping")).Returns(true);
```

## Repeated Calls
To test methods that should have different outcomes when called repeatedly:
```cs
mock.SetupSequence(p => p.GetSomething(It.IsAny<string>())
    .Returns(1)
    .Returns(2)
    .Returns(3);
```

If the method returns `void`, replace `Returns(arg)` with `Pass()`.

## `out` Parameters
When `TryParse()` is called with argument `"ping"`, it should set the `out` parameter to `"ack"` and return `true`:
```cs
var outString = "ack";
mock.Setup(mock => mock.TryParse("ping", out outString)).Returns(true);
```

## `ref` Parameters 
Only matches if the `ref` argument to the invocation is the same instance:
```cs
var instance = new Bar();
mock.Setup(mock => mock.Submit(ref instance)).Returns(true);
```

Or:
```cs
var value = "This is a test value";
mock.Setup(p => p.DoSomething(ref value));
```

## Async Methods
Use the Task's `Result` property:
```cs
mock.Setup(mock => mock.DoSomethingAsync().Result).Returns(true);
```

Or, use `ReturnsAsync()`:
```cs
mock.Setup(p => p.GetValueAsync()).ReturnsAsync(123);
```

## Methods with Computed Return Values
For this scenario, both `Returns()` and `ReturnsAsync()` have overloads that accept a delegate:
```cs
mock.Setup(p => p.Add(It.IsAny<int>(), It.IsAny<int>())
    .Returns((int first, int second) => first + second);
```

## Methods That Throw Exceptions
```cs
mock.Setup(p => p.DoSomething()).Throws<Exception>());

mock.Setup(p => p.DoSomethingAsync()).ThrowsAsync(new Exception());
```

# Configuring Mocked Delegates
Consider this delegate:
```cs
public delegate int ParseString(string value);
```

To mock it:
```cs
var mock = new Mock<ParseString>();

mock.Setup(p => p(It.IsAny<string>()))
    .Returns(42);
```