---
title: "notes > .net > core > control flow"
date: 2022-01-01T00:00:00-06:00
draft: false
---

# `if` - `else if` - `else`
```csharp
if (condition) && (condition2) || (condition3) { … }
else if (condition) { … }
else { … }
```

# Ternary Operator
```cs
condition ? true-return : false-return
```

# `while`
```cs
while (condition) { … }
```

# `do … while`
Executes the code in the body, then checks the condition:
```cs
do {
	…
} while (condition)
```

# `for`
```cs
for (initializer; condition; iterator) { … } 
```
initializer:  `int x = 0`  
condition:    `x < 10`  
iterator:	 `x++`  

All 3 are optional.

# `foreach`
Uses `IEnumerable<T>`.  
Use foreach to enumerate the elements of a collection:
```cs
foreach (int item in a) { … }
foreach (var name in names) { … }
```

`foreach` works on any type that follows these rules:
1. The type must have a method named `GetEnumerator` that returns an object.
2. The returned object must have a property named `Current` and a method named `MoveNext.`
3. The Movenext method must change the value of `Current` and return `true` if there are more items to enumerate through or return `false` otherwise.

## Extend `IEnumerable<T>` to Use `foreach` with Index
```cs
public static IEnumerable<(T item, int index)> WithIndex<T>(this IEnumerable<T> source) {
    return source.Select((item, index) => (item, index));
}

// And now:
foreach (var (item, index) in collection.WithIndex()) {
	DoSomething(item, index);
}
```

# Switch Case
```cs
switch (expression) {	// expression is tested against the cases below.
	case firstCase:	    // if expression == firstCase, execute this block.
		…
		break;		    // must explicitly break or return.
	case secondCase when (otherCondition):	// use the when keyword to define another condition
		…
		break;
	case thirdCase:	    // if expression == thirdCase, fallthrough to fourthCase and execute that block.
	case fourthCase:
		goto Some_label;
	default:		    // if no other cases match, execute this block.
		…
		break;
}

Console.WriteLine("End of switch statement.");
Some_label:
Console.WriteLine("Jumped directly to the label.");
```