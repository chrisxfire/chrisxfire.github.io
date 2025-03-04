---
title: variables
date: 2021-11-06T00:00:00-06:00
draft: false
weight: 1
---

# variables
Every variable has a type that determines what values can be stored in it:
- Non-nullable value type
- Nullable value type
- object
- Class type, Interface type, Array type, Delegate type

# identifiers
Identifiers are variable names.  
Identifiers start with a letter or `_` and use PascalCase.  
`@identifier` allows for variables to be named with C# reserved words.

# creating
C# is strongly typed, so all variables need to be typed: 
```cs 
type identifier; // Declare a variable.
type identifier = value;	// Declare and initialize (instantiate).
```

# implicit typing
Implicitly typed local variables are created with var:
```cs
var message = "Hello, world!";	// message is now implicitly typed string.
```

The `var` keyword requires the variable to be declared and initialized.

## uses
The var keyword can be used:
- On local variables declared at method scope
- In a for initialization statement.
- in a foreach initialization statement.
- In a using statement.
