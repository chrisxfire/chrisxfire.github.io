---
title: regular expressions
date: 2022-01-22T08:22:40-0700
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expressions)]
In .NET, the regular expression engine needs a minimum of two pieces of information:
1. The regular expression pattern to identify the text.
2. The text to parse for the regular expression.

.NET's RegEx implementation is compatible with Perl 5.

# Create a Regex
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
* `Regex.Replace(input, pattern)` — replace text that matches the regular expression pattern

## `Match` 
The result of a single regex match.
* `Match.Success` — bool if a match was found
* `Match.NextMatch()` — return the next substring of input that matches pattern
* `Match.Groups` — a `GroupCollection` object that contains information about the substrings that match capturing groups used in the regex pattern
* `Match.Value` — a substring in input that matches pattern
* `Match.Index` — the zero-based index of the matched substring in input

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

# Regex Constructs 
## Character Escapes
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

## Character Classes
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

### Character Class Subtraction
`[base_group-[excluded_group]]`  

| Use         | to match                           |
| ----------- | ---------------------------------- |
| `[a-z-[m]]` | any character from a to z except m |

### Custom Character Classes
- `[aeiouAEIOU]` matches any vowel, both lowercase and uppercase.
- `[a-zA-Z0-9]` matches any lowercase letter, uppercase letter, or digit.

## Anchors
Anchors cause a match to succeed or fail depending on the current position, but do not advance through the string.
| Anchor      | Match must…                                         | Example | Matches                                |
| ----------- | --------------------------------------------------- | ------- | -------------------------------------- |
| `^` or `\A` | start at beginning of string                        |         |                                        |
| `$` or `\Z` | occur at the end of the string or before the \n     |         |                                        |
| `\z`        | occur at the end of the string                      |         |                                        |
| `\G`        | occur at point where previous match ended           | \G\\d\  | "(1)" "(3)" "(5)" in `(1)(3)(5)[7](9)` |
| `\b`        | occur on a boundary between a \w and a \W character |         |                                        |
| `\B`        | NOT occur on a \b boundary                          |         |                                        |

## Groupings
| Construct                 | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| `(subexpression)`         | Capture the matched subexpression and assign it a 1-based ordinal |
| `(?<name> subexpression)` | Capture the matched subexpression into a named group              |
| `(?'name' subexpression)` | Same                                                              |
| `(?: subexpression)`      | A non-capturing group                                             |
| `(?> subexpression)`      | An atomic group                                                   |

By default, groups are named with a number that matches the sequence in which they appear in the regular expression pattern. For
example, the pattern `(\w+?)` matches one or more (`+`) word characters (`\w`) but as few as possible (`?`).
Refer to this group via `\1`.

## Lookahead & Lookbehind Assertions
Lookahead and lookbehind assertions are anchors that, without moving the pointer, look ahead or behind to test a condition.

| Construct     | Name                | Description                                                                      |
| ------------- | ------------------- | -------------------------------------------------------------------------------- |
| `(?= check)`  | Positive lookahead  | Assert what immediately follows the current position in the string is check      |
| `(?! check)`  | Negative lookahead  | Assert what immediately follows the current position in the string is NOT check  |
| `(?<= check)` | Positive lookbehind | Assert what immediately precedes the current position in the string is check     |
| `(?<! check)` | Negative lookbehind | Assert what immediately precedes the current position in the string is NOT check |

## Quantifiers
| Quantifier | Matches the previous element…                       | Pattern     | Matches                  |
| ---------- | --------------------------------------------------- | ----------- | ------------------------ |
| `?` (lazy) | zero or more times, but as few times as possible    | `a.?c`      | "abc" in "abcbc"         |
| `+`        | one or more times                                   | `be+`       | "bee" in "been"          |
| `+?`       | one or more times, but as few times as possible     | `"be?"`     | "be" in "been"           |
| `?`        | zero or one time                                    | `"rai?"`    | "rai" in "rain"          |
| `??`       | zero or one time, but as few times as possible      | `"rai??"`   | "ra" in "rain"           |
| `{n}`      | exactly n times                                     | `",\d{3}"`  | ",043" in "1,043.6"      |
| `{n}?`     | exactly n times                                     | `",\d{3}"`  | ",043" in "1,043.6"      |
| `{n,}`     | at least n times                                    | `"\d{2,}"`  | "166"                    |
| `{n,}?`    | at least n times, but as few times as possible      | `"\d{2,}"`  | "166"                    |
| `{n,m}`    | between n and m times                               | `"\d{3,5}"` | "19302" in "193024"      |
| `{n,m}?`   | between n and m times, but as few times as possible | `"\d{3,5}"` | "193", "024" in "193024" |

## Backreference Constructs
*Backreferences* allow a previously matched subexpression to be identified later in the same regular expression.  

| Construct  | Description                            |
| ---------- | -------------------------------------- |
| `\n`       | Match the value of subexpression n.    |
| `\k<name>` | Match the value of subexpression name. |

## Comments
- `(?# comment)` // an inline comment
- `# comment` // an end-of-line comment

## [Alternation Constructs](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#alternation-constructs)

## [Substitutions](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#substitutions)

# Security
> When processing untrusted input, always pass a timeout.

A threat actor can pass malicious input, knowing that the input will be matched against a regular expression pattern, and cause a denial of service condition
by crafting that input to take excessively long to process.  A timeout mitigates this. 

# Miscellaneous
* `System.Web.RegularExpressions` contains RegEx options that implement predefined RegEx patterns for parsing HTML, XML, and other structured documents.