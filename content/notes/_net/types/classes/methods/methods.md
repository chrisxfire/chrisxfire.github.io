---
title: methods
date: 2021-11-06T10:44:24-0600
draft: false
weight: 1
---

# methods
Methods are functions that belong 
to a type that execute statements.  
They are actions that an object can perform, either on itself or on related objects.  
They can be declared in a class, record, or struct.  

There are 4 specialized categories of methods:  
1. Constructor Statements herein execute when `new()` is used to instantiate a class.
2. Property Statements herein execute when data is set or get. Properties encapsulate (and protect) fields.
3. Indexer Statements herein execute when data is set or get or array syntax `[]` is used.
4. Operator Statements herein execute when you use an operator like `+` or `/` on operands of a type.

# defining
Here, param3 is an optional parameter because it has a default value:
```cs
access-level-modifiers other-modifiers return-type method-name(param1, param2, …) 
{
    expression1;
    …
    return result;
}
```
## declaring optional parameters
Parameters can be made optional in method definitions by assigning them a default value.  
Optional parameters must be last in the signature:  
```cs
public void ExampleMethod(int someNum, string someStr = "default string", int optInt = 10);
```

The default value could also be defined:
- `new int()`
- `default(int)`

Optional parameters can also be defined with [OptionalAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.interopservices.optionalattribute?view=net-6.0).

# Instance vs. Static Methods
Methods are either instance (actions an object does to itself) or static (actions the type does).
- The `this` keyword references the current instance of a class.
- Implementing both instance and static methods to perform the same function gives other developers options on how to use your code.

## example
```cs
public static Person Procreate(Person p1, Person p2) 
{ // A static method.
    // Given two Person objects, create an offspring.
    // … Implementation here …
}

public Person ProcreateWith(Person partner) 
{ // An instance method.
    return Procreate(this, partner)// Using the current instance ("this") and another Person object, procreate.
}
```

## invoking instance methods
Instantiate an object, then call the method on that object:
```cs
var x = new class();
x.method(arg1, arg2, …)
```

## Invoking Static Methods:
Static methods are called directly on types:
```cs
type-name.method(arg1, arg2, …)
```

## invoking method with named arguments
Assuming a method defined like this:
```cs
public void PrintOrderDetails(int orderNum, string productName, string sellerName) 
{ 
    … 
}
```
Instead of position arguments, you can specify named arguments when invoking methods in any order:
```cs
PrintOrderDetails(sellerName: "Gift Shop", productName: "Red Mug", orderNum: 11);
```

However, if named and positional arguments are mixed, they <u>must</u> be in the correct position:
```cs
PrintOrderDetails(orderNum: 11, "Red Mug", "Gift Shop");
```

## invoking method with optional arguments
If an argument is provided for any one in a series of optional parameters, an argument must be provided for all preceding optional parameters. Given:
```cs
public void ExampleMethod(int someNum, string someStr = "default string", int optInt = 10);

ExampleMethod(3); // OK.
ExampleMethod(3, 9); // Error.
```
If the name of the 3rd parameter is known, this can be accomplished:
```cs
ExampleMethod(3, optInt: 9);
```

# returning
## returning multiple values
A method can use tuples to return multiple values:
```cs
public (type1, type2, type3) method-name(param1, param2, …)
// or
public (type1: name1, type2: name2, type3: name3) method-name(param1, param2, …) 
{
    …
    return (val1, val2, val3);
}
```

## returning immediately
If a method just has a single statement or returns the result of a single expression, use `=>`:
```cs
public Point Move(int dx, int dy) => New Point(x + dx, y + dy);

public void Print() => Console.WriteLine("…");

public string Name => First + " " + Last;
```

# parameters
Parameters pass values or references to methods.  
By default, value types and reference types are passed by value.  

## Passing a Value-Type by Value
A copy of the value is passed:
```cs
int n = 5;
SquareIt(n);

static void SquareIt(int x)
Console.WriteLine(xx); // output: 25

Console.WriteLine(n); // output: 5
```

## Passing a Value-Type by Reference
```cs
int n = 5;
SquareIt(ref n);

static void SquareIt(ref int x)
Console.WriteLine(xx); // output: 25

Console.WriteLine(n); // output: 25
```

## Passing a Reference-Type by Value
When passing a reference-type parameter by value, you can change the data belonging to the referenced object, but not the value of the reference itself:

```cs
int[] arr = { 1, 3, 5 };

Change(arr);

static void Change(int[] pArray) 
{
    pArray[0] = 10; // This changes the original array.
    pArray = new int[3] { 2, 4, 6 }; // This is a new array.
}

Console.WriteLine(pArray[0]); // output: 10
```

## Passing a Reference-Type by Reference
```cs
int[] arr = { 1, 3, 5 };

Change(ref arr);

static void Change(ref int[] pArray) 
{
    pArray[0] = 10; // This changes the original array.
    pArray = new int[3] { 2, 4, 6 }; // This changes the original array.
}

Console.WriteLine(pArray[0]); // output: 2
```

## passing an arbitrary number of parameters
Use the `params` keyword to specify that the last argument is a parameter array:
```cs
string GetVowels(params string[] input) 
{ 
    … 
}
```

Valid calls on the above method signature:
- An array of the type: `result = GetVowels(new[] { "apple", "banana", "pear", … });`
- A comma-separated list: `result = GetVowels("apple", "banana", "pear", …);`
- Pass null: `result = GetVowels(null);`
- Pass nothing: `result = GetVowels();`

