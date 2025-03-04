---
title: lambda expressions
date: 2022-05-07T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/fundamentals/expressions/lambda
---

# [Lambda Expression](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions)
Lambda expressions are anonymous functions.  
The lambda operator `=>` ("returns") separates a lambda's parameter list from its body.

```cs
(x) => x * x; // A lambda (anonymous method) with a parameter named x that returns x * x.
```

# lambdas in methods
```cs
int MyFunc(int x)
{
	return x;
}
```
…is equivalent to…
```cs
int MyFunc(int x) => x;
```

# lambdas in anonymous methods
```cs
Func<int, int> = delegate (int x) { return x; };
```
…is equivalent to…
```cs
Func<int, int> = x => x;
```

And...
```cs
someVar.Find(delegate(int in)
{
	if (n < 10)
		return n;
});
```
…is equivalent to…
```cs
someVar.Find(n => n < 10);
```

# Lambda Definition vs. Normal Method Definition
Lambda:
```cs
public override string ToString() => $"{firstName} {lastName}".Trim
```
Normal:
```cs
public override string ToString()
{
	return $"{firstName} {lastName}".Trim();
}
```

# 2 forms of lambda expressions
Expression Lambdas take this form:
```cs
(input-parameters) => expression with return-value
```

Statement Lambdas take this form:
```cs
(input-parameters) => { sequence-of-statements }
```

The body of a statement lambda can have any number of statements (though usually limited to 2 or 3):
```cs
Action<string> greet = name => 
{
	string greet = $"Hello {name}!");
	Console.WriteLine(greeting);
};

greet("World"); // Output: "Hello World!"
```

# lambdas as delegates
Any lambda expression can be converted to a delegate type.
If the lambda doesn't return a value, it can convert to one of the Action delegate types.
- A lambda with 2 parameters, no return value, can convert to `Action<T1, T2>`.
Otherwise, it can be converted to one of the Func delegate types.
- A lambda with 1 parameter and a return value can convert to a `Func<T, TResult>`:
```cs
Func<int, int> square = (x) => x * x; // Since this only has one input parameter, () is optional.
```

Lambdas can be used when code requires instances of delegate types like in `Task.Run(Action)`.

# input parameters of lambda expressions
Input parameters are enclosed in parentheses:
```cs
Action line = () => Console.WriteLine();
```

Since this only has one input parameter, `()` is optional:
```cs
Func<double, double> cube = (x) => x * x * x; 
```

Two or more input parameters are separated by commas:
```cs
Func<int, int, bool> testForEquality = (x, y) => x == y;
```

If the compiler cannot infer types of input parameters, specify them explicitly:
```cs
Func<int, string, bool> isTooLong = (int x, string s) => s.Length > x;
```

Discards can also be used if the input parameters are not used in the expression:
```cs
Func<int, int, int> constant = (_, _) => 42;
```

> [!IMPORTANT]
> Availability: C# 12

Parameters can have default values. The syntax and restrictions are the same as for methods and local functions:
```cs
var IncrementBy = (int source, int increment = 1) => source + increment;

Console.WriteLine(IncrementBy(5)); // 6
Console.WriteLine(IncrementBy(5, 2)); // 7
```

# tuples
Lambdas can contain tuples as a comma-delimited list of components in parentheses:
```cs
Func<(int, int, int), (int, int, int)> doubleThem = ns => (2 * ns.Item1, 2 * ns.Item2, 2 * ns.Item3);
var numbers = (2, 3, 4);
var doubledNumbers = doubleThem(numbers); // doubledNumbers is (4, 6, 8)
```

# Lambdas with System.Linq
The standard query operators can target a Named Method:
```cs
static bool NamesLongerThanFour(string n) { return n > 4; }

var query1 = names.Where(
	new Func<string, bool>(NamesLongerThanFour) // For each string element in names, pass it to this function.
);
```

Or a Lambda Expression:
```cs
var query2 = names.Where(name => name.Length > 4);
```

With `Func` delegates, user-defined expressions can be applied to each element in a collection.
With the `Count` standard query operator:
```cs
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };
int oddNumbers = numbers.Count(n => n % 2 == 1);
Console.WriteLine($"{oddNumbers} odd numbers."); // 6.
```

With the `TakeWhile` standard query operator:
```cs
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };
int firstNumbersLessThanSix = numbers.TakeWhile(n => n < 6);
Console.WriteLine($"{firstNumbersLessThanSix}"); // 5 4 1 3
```

If querying `IEnumberable<Customer>`, the input variable is inferred to be of type Customer which gives you access to Customer's methods and properties:
```cs
customer.Where(c => c.City == "London");
```

# [Natural (Inferred) Type of a Lambda Expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions#natural-type-of-a-lambda-expression)
> [!IMPORTANT]
> Availability: C# 10  

The compiler can sometimes infer the type of a lambda expression.
Here, the type is inferred to be `Func<string, int>`:
```cs
var parse = (string s) => int.Parse(s);
```

If there's not enough information, the compiler cannot infer the parameter type:
```cs
var parse = s => int.parse(s); // ERROR
```

So you must declare the type:
```cs
Func<string, int> parse = s => int.Parse(s); // OK
```

# [Return Type of a Lambda Expression](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions#explicit-return-type)
> [!IMPORTANT]
> Availability: C# 10

Usually, the compiler can infer the return type of a lambda expression. In some cases, it cannot:
```cs
var choose = (bool b) => b ? 1 : "two"; // ERROR: Cannot infer return type
```

In these cases, the return type can be explicitly specified:
```cs
var choose = object (bool b) => b ? 1 : "two"; // Func<bool, object>
```

Note that when explicitly specifying the return type, the input parameters must be parenthesized. 

# [Attributes](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions#attributes)
> [!IMPORTANT]
> Availability: C# 10

Attributes (like `ProvidesNullCheck`) can be added to a lambda expression:
```cs
Func<string?, int?> parse = [ProvidesNullCheck] (s) => (s is not null) ? int.Parse(s) : null;
```

They can also be added to a lambda expression's parameters, like `DisallowNull` here:
```cs
var concat = ([DisallowNull] string a, [DisallowNull] string b) => a + b;
```

Finally, they can be added to the lambda expression's return value, like `NotNullIfNotNull` here:
```cs
var inc = [return: NotNullIfNotNull(nameof(s))] (int? s) => s.HasValue ? s++ : null;
```