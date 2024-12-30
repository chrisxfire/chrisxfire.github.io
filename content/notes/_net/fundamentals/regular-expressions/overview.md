---
title: regular expressions
date: 2022-01-22T08:22:40-0700
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expressions)]
The .NET regular expression engine is a backtracking regular expression matcher. It employs a nondeterministic finite automation (NFA) engine 
like that used in Perl, Python, and other languages. 

| Regex Engine Type <br />  [[more information](https://learn.microsoft.com/en-us/dotnet/standard/base-types/details-of-regular-expression-behavior)] | Examples                | Processing <br /> driven by... | Guaranteed to <br /> find longest <br /> match possible | May test same <br /> character twice | Supports <br /> backtracking | Can match <br /> backreferences | Can capture <br /> sub-expressions |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ------------------------------ | ------------------------------------------------------- | ------------------------------------ | ---------------------------- | ------------------------------- | ---------------------------------- |
| Deterministic <br /> Finite <br /> Automation                                                                                                       | .NET, Perl, Python, Tcl | Input string                   | Yes                                                     | No (faster)                          | No                           | No                              | No                                 |
| Traditional <br /> Nondeterministic <br /> Finite <br /> Automation                                                                                 | awk, egrep, lex         | Regular expression pattern     | No                                                      | Yes (slower)                         | Yes                          | Yes                             | Yes                                |
| POSIX <br /> Nondeterministic <br /> Finite <br /> Automation                                                                                       | N/A                     | Regular expression pattern     | Yes                                                     | Yes (slowest)                        | Yes                          | Yes                             | Yes                                |

In .NET, the regular expression engine needs a minimum of two pieces of information:
1. The regular expression pattern to identify the text.
2. The text to parse for the regular expression.

.NET's regex implementation is compatible with Perl 5.

# create a regex
```cs
public class Foo 
{
    public Regex regex = new Regex(@"abc|def", RegexOptions.IgnoreCase);

    public bool Bar(string input) 
    {
        bool isMatch = regex.IsMatch(input);
        // ...
    }
}
```

# [System.Text.RegularExpressions](https://docs.microsoft.com/en-us/dotnet/api/system.text.regularexpressions.regex?view=net-6.0)
The `Regex` type in this class represents the .NET regular expression engine. It can perform the following operations:
* `Regex.IsMatch(input, pattern)` — determine if the regular expression pattern occurs in the text.
* `Regex.Match(input, pattern)` — retrieve one occurrence of a match and return it in a `RegularExpressions.Match` object.
* `Regex.Matches(input, pattern)` — retrieve all occurrences of a match and return them in a `RegularExpressions.MatchCollection` object.
*   Note: `MatchCollection` is empty if no matches were found.
*   Note: By default, this method uses lazy evaluation to populate the `MatchCollection`. Use `foreach` to traverse the collection.
* `Regex.Replace(input, pattern)` — replace text that matches the regular expression pattern

## `Match` 
The result of a single regex match.
* `Match.Success` — bool if a match was found
* `Match.NextMatch()` — return the next substring of input that matches pattern
* `Match.Groups` — a `GroupCollection` object that contains information about the substrings that match capturing groups used in the regex pattern
* `Match.Value` — a substring in input that matches pattern
* `Match.Index` — the zero-based index of the matched substring in input

## `MatchCollection`
A collection of `Match` objects representing all the matches found in the order in which they occur in the input string.
- This object is empty if no matches are found.

## `GroupCollection`
A collection of Group objects that represent captured groups from a single match:
* `Group.Value` — the captured substring
* `Group.Index` — the starting position of the captured group in the input text
* `Group.Length` — the length of the captured substring
* `Group.Success` — bool if a substring matched the pattern defined by the capturing group

`GroupCollection[0]` is the entire match. Each following element is the result of a single capture group.  

Unnamed groups can be retrieved via their index.
- They appear first in the collection.
- Calling `Regex.GetGroupNumbers()` returns what numbered groups are available.

Named groups can be retrieved via their name or index.
- Calling `Regex.GetGroupNames()` returns what named groups are available.

## `Group`
The result from a single capturing group.

# miscellaneous
* `System.Web.RegularExpressions` contains RegEx options that implement predefined RegEx patterns for parsing HTML, XML, and other structured documents.
* `System.Configuration.RegexStringValidator` — validate a string against the rules of a regular expression.
* Regular expression pattern examples:
  * [Finding HREFs](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-example-scanning-for-hrefs)
  * [Find Protocol and Port Number from URL](https://learn.microsoft.com/en-us/dotnet/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url)
  * [Strip Invalid Characters from String](https://learn.microsoft.com/en-us/dotnet/standard/base-types/how-to-strip-invalid-characters-from-a-string)
  * [Verify Email Addresses](https://learn.microsoft.com/en-us/dotnet/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format)
  * [Others](https://www.regular-expressions.info/examples.html)