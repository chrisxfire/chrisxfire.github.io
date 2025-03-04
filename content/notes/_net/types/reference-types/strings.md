---
title: strings
date: 2021-11-06T16:38:02-0600
draft: false
weight: 1
tags:
 - kb/dotnet/types/reference/strings
---

# [Strings](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-8.0)
A sequence of UTF-16 code units.  
Stored internally as a sequential read-only collection of `Char` objects.  
- `Length` property represents the number of `Char` objects contained, not the number of code units.
- To access the individual code points, use `StringInfo`

The `string` keyword looks like a type but is actually an alias for the type `String`.

> [!TIP] See also: https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/strings/

# empty strings
Empty strings are represented as `""`  
However, to create empty strings, use the constant `String.Empty`. This avoids null reference exceptions.  

# comparisons
## Case-sensitive, Ordinal Comparisons
Although `String` is a reference type, the equality operators `==` and `!=` are defined to compare the values of `string` objects, not references.
This makes the equality testing *value* based.

- `String.Equals`
- `==` (`String.Equality`)
- `!=` (`String.Inequality`)

## Case-insensitive, Ordinal Comparisons
```cs
string1.Equals(string2, StringComparison.OrdinalIgnoreCase)  
String.Compare(string1, string2, StringComparison.OrdinalIgnoreCase)  
```

# constructing
```cs
string x; // declare without initializing
string? y = null; // initialize to null
string z = string.Empty; // initialize as an empty string
string foo = "some string"; // initialize with a regular string literal
System.String bar = "some other string"; // initialize with System.String instead of the string keyword
string baz = @"C:\Windows\System32"; // initialize with a verbatim string literal

char[] letters = { 'A', 'B', 'C' };
string x = new string(letters); // Use the constructor only when creating a string from a char*, char[], or sbyte*.

# accessing
Use `String.IsNullOrEmpty(string)` to verify the value of a string before accessing it.

# formatted strings
Use `string.Format()` for formatted strings:
```cs
string result = string.Format("{0} and {1}", var1, var2)
```

## formats
| format                      | output                            |
| --------------------------- | --------------------------------- |
| `d`                         | 6/15/2009                         |
| `D`                         | Monday, June 15, 2009             |
| `f`                         | Monday, June 15, 2009 1:45 PM     |
| `F`                         | Monday, June 15, 2009 1:45:30 PM  |
| `g`                         | 6/15/2009 1:45 PM                 |
| `G`                         | 6/15/2009 1:45:30 PM              |
| `M`/`M`                     | June 15                           |
| `O`/`o` (roundtrip pattern) | 2009-06-15T13:45:30.0000000-07:00 |
| `R`/`r` (RFC1123 pattern)   | Mon, 15 Jun 2009 20:45:30 GMT     |
| `s` (sortable pattern)      | 2009-06-15T13:45:30               |
| `t`                         | 1:45 PM                           |
| `T`                         | 1:45:30 PM                        |
| `u` (universal sortable)    | 2009-06-15 13:45:30Z              |
| `U` (universal full)        | Monday, June 15, 2009 8:45:30 PM  |
| `Y`                         | June 2009                         |

## numeric formats
| format  | output             |
| ------- | ------------------ |
| `C`/`c` | $123.46            |
| `D`/`d` | 1234               |
| `E`/`e` | 1.052033E+003      |
| `F`/`f` | 1234.57            |
| `G`/`g` | -123.456           |
| `N`/`n` | 1,234.57           |
| `P`/`p` | 100.00 %           |
| `R`/`r` | 123456789.12345678 |
| `X`/`x` | FF                 |

Currency: 
- `{var1:C}`

Dates:
- `{var1:d}` (mm/dd/yyyy)
- `{var1:D}` (dayname, month dd, yyyy)

Times:
- `{var1:t}` (h:mm AM)
- `{var1:T}` (h:mm:ss AM)

Numbers:
- `{var1:N}` (thousands separators, 2 digits of precision)
- `{var1:N4}` (thousands separators, 4 digits of precision)

Percentage:
- `{var1:P2}` (2 digits of precision)

## alignment
Alignment is expressed as a signed integer $n$ indicating preferred field width:
- If $n$ is less than the length of the string, it is ignored.  
- If $n$ is positive, the field is right-aligned.  
- If $n$ is negative, the field is left-aligned.  

# [Interpolated Strings](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated)
String interpolation achieves the same results as string formatting.  

Use `$` for interpolated strings: `interpolationExpression,alignment:formatString`

## interpolated strings with newlines
> [!IMPORTANT]
> Availability: C# 11: Newlines are permitted in string interpolations. 

## [Constant Interpolated Strings](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/const)
> [!IMPORTANT]
> Availability: C# 10

Interpolated strings may be declared as `const` if all their placeholders are also `const`:
```cs
const string Language = "C#";
const string Platform = ".NET";
const string FullProductName = $"{Platform} - Language: {Language}";
```

## ternary operator in interpolated expression
Since `:` has special meaning in interpolation expressions, when using it as the conditional operator, wrap it in parentheses:
```cs
$"My house is: {(a < 1 ? "red" : "blue")}"
```

# verbatim strings
Verbatim strings will keep their whitespace and print escapes verbatim:  
```cs
Console.WriteLine(@" c:\source\repos(this is where your code goes)");
```

Verbatim and interpolated strings can be combined.

Use double quotation marks to embed a literal quotation mark in a verbatim string.

# raw string literals
> [!IMPORTANT]
> Availability: C# 11  

Raw string literals eliminate all need to escape content. They:
- Start with at least three quotes (`"""`)
- End in the same number of quotes

Newlines following the opening quote and preceding the closing quote are not included in the content.

## raw string literals and string interpolation
> [!IMPORTANT]
> Availability: C#11

Use multiple `$` characters to denote how many consecutive braces start/end an interpolation.  
In this example, two braces start/end an interpolation and the third is printed:
```cs
var location = $$"""
    You are at {{{Longitude}}, {{Latitude}}}
