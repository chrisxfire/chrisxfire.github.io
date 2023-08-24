---
title: regular expressions
date: 2022-01-22T08:22:40-0700
draft: false
weight: 1
---

# [System.Text.RegularExpressions](https://docs.microsoft.com/en-us/dotnet/api/system.text.regularexpressions.regex?view=net-6.0)
Represents the .NET regular expression engine.  

Instantiating a regular expression object is an expensive operation.

# Regular Expression Engine Performance Considerations
Four techniques for coupling the regex engine to a regex pattern:
1.  Call a static pattern-matching method  
2.  Instantiate a RegEx object <u>without</u> a `Compiled` option
3.  Instantiate a RegEx object <u>with</u> a `Compiled` option
4.  Create a RegEx object and save it to a standalone assembly

## Using Static Regular Expressions (#1)
This is inefficient:
```cs
public static bool IsValidCurrency(string currencyValue)
{
    string pattern = @"\p{Sc}+\s\d+";
    Regex currencyRegex = new Regex(pattern); // This object is instantiated each time the method is called
    return currencyRegex.IsMatch(currencyValue);
}
```

By default, the last 15 most recently used static regular expression patterns are cached. This is controlled by `RegEx.CacheSize`.
That makes this static call to `Regex.IsMatch` is efficient:
```cs
public static bool IsValidCurrency(string currencyValue)
{
    string pattern = @"\p{Sc}+\s\d+";
    return Regex.IsMatch(currencyValue, pattern);
}
```

## Interpreted (#2) vs. Compiled (#3) Regular Expressions
| Type        | Startup | Execution | Use when                                                 |
| ----------- | ------- | --------- | -------------------------------------------------------- |
| Interpreted | Faster  | Slower    | Calling regex methods with a specific regex infrequently |
| Compiled    | Slower  | Faster    | Calling regex methods with a specific regex frequently   |

## Backtracking
Ordinarily, the regex engine uses linear progression to traverse an input string and compare it to a regex pattern. Indeterminate quantifiers like `*`, `+`, and `?` allow the regex engine to give up a partial successful match to search for a successful match in the entire pattern. This is *backtracking*.  

Backtracking can significantly degrade performance. Worst case, execution time doubles for each additional character in input.
If backtracking is not necessary, either:
1. Disable it with an atomic group: `(?>subexpression)`, or;
2. Pass `RegexOptions.NonBacktracking`.  This guarantees linear progression and avoids backtracking.

### Nonbacktracking Mode Considerations
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
Use capturing groups such as `(subexpression)` and `(?<name>subexpression)` only when necessary and disable otherwise. These language elements are expensive.  

Options to disable:
- Use `(?:subexpression)` which prevents the capture of matched substrings (does not disable substring captures in nested groups).
- Use the ExplicitCapture option which disables all unnamed or implicit captures in the the regular expression pattern.

# Character Escapes
| Escaped char | Matches         | Notes            |
| ------------ | --------------- | ---------------- |
| `\a`         | Bell character  |                  |
| `\b`         | Backspace       |                  |
| `\t`         | Tab             |                  |
| `\r`         | Carriage return | `\r` is not `\n` |
| `\v`         | Vertical tab    |                  |
| `\f`         | Form feed       |                  |
| `\n`         | Newline         |                  |
| `\e`         | Escape          |                  |

# Character Classes
| Class    | Matches any single…                          | Example                          |
| -------- | -------------------------------------------- | -------------------------------- |
| `[ae]`   | character in the group (case-sensitive)      | "a" in "gray"                    |
| `[^aei]` | character NOT in the group (case-sensitive)  | "r" "g" "n" in "reign"           |
| `[A-Z]`  | character in the range                       | "A" "B" in "AB123"               |
| `a.e`    | character except `\n`                        | "ate" in "water"                 |
| `\p{Lu}` | character in the Unicode category of Lu      | "C" "L" in "City Lights"         |
| `\P{Lu}` | character NOT in the Unicode category Lu     | "i" "t" "y" in "City"            |
| `\w`     | "word" character (alphanumeric)              | "I" "D" "A" "1" "3" in "ID A1.3" |
| `\W`     | non-word character                           |                                  |
| `\s`     | white-space character [cr/nl/ff, tab, space] |                                  |
| `\S`     | non-white-space character                    |                                  |
| `\d`     | digit [0-9]                                  |                                  |
| `\D`     | character NOT a digit                        |                                  |

## Character Class Subtraction
`[base_group-[excluded_group]]`  

| Use         | to match                           |
| ----------- | ---------------------------------- |
| `[a-z-[m]]` | any character from a to z except m |

## Custom Character Classes
- `[aeiouAEIOU]` matches any vowel, both lowercase and uppercase.
- `[a-zA-Z0-9]` matches any lowercase letter, uppercase letter, or digit.

# Anchors
Anchors cause a match to succeed or fail depending on the current position, but do not advance through the string.
| Anchor      | Match must…                                         | Example | Matches                                |
| ----------- | --------------------------------------------------- | ------- | -------------------------------------- |
| `^` or `\A` | start at beginning of string                        |         |                                        |
| `$` or `\Z` | occur at the end of the string or before the \n     |         |                                        |
| `\z`        | occur at the end of the string                      |         |                                        |
| `\G`        | occur at point where previous match ended           | \G\\d\  | "(1)" "(3)" "(5)" in `(1)(3)(5)[7](9)` |
| `\b`        | occur on a boundary between a \w and a \W character |         |                                        |
| `\B`        | NOT occur on a \b boundary                          |         |                                        |

