---
title: setting return values
date: 2023-10-30T00:00:00-06:00
draft: false
weight: 2
---

# [Overview](https://nsubstitute.github.io/help/set-return-value/)  

# return values
Assuming this interface:
```cs
public interface ICalculator {
	int Add(int a, int b);
	string Mode { get; set; }
}
```

And this substitute:
```cs
var calculator = Substitute.For<ICalculator>();
```

Use the following API to set return values:

## for methods
```cs
calculator.Add(1, 2).Returns(3);
```

### using argument matching
```cs
// Return when first arg is anything and second arg is 5:
calculator.Add(Arg.Any<int>(), 5).Returns(10);

Assert.AreEqual(10, calculator.Add(123, 5));
Assert.AreEqual(10, calculator.Add(-9, 5));
Assert.AreNotEqual(10, calculator.Add(-9, -9));

// Return when first arg is 1 and second arg less than 0:
calculator.Add(1, Arg.Is<int>(x => x < 0)).Returns(345);

Assert.AreEqual(345, calculator.Add(1, -2));
Assert.AreNotEqual(345, calculator.Add(1, 2));

// Return when both args equal to 0:
calculator.Add(Arg.Is(0), Arg.Is(0)).Returns(99);

Assert.AreEqual(99, calculator.Add(0, 0));
```

### for any argument
The `ReturnsForAnyArgs` method is a shortcut for replacing each argument  with `Arg.Any<T>()`:
```cs
calculator.Add(1, 2).ReturnsForAnyArgs(100); 
// or...
calculator.Add(default, default).ReturnsForAnyArgs(100);

Assert.AreEqual(100, calculator.Add(1, 2));
Assert.AreEqual(100, calculator.Add(-7, 15));
```

## for properties
```cs
calculator.Mode.Returns("DEC");
```

## For Multiple Return Values (Properties or Methods)
```cs
calculator.Mode.Returns("DEC", "HEX", "BIN");

// All true:
Assert.AreEqual("DEC", calculator.Mode);
Assert.AreEqual("HEX", calculator.Mode);
Assert.AreEqual("BIN", calculator.Mode);
```

If this Assert statement were added, it would fail:
```cs
Assert.AreEqual("DEC", calculator.Mode); // Expected "DEC", got "BIN"
```