---
title: verifying mocks
date: 2023-10-31T00:00:00-06:00
draft: false
weight: 2
---

# overview
> Credit: https://docs.educationsmediagroup.com/unit-testing-csharp/moq

Verifications are conducted after production code has been called. They verify that a certain method/property was called with specific arguments.

Test examples below use this interface:
```cs
public interface IService 
{
    void Send(string message);

    Task SendAsync(string message);

    event EventHandler<MessageEventArgs> Sent;

    string ContentType { get; set; }
}
```

# implicit verification
The implicit approach involves calling `Verifiable()` at the end of each configuration to mark the mock to be verified:
```cs
// ARRANGE
// When using this approach, configure mocks with expected parameters as much as possible...
mock.Setup(p => p.Send("Hello word")).Verifiable("Optional custom failure message");

// ASSERT
// ...and rely on implicit verification as much as possible:
mock.VerifyAll(); // Verify all configurations enriched with `Verifiable()` on a single mock were invoked
Mock.Verify(mock, anotherMock, yetAnotherMock); // Verify all configurations enriched with `Verifiable()` on several mocks were invoked
mock.VerifyNoOtherCalls(); // Verify that no other invocations were made other than those already verified
```

## implicit verification for properties
```cs
mock.SetupProperty(p => p.ContentType, "text/plain").Verifiable();
mock.SetupGet(p => p.ContentType).Returns("text/plain").Verifiable();
mock.SetupSet(p => p.ContentType = It.IsAny<string>()).Verifiable();
```

# explicit verification
The explicit approach involves calling `Verify()` on a standalone line. 
```cs
// When using this approach, configure mocks with matchers as much as possible...
mock.Setup(p => p.Send(It.IsAny<string>()));

// ...and rely on explicit verification with constraints as much as possible:
mock.Verify(p => p.Send("Hello world"), Times.Once())
```

## explicit verification for properties
```cs
mock.VerifyGet(p => p.ContentType, Times.Once());
mock.VerifySet(p => p.ContentType = "text/plain", Times.Once());
```

# times
The `Times` class has static methods that can constrain the amount of invocations to expect:
```cs
Times.Exactly(3)
Times.AtLeast(3)
Times.AtMost(3)
Times.Between(3, 5, Range.Inclusive)
Times.Between(2, 4, Range.Exclusive)
Times.Never()
Times.Once()
Times.AtLeastOnce()
Times.AtMostOnce()
```

# verifying event handling
```cs
mock.VerifyAdd(p => p.Sent += It.IsAny<EventHandler<MessageEventArgs>>());
mock.VerifyRemove(p => p.Sent -= It.IsAny<EventHandler<MessageEventArgs>>());
```