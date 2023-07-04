---
title: notes > code > .net > classes > methods > methods
date: 2021-11-06T10:44:24-0600
draft: false
---
# Methods
Methods are functions that belong 
to a type that execute statements.  
They are actions that an object can perform, either on itself or on related objects.  
They can be declared in a class, record, or struct.  

There are 4 specialized categories of methods:  
1. Constructor Statements herein execute when `new()` is used to instantiate a class.
2. Property Statements herein execute when data is set or get. Properties encapsulate (and protect) fields.
3. Indexer Statements herein execute when data is set or get or array syntax `[]` is used.
4. Operator Statements herein execute when you use an operator like `+` or `/` on operands of a type.

# Defining
Here, param3 is an optional parameter because it has a default value:
```cs
access-level-modifiers other-modifiers return-type method-name(param1, param2, …) 
{
    expression1;
    …
    return result;
}
```
## Declaring Optional Parameters
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

## Example
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

## Invoking Instance Methods
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

## Invoking Method with Named Arguments
Assuming a method defined like this:
```cs
public void PrintOrderDetails(int orderNum, string productName, string sellerName) 
{ 
    … 
}
```
Instead of position arguments, you can specify named arguments when invoking methods in any order:
```cs
PrintOrderDetails(sellerName: "Gift Shop", productName: "Red Mug", ordeNum: 11);
```

However, if named and positional arguments are mixed, they <u>must</u> be in the correct position:
```cs
PrintOrderDetails(orderNum: 11, "Red Mug", "Gift Shop");
```

## Invoking Method with Optional Arguments
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

# Returning
## Returning Multiple Values
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

## Returning Immediately
If a method just has a single statement or returns the result of a single expression, use `=>`:
```cs
public Point Move(int dx, int dy) => New Point(x + dx, y + dy);

public void Print() => Console.WriteLine("…");

public string Name => First + " " + Last;
```

# Parameters
Parameters pass values or references to methods.  
By default, value types and reference types are passed by value.  

## Pass a Value Type by Value
```cs
int n = 5;
SquareIt(n);

static void SquareIt(int x)
Console.WriteLine(xx); // output: 25

Console.WriteLine(n); // output: 5
```

## Pass a Value Type by Reference
```cs
int n = 5;
SquareIt(ref n);

static void SquareIt(ref int x)
Console.WriteLine(xx); // output: 25

Console.WriteLine(n); // output: 25
```

## Pass a Reference Type by Value
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

## Pass a Reference Type by Reference
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

## Passing an Arbitrary Number of Parameters
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

## Passing a Value-Type by Value
A copy of the value is passed:
```cs
static void SquareIt(int x) => x = x;

static void Main() 
{
    int n = 5; // The value before calling the method = 5.

    SquareIt(n);  // The value in the method = 25.
    Console.WriteLine(n); // The value after calling the method = 5.
}
```

## Passing a Reference-Type by Value
When passing a reference-type parameter by value, you can change the data belonging to the referenced object, but not the value of the reference itself:
```cs
static void Change(int[] myArray) 
{
    myArray[0] = -1; // This change affects the original element.
    myArray = new int[3] { 7, 9, 11 }; // This change is local.
}

static void Main() 
{
    int[] arr = { 1, 3, 5 };
    Change(arr); // arr is now -1, 3, 5;
}
```

## Swapping Value Types
```cs
static void SwapByRef(ref int x, ref int y) 
{
    int temp = x;
    x = y;
    y = temp;
}
```

# Passing Values by Reference
By default, value types are passed by value. These modifiers specify that a variable is passed by reference.  
Any operation on the parameter is made on the argument that was passed in.  

## Restrictions
These keywords are not part of the message signature and so do not apply to overloading if they are the only difference in the signature.

<table style="width:100%;">
<colgroup>
<col style="width: 13%" />
<col style="width: 15%" />
<col style="width: 15%" />
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Parameter<br />
Modifier</strong></th>
<th><strong>Initialization<br />
before passing</strong></th>
<th><strong>Modification by<br />
called method</strong></th>
<th><strong>Both caller and<br />
definition use keyword</strong></th>
<th><strong>Use on first arg of<br />
extension method</strong></th>
<th><strong>Use in async<br />
methods</strong></th>
<th><strong>Use in iterator (yield return<br />
or yield break) methods</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>out</td>
<td>optional</td>
<td>optional</td>
<td>required</td>
<td>never</td>
<td>prohibited</td>
<td>prohibited</td>
</tr>
<tr class="even">
<td>ref</td>
<td>required</td>
<td>required</td>
<td>required</td>
<td>only if arg is not struct</td>
<td>prohibited</td>
<td>prohibited</td>
</tr>
<tr class="odd">
<td>in</td>
<td>required</td>
<td>prohibited</td>
<td>optional</td>
<td>only if arg is a struct</td>
<td>prohibited</td>
<td>prohibited</td>
</tr>
</tbody>
</table>

## Example
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

# Returning Values by Reference
By default, the value is returned by value.  
Values can be returned by reference with the `ref` keyword both in the method signature and the return statement:
```cs
public ref int SomeMethod() 
{
    return ref someValue;
}
```

## Consuming a Ref Return Value
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

# Method Overloading
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
