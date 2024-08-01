---
title: nullables
date: 2021-11-23T00:00:00-06:00
draft: false
weight: 1
---

# Dereferencing
Accessing a member of a variable through the dot operator.
- Dereferencing a null variable whose value is null is a `NullReferenceException`.

# Checking for Null
```cs
void FindRoot(Node node, Action<Node> processNode) {
	// If this wasn't checked first…
	for (
		var current = node; 
		current is not null; 
		current = current.Parent) { // …then this could be a NullReference…
		processNode(current); 	  // …and so could this.
	}
}
```

Also:
```cs
if (message is not null) { … } 
```

# Using Utility Methods to Check for Null
If you have a private utility method like `IsNotNull()` to check for null, you must add an attribute to its signature to tell the compiler what it does:
```cs
private static bool IsNotNull([NotNullWhen(true)] object? obj) => obj != null;
```

# Null-forgiving Operator (`!`)
The null-forgiving operator (`!`) forces the null-state of a variable to be not-null.  
Use this when you know the variable cannot be null:
```cs
name!.Length;
```
or
```cs
string msg = TryGetMessage(arg)!;
```

# Null-conditional Operator (`?.`)
The null-conditional operator (`?.`) assigns `null` to a variable instead of throwing an exception:
```cs
string authorName = null;
```

This throws a `NullReferenceException`:
```cs
int x = authorName.Length
```

If `authorName.Length` is `null`, set `y` to `null.`  Else, set `y` to `authorName.Length`:
```cs
int? y = authorName?.Length;
```

# Null-coalescing Operator (`??`)
The null-coalescing operator (`??`).
If the left-side operand is not null, return its value.  Else, evaluate the right-side operand:

If `authorName.Length` is `null`, set `y` to `3`.  Else, set `y` to `authorName.Length`:
```cs
int y = authorName?.Length ?? 3;
```

The right side can also be a throw statement:
```cs
var name = value ?? throw new ArgumentNullException(nameof(value), "Name cannot be null.");
```

# Null-coalescing Assignment Operator (`??=`)
The null-coalescing assignment operator (`??=`). 
If the left-side operand is null, assign it the value of the right-side operand.
```cs
int a? = null;
List<int> numbers = new();

numbers.Add(5);
// If a is not null, Add(a).  Else, Add(0).
numbers.Add(a ??= 0); // Adds 0 to numbers.
```

This operator can replace null checking if statements.  So, instead of:
```cs
if (variable is null) { 
	variable = expression;
}
```

Use:
```cs
variable ??= expression;
```

# Avoid Non-nullable Reference Variables Being Uninitialized
```cs
public class Person {
	public string FirstName { get; set; }
	public string LastName { get; set; }
	
	public Person(string f, string l) {	// This constructor requires FirstName and LastName, thereby avoiding a
		FirstName = f;			  // nullable reference.
		LastName = l;
	}
}
```

If the object is required to be created before it's properties are set, use a default non-null value:
```cs
public class Person {
	public string FirstName { get; set; } = string.Empty
	…
}
```

# Allow Reference Types to Hold Null Value
By default in .NET 6+, reference types cannot hold null values.  To override this, at the top of a code file:
```cs
#nullable disable
```
