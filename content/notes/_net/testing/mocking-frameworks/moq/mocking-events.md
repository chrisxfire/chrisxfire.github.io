---
title: mocking events
date: 2023-11-10T00:00:00-06:00
draft: false
weight: 1
---

# Overview
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