## swapping value types
```cs
static void SwapByRef(ref int x, ref int y) 
{
    int temp = x;
    x = y;
    y = temp;
}
```

# reference parameter modifiers for passing values by reference
By default, value types are passed by value. These modifiers specify that a variable is passed by reference.  
Any operation on the parameter is made on the argument that was passed in.  
These modifiers are not part of the message signature and so do not apply to overloading if they are the only difference in the signature.  

- `ref` modifier: The passed argument must be initialized before calling the method. The method may assign a new value to the parameter.
- `out` modifier: The passed argument may be initialized before calling the method. The method must assign a new value to the parameter.
- `ref readonly` modifier: The passed argument must be initialized before calling the method. The method cannot assign a new value to the parameter.
- `in` modifier: The passed argument must be initialized before calling the method. The method cannot assign a new value to the parameter. The compiler may create a temporary variable to hold a copy of the argument to `in` parameters.

The below table summarizes the above points and adds additional information:

| Parameter modifier | Means the method...                                                                     | Argument passed to this parameter includes | Use in `async` methods | Use in iterator methods | Use when first argument is a struct |
| ------------------ | --------------------------------------------------------------------------------------- | ------------------------------------------ | ---------------------- | ----------------------- | ----------------------------------- |
| `ref`              | Reads or writes the value of the argument                                               | `ref` modifier, required                   | prohibited             | prohibited              | permitted                           |
| `out`              | Sets the value of the argument                                                          | `out` modifier, required                   | prohibited             | prohibited              | permitted                           |
| `in`               | Reads—cannot write—the value of the argument (argument will be passed by reference)     | `in` modifier, optional                    | prohibited             | prohibited              | prohibited                          |
| `ref readonly`     | Reads—cannot write—the value of the argument (argument *should* be passed by reference) | `in` or `ref` modifier, required           | prohibited             | prohibited              | prohibited                          |

## `ref` parameter modifier
```cs
void Method(ref int refArgument)
{
    refArgument = refArgument + 44;
}

int number = 1;
Method(ref number);
Console.WriteLine(number); // Output: 45
```

## `out` parameter modifier
```cs
int initializeInMethod;
OutArgExample(out initializeInMethod);
Console.WriteLine(initializeInMethod);     // value is now 44

void OutArgExample(out int number)
{
    number = 44;
}
```

The `out` variable can be declared in the argument list of a method call:
```cs
string numberAsString = "1640";

if (Int32.TryParse(numberAsString, out int number))
    Console.WriteLine($"Converted '{numberAsString}' to {number}"); // output: Converted '1640' to 1640

else
    Console.WriteLine($"Unable to convert '{numberAsString}'");
```

## [`in` parameter modifier](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters#in-parameter-modifier)
The `in` modifier allows the compiler to create a temporary variable for the argument and pass a readonly reference to that argument. Methods that are defined using `in` parameters potentially gain performance optimization.

```cs
int readonlyArgument = 44;
InArgExample(readonlyArgument);
Console.WriteLine(readonlyArgument);     // value is still 44

void InArgExample(in int number)
{
    // Uncomment the following line to see error CS8331
    //number = 19;
}
```

## `ref readonly` modifier
Arguments passed to a `ref readonly` parameter require either the `ref` or `in` modifier to be used at the call site:
- Use `ref` if the argument is a variable and writable.
- Use `in` when the argument is a variable and either writable or `readonly`.

```cs
public static void ForceByRef(ref readonly OptionStruct thing)
{
    // ...
}

ForceByRef(in options);
ForceByRef(ref options);
ForceByRef(options); // Warning! variable should be passed with `ref` or `in`
ForceByRef(new OptionStruct()); // Warning, but argument is an expression, so no variable to reference
```

## `ref` and `out` parameter modifiers
```cs
public void PassingParameters(int x, ref int y, out int z) 
{
    z = 99;
    x++;
    y++;
    z++;
}

int a = 10;
int b = 20;

PassingParameters(a, ref b, out c);

a // returns 10
b // returns 21 because y is a reference to b
c // returns 100 because z is a reference to c
```

# returning values by reference
By default, the value is returned by value.  
Values can be returned by reference with the `ref` keyword both in the method signature and the return statement:
```cs
public ref int SomeMethod() 
{
    return ref someValue;
}
```

## consuming a ref return value
The ref return value is an alias to another variable in the called method's scope.   

This value can be consumed like any other:
```cs
int myValue = SomeMethod();
```
- Any future assignments to `myValue` will not change the value of the variable returned by `SomeMethod()`.

Declare a ref local variable if you intend to modify it:
```cs
ref int myValue = ref SomeMethod();
```
- Here, `myValue` is now a reference to the value returned by `SomeMethod()`.
- Changing `myValue` will change the value of the variable returned by `SomeMethod()`.

# method overloading
Permits multiple methods in the same class to have the same name as long as they have a different signature:
```cs
class F 
{
    static void F() => Console.WriteLine("F()");
    static void F(object x) => Console.WriteLine("F(object)");
    static void F(int x) => Console.WriteLine("F(int)");
    static void F(double x) => Console.WriteLine("F(double)");
    static void F<T>(T x) => Console.WriteLine("F<T>(T)");
    public static void UsageExample()

    {
        F(); // Invokes F()
        F(1); // Invokes F(int)
        F(1.0); // Invokes F(double)
        F("abc"); // Invokes F<string>(string)
        F((double)1); // Invokes F(double)
        F((object)1); // Invokes F(object)
        F<int>(1); // Invokes F<int>(int)
    }
}
```
