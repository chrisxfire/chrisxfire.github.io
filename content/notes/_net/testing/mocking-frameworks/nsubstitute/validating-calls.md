---
title: validating calls
date: 2023-10-30T00:00:00-06:00
draft: false
weight: 3
---

# [Overview](https://nsubstitute.github.io/help/received-calls/)  

# validating calls
Assuming this code:
```cs
public interface ICommand 
{
    void Execute();

    event EventHandler Executed;
}

public class SomethingThatNeedsACommand 
{
    ICommand command;

    public SomethingThatNeedsACommand(ICommand command) => this.command = command;

    public void DoSomething() { command.Execute(); }
    public void DoNothing { }
}
```
## to methods
### validate a method was called
```cs
[Test]
public void Should_execute_command() 
{
    var command = Substitute.For<ICommand>();
    var something = new SomethingThatNeedsACommand(command);
    
    something.DoSomething();
    
    // Assert
    command.Received().Execute(); // Successful because command received a call to its Execute method.

    // Or, assert that a method was called a specific number of times:
    command.Received(3).Execute();
}
```

To confirm a method was called regardless of arguments:
```cs
calculator.Add(1,3);

calculator.ReceivedWithAnyArgs().Add(default, default);
```

### validate a method was not called
```cs
var command = Substitute.For<ICommand>();
var something = new SomethingThatNeedsACommand(command);

something.DoNothing;

command.DidNotReceive().Execute();
```

To confirm a method was not called regardless of arguments:
```cs
calculator.Add(1,3);

calculator.DidNotReceiveWithAnyArgs().Subtract(default, default);
```

### validate a method was called with specific arguments
```cs
calculator.Add(1, 2);
calculator.Add(-100, 100);

// Validate method received call with second arg of 2 and any first arg:
calculator.Received().Add(Arg.Any<int>(), 2);

// Validate method received call with first arg less than 0, and second arg of 100:
calculator.Received().Add(Arg.Is<int>(x => x < 0), 100);

// Validate method did not receive a call where second arg is >= 500 and any first arg:
calculator.DidNotReceive().Add(Arg.Any<int>(), Arg.Is<int>(x => x >= 500));
```

### clear previous method calls
```cs
command.ClearReceivedCalls();
```

## to properties
```cs
calculator.Mode = "Test";

// Validate a call to a getter:
_ = calculator.Received().Mode; // OK

// Validate a call to a setter:
calculator.Received().Mode = "Test 2"; // Fails
```

## to indexers
```cs
var dictionary = Substitute.For<IDictionary<string, int>>();
dictionary["test"] = 1;

dictionary.Received()["test"] = 1;
dictionary.Received()["test"] = Arg.Is<int>(x => x < 5);
```

## validating event subscriptions
See https://nsubstitute.github.io/help/received-calls/#checking-event-subscriptions

## validating event invocation
See https://nsubstitute.github.io/help/received-calls/#checking-event-invocation
