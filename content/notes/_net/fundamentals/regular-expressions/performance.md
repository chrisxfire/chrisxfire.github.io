---
title: performance
date: 2023-11-17T00:00:00-06:00
draft: false
weight: 1
---

# Regular Expression Engine Performance Considerations
There are five techniques for coupling the regex engine to a regex pattern:
1. Instantiate a `RegEx` object (*interpreted* regular expressions)
2. Call a static pattern-matching method  (*interpreted*)
3. Instantiate a `RegEx` object with the `Compiled` option (*compiled* regular expressions)
4. Create a `RegEx` object and save it to a standalone assembly (`Regex.CompileToAssembly`)
5. Use the .NET regular expression source generator, `RegexGenerator` (requires .NET 7+)

| Technique         | Invoked via                                  | Construction Cost | Execution Cost | Considerations                                                       | Use case                                                                    |
| ----------------- | -------------------------------------------- | ----------------- | -------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Interpreted       | `new Regex()` <br /> a `Regex` static method | Low               | High           | Cost is incurred each instantiation                                  | A Regex that is called infrequently and high performance cost is acceptable |
| Compiled          | `RegexOptions.Compiled`                      | High              | Low            | Adds to startup cost                                                 | A Regex that is called frequently in .NET 6 or earlier                      |
| Assembly          | `Regex.CompileToAssembly`                    | Low               | Low            | Difficult to use <br /> Difficult to debug                           | Low performance cost and smaller app size is required                       |
| Source generation | `GeneratedRegexAttribute`                    | Low               | Low            | Supports AOT compilation <br /> Emits more source, increase app size | A Regex that is called frequently in .NET 7 or later                        |

## Avoid Repeated Regex Object Instantiation
Each time a Regex object is instantiated, the regular expression pattern passed to it must be recompiled. This is an expensive operation.

Below, each time `IsValidCurrency` is called, a new `Regex` object is instantiated:
```cs
public static bool IsValidCurrency(string currencyValue)
{
    string pattern = @"\p{Sc}+\s\d+";
 
    Regex currencyRegex = new Regex(pattern); // This object is instantiated and the regular expression pattern is compiled
 
    return currencyRegex.IsMatch(currencyValue);
}
```

Instead, consider this call to a static `Regex` method:
```cs
public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";

      return Regex.IsMatch(currencyValue, pattern);
   }
}
```

## Using Source Generated Regular Expressions (#5)
> [!IMPORTANT]
> Availability: .NET 7 

A *source generator* is a component that plugs into the compiler, is given information about the code like an
analyzer, and can augment the compiled output with additional source code. 

The `RegexGenerator` (source generator) is invoked on partial methods decorated with `GeneratedRegexAttribute` with a return type `Regex`.

```cs
[GeneratedRegex("abc|def", RegexOptions.IgnoreCase, "en-US")]
private static partial Regex AbcOrDefGeneratedRegex();

private static void EvaluateText(string text)
{
    if (AbcOrDefGeneratedRegex().IsMatch(text))
        // ...
}
```

The generated source code can be debugged like any other source code.

# Other Performance Considerations
## Backtracking
Ordinarily, the regex engine uses linear progression to traverse an input string and compare it to a regex pattern. 
Indeterminate quantifiers like `*`, `+`, and `?` allow the regex engine to give up a partial successful match to search for a successful match in the entire pattern. This is *backtracking*.  

Backtracking can significantly degrade performance. Worst case, execution time doubles for each additional character in input.
If backtracking is not necessary, either:
1. Disable it with an atomic group: `(?>subexpression)`, or;
2. Pass `RegexOptions.NonBacktracking`.  This guarantees linear progression and avoids backtracking.

## Nonbacktracking Mode Considerations
NonBacktracking is <u>not</u> compatible with:
- `RegexOptions.RightToLeft`
- `RegexOptions.ECMASCript`
- Atomic groups
- Backreferences
- Balancing groups
- Conditionals
- Lookarounds
- Start anchors (\G)

If a capture group is in a loop, `NonBacktracking` will only return the last matched value for that capture.  This is different from the normal behavior of returning all matched values.

## Timeouts
Always set a timeout to minimize effect of excessive backtracking, if it occurs.  

Setting a timeout value:
- The `Regex` type has an overloaded constructor that accepts a `TimeSpan` value.
- The `Regex.Match` and `Regex.Replace` methods have an overload that include a `matchTimeout` parameter.
- Set process-wide or AppDomain-wide timeouts:
  - `AppDomain.CurrentDomain.SetData("REGEX_DEFAULT_MATCH_TIMEOUT", TimeSpan.FromMilliseconds(timeoutValueInMilliseconds));`

If timeouts are reached, a `RegexMatchTimeoutException` is thrown.

## Capturing Groups
Use capturing groups such as `(subexpression)` and `(?<name>subexpression)` only when necessary and disable otherwise. These constructs are expensive.  

Options to disable:
- Use `(?:subexpression)` which prevents the capture of matched substrings (does not disable substring captures in nested groups).
- Use the `ExplicitCapture` option which disables all unnamed or implicit captures in the the regular expression pattern.