""";
```

# UTF-8 String Literals
> [!IMPORTANT]
> Availability: C# 11  
By default, strings in .NET are stored in UTF-16 encoding.  To encode a string as UTF-8, suffix it with `u8`:
```cs
ReadOnlySpan<byte> AuthWithTrailingSpace = new byte[] { 0x41, 0x55, 0x54, 0x48, 0x20 };
ReadOnlySpan<byte> AuthStringLiteral = "AUTH "u8;
byte[] AuthStringLiteral = "AUTH "u8.ToArray();
```

Notes:
- UTF-8 string literals cannot be combined with string interpolation.
- UTF-8 string literals cannot be used as the default value for an optional parameter (they are runtime constants, not compile-time constants).

# unicode escape sequences
`\unnnn`

# Encoding / Decoding Strings
```cs
string someString = "This is some string.";
Encoding encoder = Encoding.ASCII; // Or .UTF7, .UTF8, .Unicode, .UTF32, .Default (which is UTF-8)
byte[] encoded = encoder.GetBytes(someString); // Encode the string into a byte array.
encoded.Length; // Returns the number of bytes the encoding needed.
string decoded = encoder.GetString(someString); // Decode the byte array back into a string.
```

# properties
- `Length` — Return the length of the string.  

# methods
- `String.IsNullOrEmpty(string)` — Boolean if string is null or empty.  
- `String.IsNullOrWhiteSpace(string)` — Boolean if string is null or whitespace.  
- `String.Join("sep", collection)` — Concatenates elements of collection and separates each with sep.  
- `String.Concat(str1, str2)` — Concatenates two string variables. Same as + operator.  
  - .NET creates a new string in memory. Poor performance in loops.  

## searching
- `Contains("substr")` — Boolean if str is in string.  
- `StartsWith("substr")` — Boolean if string starts with str.  
- `EndsWith("substr")`  
- `IndexOf("substr")` — Return the index of the first occurrence of substr in string.  
- `LastIndexOf("substr")` — Return the index of the last occurrence of substr in string.  
- `IndexOfAny("substr")` — Return the index of the first occurrence of any of substr where substr is a comma-separated list.  
- `Substring(s, n)` — Return the substring at starting index s extending for n characters.  

## manipulating
All methods and operators that appear to modify a string actually  — return a new string object.

- `Insert`
- `Remove(s, n)` — Remove the substring starting at index s for n characters.  
- `Replace("substr1", "substr2", ignoreCase=)` — Replace substr1 with substr2.  
  - `ignoreCase` is boolean and optional.  
  - If `substr2` is null, all occurrences of `substr1` are removed.  
- `Split("delim", options)` — Returns a string array containing subsets of the string split at delim.  
  - options can be `StringSplitOptions.RemoveEmptyEntries` and `TrimEntries`  
- `ToCharArray()` — Convert the string to a character array  
  - This allows you to use array methods like `Reverse()`  
- `ToLower()` — Return a lowercased string.  
- `ToUpper()` — Return an uppercased string.  
- `Trim('c')` — Return a string with character c trimmed.  

## whitespace
- `PadLeft(n, char)` — Add n spaces to the left. Optionally, use char instead of spaces.  
- `PadRight(n, char)`  
- `TrimStart() `— Return a string with leading whitespace trimmed.  
- `TrimEnd()` — Return a string with trailing whitespace trimmed.  
- `Trim()` — Return a string with leading and trailing whitespace trimmed.  

# determine if string represents numeric value
Use `TryParse` methods of numeric types.
