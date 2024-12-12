---
title: pattern matching
date: 2021-11-19T00:00:00-06:00
draft: false
weight: 1
---

# [Pattern Matching](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching#type-tests) 
See also: https://www.thomasclaudiushuber.com/2021/02/25/c-9-0-pattern-matching-in-switch-expressions/  
See also: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/patterns

## Declaration and Type Patterns
Use declaration and type patterns to check if the runtime type of an expression is compatible with a given type:
```cs
if (o is int i) { … }	// If o matches the pattern of an integer, store it in variable i.
```

Check if a value is null with a declaration pattern using `is`:
```cs
int? maybe = 12;
if (maybe is int number) 
{ 	// Combines test and assignment in single statement.
	…				 // Implicitly:  number = (int)maybe 
}
```

## Logical Pattern (`and`, `or`, and `not`)
Logical patterns are created with `and`, `or`, and `not`:

Check for null or negated null:
```cs
if (x is null and y is not null) { … }
```

*Conjunctive* `and` patterns match an expression when both patterns match the expression:
```cs
Console.WriteLine(Classify(13));  // output: High
Console.WriteLine(Classify(-100));  // output: Too low
Console.WriteLine(Classify(5.7));  // output: Acceptable

static string Classify(double measurement) => measurement switch
{
    < -40.0 => "Too low",
    >= -40.0 and < 0 => "Low",
    >= 0 and < 10.0 => "Acceptable",
    >= 10.0 and < 20.0 => "High",
    >= 20.0 => "Too high",
    double.NaN => "Unknown",
};
```

The opposite of conjunctive `and` patterns are disjunctive `or` patterns, which matches an expression when either pattern matches the expression:
```cs
Console.WriteLine(GetCalendarSeason(new DateTime(2021, 1, 19)));  // output: winter
Console.WriteLine(GetCalendarSeason(new DateTime(2021, 10, 9)));  // output: autumn
Console.WriteLine(GetCalendarSeason(new DateTime(2021, 5, 11)));  // output: spring

static string GetCalendarSeason(DateTime date) => date.Month switch
{
    3 or 4 or 5 => "spring",
    6 or 7 or 8 => "summer",
    9 or 10 or 11 => "autumn",
    12 or 1 or 2 => "winter",
    _ => throw new ArgumentOutOfRangeException(nameof(date), $"Date with unexpected month: {date.Month}."),
};
```

### Logical Pattern Precedence
The combinators have the following precedence:
1. `not`
2. `and`
3. `or`

> [!TIP]  
> More information: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/patterns#precedence-and-order-of-checking

## Parenthesized Pattern
Use to emphasize or change the precedence in logical patterns:
```cs
if (input is not (float or double)) { … }
```

## Property Pattern
Use to match an expression's properties or fields against a nested pattern:
```cs
static bool IsConferenceDay(DateTime date) => date is { Year: 2020, Month: 5, Day: 19 or 20 or 21 };
```
or:
```cs
static bool IsAnyEndOnXAxis(Segment segment) => segment is { Start.Y: 0 } or { End.Y: 0 };
```

## `var` Pattern
Use to match any expression and assign the result to a new local variable:
```cs
static bool IsAcceptable(int id, int absLimit) =>
    SimulateDataFetch(id) is var results 
    && results.Min() >= -absLimit 
    && results.Max() <= absLimit;

static int[] SimulateDataFetch(int id)
{
    var rand = new Random();
    return Enumerable
               .Range(start: 0, count: 5)
               .Select(s => rand.Next(minValue: -10, maxValue: 11))
               .ToArray();
}
```

## List Pattern
<g>Availability: C# 11</g>  
List patterns allow you to match an array or a list against a sequence of patterns:

A pattern of:  
```cs
expr is [1, 2, 3]
```
…is equivalent to…
```cs
expr.Length is 3
    && expr[0] is 1
    && expr[1] is 2
    && expr[2] is 3
```

```cs
int[] numbers = { 1, 2, 3 };

Console.WriteLine(numbers is [1, 2, 3]);  // True
Console.WriteLine(numbers is [1, 2, 4]);  // False
Console.WriteLine(numbers is [1, 2, 3, 4]);  // False
Console.WriteLine(numbers is [0 or 1, <= 2, >= 3]);  // True
```

