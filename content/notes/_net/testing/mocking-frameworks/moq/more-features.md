---
title: more features
date: 2023-10-31T00:00:00-06:00
draft: false
weight: 3
---

# overview
These notes provide links to other features of Moq not covered in other notes.

# customizing mock behavior
When instantiating a mock, pass the `MockBehavior` enum to customize the behavior:
```cs
var mock = new Mock<IService>(MockBehavior.Strict);
```

Behaviors:
* `Strict` — throw an exception whenever a method or property is invoked without a matching configuration  
* `Loose` (default) — return a default value instead of throwing an exception

# callbacks
See https://docs.educationsmediagroup.com/unit-testing-csharp/moq/callbacks

# implicit mocks
When mocking interfaces that don't need any configuration or verification, use implicit mocks:
```cs
var logger = Mock.Of<ILogger>();
```

This is equivalent to:
```cs
var mock = new Mock<ILogger>();
var logger = mock.Object;
```

To get the underlying mock:
```cs
var mock = Mock.Get(logger);
```

# mocking a type with generic methods
Consider this interface:
```cs
public interface IService
{
    void DoSomething<T>(T argument);
}
```

Use `It.IsAnyType` to configure the mocked method to accept any type:
```cs
mock.Setup(p => p.DoSomething(It.IsAny<It.IsAnyType>()))
    .Callback((object value) => TestContext.Progress.Writeline($"DoSomething: {value}"));
```

Use `It.IsSubtype` to constrain the incoming type parameter:
```cs
mock.Setup(p => p.DoSomething(It.IsAny<It.IsSubtype<IList<string>>>()))
    .Callback((IList<string> items) => TestContext.Progress.Writeline($"Received list of {items.Count} strings"));

mock.Setup(p => p.DoSomething(It.IsAny<It.IsSubtype<IList<int>>>()))
    .Throws<ArgumentException>();
```

# mocking a type that inherits multiple interfaces
Consider this class that inherits more than one interface:
```cs
public class Dependency : IDependency, IDisposable { ... }
```

To mock it:
```cs
var mock = new Mock<IDependency>();
var mockDisposable = mock.As<IDisposable>();
```

Or, to access the mock of the `IDisposable` interface from `mock`:
```cs
mock.As<IDisposable>().Setup(p => p.Dispose());
```