---
title: validating calls
date: 2023-10-30T00:00:00-06:00
draft: false
weight: 3
---

# Overview
> Documentation: https://nsubstitute.github.io/help/received-calls/

# Validating Calls
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
## To Methods
### Validate a Method was Called
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

### Validate a Method Was Not Called
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

### Validate a Method was Called with Specific Arguments
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

### Clear Previous Method calls
```cs
command.ClearReceivedCalls();
```

## To Properties
```cs
calculator.Mode = "Test";

// Validate a call to a getter:
_ = calculator.Received().Mode; // OK

// Validate a call to a setter:
calculator.Received().Mode = "Test 2"; // Fails
```

## To Indexers
```cs
var dictionary = Substitute.For<IDictionary<string, int>>();
dictionary["test"] = 1;

dictionary.Received()["test"] = 1;
dictionary.Received()["test"] = Arg.Is<int>(x => x < 5);
```

## Validating Event Subscriptions
See https://nsubstitute.github.io/help/received-calls/#checking-event-subscriptions

## Validating Event Invocation
See https://nsubstitute.github.io/help/received-calls/#checking-event-invocation
