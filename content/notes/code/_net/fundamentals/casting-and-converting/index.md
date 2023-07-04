---
title: notes > code > .net > fundamentals > casting and converting
date: 2022-01-01T00:00:00-06:00
draft: false
---

# Conversions & Casting
C# is statically typed at compile time.  Once a variable is typed, it cannot hold a different type.

# Implicit Conversions (*Conversions*)
Implicit conversions happen automatically, always succeed, and no data is lost.  
Example:  converting from a `long` to an `int.`

## Derived to Base Type
A derived class always contains all members of a base class.

# Explicit Conversions (*Casting*)
Casting is required when data may be lost in the conversion, or if the conversion may otherwise fail:  
```cs
double x = 1234.7
int a;
a = int(x); // Casting is required because data will be lost.
// a = 1234
```

Casting between reference types does not change the run-time type of the underlying object.

## Base to Derived Type
Explicit conversion is required; will throw an `InvalidCastException` at run time if the right-side object is not the left-side type:
```cs
Giraffe g = new();
Animal a = g; // Implict conversion: safe.
Giraffe g2 = (Giraffe)a; // If a is not a Giraffce, throw InvalidCastException.
```

# User-defined Conversions
Special methods that enable explicit and implict conversions between custom types that do not have a base–derived class relationship.

# Conversions with Helper Classes
Used to convert between non-compatible types like `int` and `DateTime.`

Use the `BitConverter` class to convert an array of bytes into primitive data types.

## Converting Strings to Numbers
Use the `Parse()` and `TryParse()` methods of numeric types.

When using `Parse()`, always catch `FormatException` for when the parse fails:
```cs
string input = "123";
try { 
	int result = Int32.Parse(input);
}
catch (FormatException ex) { … }
```

`TryParse()` will return boolean if the parse can succeed and, if true, store it in an out variable:
```cs
string input = "123";
if (int.TryParse(input, out int result) { … }
```

Use methods of the `Convert` type for general objects that implement `IConvertible`:  
```cs
Convert.ToDecimal(input);
```

## Convert to/from Base64 String
```cs
// Convert a byte array to a base 64 string:
byte[] bytes = { 1, 2, 4, 8, 16, 32 };
string b64 = Convert.ToBase64String(bytes);

// Convert a base 64 string to a byte array:
byte[] newBytes = Convert.FromBase64String(b64);
```

## Convert to/from UTF-8
```cs
using System.Text;

// Convert a UTF-8 JSON string to bytes:
byte[] bytes = Encoding.UTF8.GetBytes(string);
```

# Avoiding Casting Exceptions
Use the `is` or `as` keywords as shown here.  
Alternatively, write try-catch for `InvalidCastException`.

# Using Pattern Matching
## `is` Statement
Use the `is` statement to cast without the risk of an `InvalidCastException`.
```cs
if (a is Mammal m) {
	// If a is a Mammal, declare new Mammal m and set m = a.
}
```
Equivalent to:
```cs
if (a is Mammal) {
	Mammel m = (Mammal)a;
}
```

## `as` Statement
Use the `as` statement to cast without the risk of an `InvalidCastException`.
```cs
var m = o as Mammal; // If o is a Mammal, set m = o.  Else, m = null.
if (m != null) { … }
```

## Pattern Matching Switch Example
```cs
static void PatternMatchingSwitch (System.ValueType val) {
	switch (val) {
		case int number: …
		case long number: …
		case decimal number: …
	}
}
```
