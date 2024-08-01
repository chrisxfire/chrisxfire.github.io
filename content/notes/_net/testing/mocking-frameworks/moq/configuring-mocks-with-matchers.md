---
title: configuring mocks with matchers
date: 2023-11-05T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Argument matchers can be used for configuring and verifying methods and properties.

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

var sut = new Service(mock.Object);
```

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