Combine with the [discard pattern](#discard-pattern) to match any element and the [var pattern](#var-pattern) to capture the element.  The discard `_` matches any single element:
```cs
List<int> numbers = new() { 1, 2, 3 };

if (numbers is [var first, _, _])
    Console.WriteLine($"The first element of a three-item list is {first}."); // The first element of a three-item list is 1.
```

Use a slice pattern to match only elements at the start or end of a sequence.  The range pattern `..` matches any sequence of zero or more elements:
```cs
Console.WriteLine(new[] { 1, 2, 3, 4, 5 } is [> 0, > 0, ..]);  // True
Console.WriteLine(new[] { 1, 1 } is [_, _, ..]);  // True
Console.WriteLine(new[] { 0, 1, 2, 3, 4 } is [> 0, > 0, ..]);  // False
Console.WriteLine(new[] { 1 } is [1, 2, ..]);  // False
```

### Convert with `as`
```cs
var v1 = v2 as type; // This safely converts v2 to type.
if (v1 != null) { … }
```

### Compare discrete values
In a switch, every expression, including null, matches `_`:
```cs
public State PerformOperation(string command) =>
   command switch {
       "SystemTest" => RunDiagnostics(),
       "Start" => StartSystem(),
       "Stop" => StopSystem(),
       "Reset" => ResetToReady(),
       _ => throw new ArgumentException("Invalid string value for command", nameof(command)),
   };
```

## Patterns on Switches
### Discard Pattern
Match any expression, including null:
```cs
static decimal GetDiscountInPercent(DayOfWeek? dayOfWeek) => dayOfWeek switch
{
    DayOfWeek.Monday => 0.5m,
    DayOfWeek.Tuesday => 12.5m,
    DayOfWeek.Wednesday => 7.5m,
    DayOfWeek.Thursday => 12.5m,
    DayOfWeek.Friday => 5.0m,
    DayOfWeek.Saturday => 2.5m,
    DayOfWeek.Sunday => 2.0m,
    _ => 0.0m,
};
```

### Type Pattern
A type pattern allows you to use a type in a switch:
```cs
public static decimal CalculateToll(this Vehicle vehicle) => vehicle switch
{
    Car => 2.00m,
    Truck => 7.50m,
    null => throw new ArgumentNullException(nameof(vehicle)),
    _ => throw new ArgumentException("Unknown type of a vehicle", nameof(vehicle)),
};
```

### Constant Pattern
A constant pattern tests if an expression equals a constant:
```cs
public static decimal GetGroupTicketPrice(int visitorCount) => visitorCount switch
{
    1 => 12.0m,
    2 => 20.0m,
    3 => 27.0m,
    4 => 32.0m,
    0 => 0.0m,
    _ => throw new ArgumentException($"Not supported number of visitors: {visitorCount}", nameof(visitorCount)),
};
```

### Relational Pattern
Use the `< > <=` and `>=` operators to compare an expression result with a constant:
```cs
Console.WriteLine(Classify(13));  // output: Too high
Console.WriteLine(Classify(double.NaN));  // output: Unknown
Console.WriteLine(Classify(2.4));  // output: Acceptable

static string Classify(double measurement) => measurement switch
{
    < -4.0 => "Too low",
    > 10.0 => "Too high",
    double.NaN => "Unknown",
    _ => "Acceptable",
};
```

### Switch Expression
Switch expressions simplify switch statements and are useful where all cases return a value to set a single variable:
```cs
message = s switch {
	FileStream writeableFile when s.CanWrite
	  => "The stream is a file that I can write to.",
	FileStream readOnlyFile
	  => "The stream is a read-only file.",
	MemoryStream ms
	  => "The stream is a memory address.",
	null
	  => "The stream is null.",
	_
	  => "The stream is some other type."
};

string WaterState(int tempInFahrenheit) =>
    tempInFahrenheit switch {
        (> 32) and (< 212) => "liquid",
        < 32 => "solid",
        > 212 => "gas",
        32 => "solid / liquid transition",
        212 => "liquid / gas transition",
    };
```

### Switch Expression with Multiple Inputs
```cs
public decimal CalculateDiscount(Order order) =>
    order switch {
        (Items: > 10, Cost: > 1000.00m) => 0.10m,
        (Items: > 5, Cost: > 500.00m) => 0.05m,
	Test for Order; if true, test for Cost > 250.00; if true, expression.
        Order { Cost: > 250.00m } => 0.02m,
        { } => throw new ArgumentException(message: "Error")	{ } matches any non-null object that 
										didn't match earlier.
        null => throw new ArgumentNullException(nameof(order), 	null matches when null is passed in.
		"Can't calculate on null order"),
        var someObject => 0m,
    };
```