# Groupings
| Construct                 | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| `(subexpression)`         | Capture the matched subexpression and assign it a 1-based ordinal |
| `(?<name> subexpression)` | Capture the matched subexpression into a named group              |
| `(?'name' subexpression)` | Same                                                              |
| `(?: subexpression)`      | A non-capturing group                                             |
| `(?> subexpression)`      | An atomic group                                                   |

# Lookahead & Lookbehind Assertions
Lookahead and lookbehind assertions are anchors that, without moving the pointer, look ahead or behind to test a condition.

| Construct     | Name                | Description                                                                      |
| ------------- | ------------------- | -------------------------------------------------------------------------------- |
| `(?= check)`  | Positive lookahead  | Assert what immediately follows the current position in the string is check      |
| `(?! check)`  | Negative lookahead  | Assert what immediately follows the current position in the string is NOT check  |
| `(?<= check)` | Positive lookbehind  | Assert what immediately precedes the current position in the string is check     |
| `(?<! check)` | Negative lookbehind | Assert what immediately precedes the current position in the string is NOT check |

# Quantifiers
| Quantifier   | Matches the previous element…                       | Pattern     | Matches                  |
| ----------- | --------------------------------------------------- | ----------- | ------------------------ |
| \` (greedy) | zero or more times                                  | `a.c`       | "abcbc" in "abcbc"       |
| `?` (lazy)  | zero or more times, but as few times as possible    | `a.?c`      | "abc" in "abcbc"         |
| `+`         | one or more times                                   | `be+`       | "bee" in "been"          |
| `+?`        | one or more times, but as few times as possible     | `"be?"`     | "be" in "been"           |
| `?`         | zero or one time                                    | `"rai?"`    | "rai" in "rain"          |
| `??`        | zero or one time, but as few times as possible      | `"rai??"`   | "ra" in "rain"           |
| `{n}`       | exactly n times                                     | `",\d{3}"`  | ",043" in "1,043.6"      |
| `{n}?`      | exactly n times                                     | `",\d{3}"`  | ",043" in "1,043.6"      |
| `{n,}`      | at least n times                                    | `"\d{2,}"`  | "166"                    |
| `{n,}?`     | at least n times, but as few times as possible      | `"\d{2,}"`  | "166"                    |
| `{n,m}`     | between n and m times                               | `"\d{3,5}"` | "19302" in "193024"      |
| `{n,m}?`    | between n and m times, but as few times as possible | `"\d{3,5}"` | "193", "024" in "193024" |

# Backreference Constructs
*Backreferences* allow a previously matched subexpression to be identified later in the same regular expression.  

| Construct  | Description                            |
| ---------- | -------------------------------------- |
| `\n`       | Match the value of subexpression n.    |
| `\k<name>` | Match the value of subexpression name. |

# [Alternation Constructs](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#alternation-constructs)

# [Substitutions](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#substitutions)

# Comments
- `(?# comment)` // an inline comment
- `# comment` // an end-of-line comment

# Create a Regex
```cs
public class Foo 
{
    public Regex regex = new Regex(@"abc|def", RegexOptions.IgnoreCase);

    public bool Bar(string input) 
    {
        bool isMatch = regex.IsMatch(input);
        // ..
    }
}
```

# Methods
```
Regex.IsMatch(input, pattern) // returns bool if pattern is matched in input
Regex.Match(input, pattern) // returns a Match object of the first match of pattern in input
Regex.Matches(input, pattern) // returns a MatchCollection (a collection of Match objects) of all matches of pattern in input or an empty collection
Regex.Replace(input, pattern, replacement)
```

# Match 
The result of a single regex match.
```cs
Match.Success // bool if a match was found
Match.NextMatch() // return the next substring of input that matches pattern
Match.Groups // a GroupCollection object that contains information about the substrings that match capturing groups used in the regex pattern
Match.Value // a substring in input that matches pattern
Match.Index // the zero-based index of the matched substring in input
```

# GroupCollection
A collection of Group objects that represent captured groups from a single match.
```cs
Group.Value // the captured substring
Group.Index // the starting position of the captured group in the input text
Group.Length // the length of the captured substring
Group.Success // bool if a substring matched the pattern defined by the capturing group
```
`GroupCollection[0]` is the entire match. Each following element is the result of a single capture group.  

Unnamed groups can be retrieved via their index.
- They appear first in the collection.
- Calling `Regex.GetGroupNumbers()` returns what numbered groups are available.

Named groups can be retrieved via their name or index.
- Calling `Regex.GetGroupNames()` returns what named groups are available.

# Group
The result from a single capturing group.
 
# Patterns
```cs
// Matches <<https://service5.ultipro.com/personnel/v1/employee-multi-phone-numbers?page=2&per_page=30>>; rel="next"
@"^<[\S]+>;\s+rel=""[\w]+""$"
```
