---
title: overview
date: 2023-10-30T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://nsubstitute.github.io/help/getting-started/)]  

NSubstitute is a mocking framework for .NET. It abstracts the difference between a mock, stub, fake, spy, or test double.

NSubstitute requires interfaces. On a limited basis, it can work with virtual members of a concrete class, but any non-virtual code will actually execute.

# Installation
```powershell
dotnet add package NSubstitute
dotnet add package NSubstitute.Analyzers.CSharp # optional
```

In test project:
```cs
using NSubstitute;
```

# Usage
Assuming this interface:
```cs
public interface ICalculator
{
    int Add(int a, int b);
    string Mode { get; set; }
    event EventHandler PoweringUp;
}
```

## Arrange
```cs
var calculator = Substitute.For<ICalculator>();
calculator.Mode = "DEC";
```

## Act
```cs
calculator.Add(1, 2);
```

## Assert
```cs
// Assert that calculator received the correct input:
calculator.Received().Add(1, 2); 
// Assert that calculator did NOT receive this incorrect input:
calculator.DidNotReceive().Add(5, 7);

calculator.Returns(3);
// or ...
Assert.That(calculator.Add(1, 2), Is.EqualTo(3));

calculator.Mode.Returns("DEC");
// or...
Assert.That(calculator.Mode, Is.EqualTo("DEC"));

// or that calculator.Mode is one of these values:
calculator.Mode.Returns("HEX", "DEC", "BIN");
Assert.That(calculator.Mode, Is.EqualTo("HEX"));
Assert.That(calculator.Mode, Is.EqualTo("DEC"));
Assert.That(calculator.Mode, Is.EqualTo("BIN"));
```