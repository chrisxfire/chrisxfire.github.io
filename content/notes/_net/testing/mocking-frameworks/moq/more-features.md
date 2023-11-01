---
title: more features
date: 2023-10-31T00:00:00-06:00
draft: false
weight: 3
---

# Overview
These notes provide links to other features of Moq not covered in other notes.

# Customizing Mock Behavior
When instantiating a mock, pass the `MockBehavior` enum to customize the behavior:
```cs
var mock = new Mock<IService>(MockBehavior.Strict);
```

Behaviors:
* `Strict` — throw an exception whenever a method or property is invoked without a matching configuration  
* `Loose` (default) — return a default value instead of throwing an exception

# Callbacks
See https://docs.educationsmediagroup.com/unit-testing-csharp/moq/callbacks

# Events
Assuming this code:
```cs
public class MessageEventArgs : EventArgs
{
    public string Message { get; set; }
}

public interface IService 
{
    event EventHandler<MessageEventArgs> Sent;

    event EventHandler<MessageEventArgs> Received;

    Task SendAsync(string message);

    void Send(string message);

    string Receive();

    Task<string> ReceiveAsync();
}
```

## Function Calls
In this approach, an event (`Sent`) is raised when a configured *function* (which, in this case, is a method with no return value, `Send()`) is invoked:
```cs
// ARRANGE
var mock = new Mock<IService>();
mock.Setup(p => p.Send(It.IsAny<string>()))
    .Raises(e => e.Sent += null, (string msg) => new MessageEventArgs { Message = msg });

var service = mock.Object;

// Attach an event handler to the event:
service.Sent += (object sender, MessageEventArgs args) => TestContext.Progress.Writeline(args.Message);

// ACT
// Invoke the Send method:
service.Send("Hello World");
```

### Asynchronous Function Calls
If we were using an asynchronous method instead, the configure it as follows:
```cs
mock.Setup(p => p.SendAsync(It.IsAny<string>()))
    .Returns(Task.CompletedTask)
    .Raises(e => e.Sent += null, (string message) => new MessageEventArgs { Message = message });
```

## Method Calls
In this approach, an event is raised when a configured *method* is invoked. This approach is the same as above, except that configuration for what the
method will return is added before configuring the call to `Raises()`:
```cs
var mock = new Mock<IService>();
mock.Setup(p => p.Receive())
    .Returns("Hello")
    .Raises(e => e.Received += null, (string msg) => new MessageEventArgs { Message = msg });

// ...
```

### Asynchronous Method Calls
If we were using an asynchronous method instead, configure it as follows:
```cs
mock.Setup(p => p.ReceiveAsync())
    .ReturnsAsync("Hello")
    .Raises(e => e.Received += null, (string msg) => new MessageEventArgs { Message = msg });
```

## Manually Raising Events
If the SUT accepts a service that exposes an event, subscribes to this event, and reacts when it is raised, we
can manually raise an event as part of the *Act* step:
```cs
mock.Raise(p => p.Sent += null, new MessageEventArgs { Message = "Hello world" });
```

## Verifying Events
Assume the event handler is registered/unregistered as follows:
```cs
service.Sent += MessageSent;
```
```cs
service.Sent -= MessageSent;
```

To verify registration/deregistration:
```cs
mock.VerifyAdd(p => p.Sent += It.IsAny<EventHandler<MessageEventArgs>>());
mock.VerifyRemove(p => p.Sent -= It.IsAny<EventHandler<MessageEventArgs>>());
```

# Implicit Mocks
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

# Mocking a Type with Generic Methods
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

# Mocking a Type That Inherits Multiple Interfaces
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