---
title: configuring mocks
date: 2023-10-31T00:00:00-06:00
draft: true
weight: 1
---

# Overview
> Credit: https://docs.educationsmediagroup.com/unit-testing-csharp/moq

Mocks are configured using the `Setup()` and `Returns()` methods. This configures the mock to return a certain value when a method or property is called.

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

# Configuring Properties
When invoked, the type's `Name` property returns value `"bar"`:
```cs
mock.Setup(mock => mock.Name).Returns("bar");
```

## Property Chains
Also known as *recursive mocks*:
```cs
var mock = new Mock<HttpContextBase>();
mock.SetupGet(p => p.Response.Request.UserAgent).Returns("My Browser");
```

## SetupSet (Setters) and SetupGet (Getters)
Use `SetupSet()` to configure the setter of the mocked type's `Name` property with a specific value:
```cs
mock.SetupSet(foo => foo.Name = "foo");
```

Use `SetupGet()` to configure the getter.

## SetupProperty for Auto Properties
Use `SetupProperty()` to start "tracking" the sets/gets on a property (useful for automatic properties):
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

## SetupAllProperties to Track All Auto Properties
```cs
mock.SetupAllProperties();
```

# Matchers
Argument matchers can be used for configuring and verifying methods and properties.

## Configuring Method Calls with Matchers
### `It.Is<T>` for any instance of `T`
When `DoSomething()` is called with any string argument, it should return `true`:
```cs
mock.Setup(mock => mock.DoSomething(It.IsAny<string>())).Returns(true);
```

### `It.IsInRange` for any value in a range
When `Add()` is called with any integer in the range [0, 10], it should return `true`:
```cs
mock.Setup(mock => mock.Add(It.IsInRange<int>(0, 10, Range.Inclusive))).Returns(true); 
```

### `It.Ref<T>.IsAny` for any value of a `ref` parameter
When `Submit()` is called with any `ref` parameter of type `Bar`, it should return `true`:
```cs
mock.Setup(mock => mock.Submit(ref It.Ref<Bar>.IsAny)).Returns(true);
```

### `It.IsRegex` for any string that matches a regular expression pattern
When `DoSomethingStringy()` is called with a string that matches regular expression pattern `"[a-d]+"`, it should return `"foo"`:
```cs
mock.Setup(x => x.GetUsername(It.IsRegex("[a-d]+", RegexOptions.IgnoreCase))).Returns("foo");
```

### `InSequence` for verifying the calling sequence
This specifies that `DoWithInteger()` must be called, followed directly by `DoWithDate()`.  Use `MockBehavior.Strict` to throw exceptions for non-configured calls:
```cs
var mockFirst = new Mock<IFirstService>(MockBehavior.Strict);
var mockSecond = new Mock<ISecondService>(MockBehavior.Strict);

var sequence = new MockSequence();

mockFirst.InSequence(sequence).Setup(p => p.DoWithInteger(1));
mockSecond.InSequence(sequence).Setup(p => p.DoWithDate(DateTime.Today));
```

### A Delegate
When `Add()` is called with a `Func<int>`, it should return `true`:
```cs
mock.Setup(mock => mock.Add(It.Is<int>(i => i % 2 == 0))).Returns(true); 
```

# Configuring Events
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

## Testing for Raised Events
### Arrange
```cs
var mock = new Mock<IService>();

mock.Setup(p => p.Send(It.IsAny<string>()))
    .Raises(e => e.Sent += null, (string msg) => new MessageEventArgs { Message = msg });
```

Configure functions (like `Receive()`) to raise an event when invoked:
```cs
mock.Setup(p => p.Receive())
    .Returns("Hello")
    .Raises(e => e.Received += null, (string msg) => new MessageEventArgs { Message = msg });
```

If the methods are asynchronous:
```cs {hl_lines=2,6}
mock.Setup(p => p.SendAsync(It.IsAny<string>()))
    .Returns(Task.CompletedTask)
    .Raises(e => e.Sent += null, (string message) => new MessageEventArgs { Message = message });

mock.Setup(p => p.ReceiveAsync())
    .ReturnsAsync("Hello")
    .Raises(e => e.Received += null, (string msg) => new MessageEventArgs { Message = msg });
```

### Act
Attach an event handler:
```cs
var service = mock.Object;

service.Sent += (object sender, MessageEventArgs args) => TestContext.Progress.Writeline(args.Message);
```

Invoke the send method:
```cs
service.Send("Hello World");
```

### Assert
Events can be raised manually:
```cs
mock.Raise(p => p.Sent += null, new MessageEventArgs { Message = "Hello world" });
```

## Verifying Event Handling
```cs
mock.VerifyAdd(p => p.Sent += It.IsAny<EventHandler<MessageEventArgs>>());
mock.VerifyRemove(p => p.Sent -= It.IsAny<EventHandler<MessageEventArgs>>());
```