---
title: constructs
date: 2023-11-18T00:00:00-06:00
draft: false
weight: 1
---

# Abstract
These notes contain various .NET regular expression constructs used for forming regular expressions.

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

# Character Escapes
| Escaped char | Matches                                              |
| ------------ | ---------------------------------------------------- |
| `\a`         | Bell character                                       |
| `\b`         | Backspace                                            |
| `\t`         | Tab                                                  |
| `\r`         | Carriage return (note: this is not the same as `\n`) |
| `\v`         | Vertical tab                                         |
| `\f`         | Form feed                                            |
| `\n`         | Newline                                              |
| `\e`         | Escape key (\u001b)                                  |
| `\\`         | Back slash                                           |

# Character Classes
| Class    | Matches any single…                          |
| -------- | -------------------------------------------- |
| `[ae]`   | character in the group (case-sensitive)      |
| `[^aei]` | character NOT in the group (case-sensitive)  |
| `[A-Z]`  | character in the range                       |
| `.`      | character except `\n`                        |
| `\p{Lu}` | character in the Unicode category of Lu      |
| `\P{Lu}` | character NOT in the Unicode category Lu     |
| `\w`     | "word" character (alphanumeric)              |
| `\W`     | non-word character                           |
| `\s`     | white-space character [cr/nl/ff, tab, space] |
| `\S`     | non-white-space character                    |
| `\d`     | digit [0-9]                                  |
| `\D`     | non-digit character                          |

## Character Class Subtraction
`[base_group-[excluded_group]]`  

| Use         | to match                           |
| ----------- | ---------------------------------- |
| `[a-z-[m]]` | any character from a to z except m |

## Custom Character Classes
- `[aeiouAEIOU]` matches any vowel, both lowercase and uppercase.
- `[a-zA-Z0-9]` matches any lowercase letter, uppercase letter, or digit.

# Comments
 `(?# comment)` // an inline comment
 `# comment` // an end-of-line comment

# Conditional Evaluation
`(?(subexpression)yes|no)` or `?(name)yes|no)` where:
- *subexpression* is a subexpression to match
- *name* is a capturing group
- *yes* is the string to match if *subexpression* is matched OR if *name* is a valid, non-empty captured group
- *no* is the subexpression to match if *subexpression* is not matched OR *name* is not a valid, non-empty captured group 

Consider a text document with paragraphs marked with a \<PRIVATE\> tag, and this regex pattern that uses conditional evaluation
to assign the contents of paragraphs intended for public and private use to different capturing groups: 

`^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$`

The colors below are used to differentiate the various parts of this regular expression:
- Begin the match at the beginning of the line ( <r>^</r> )
- <c>(<y>?\<Pvt\>\\</y><PRIVATE\><bl>\s</bl>)<r>?</r></c> 
  - Match zero or one instances ( <c><r>?</c></r> ) 
    - of `<PRIVATE>` followed by a whitespace character ( <c><bl>\s</c></bl> )
  - and assign the match to a capturing group named `Pvt` ( <c>(<y>?\<Pvt\>\\</y></c> )
- <c>(?<y>(Pvt)</y><o>(</o>(<v>\w</v><r>+</r></bl><g>\p{P}</g><r>?</r><bl>\s</bl>)<in>+</in><o>)</o></c> 
  - If the `Pvt` capturing group exists ( <c><y>?(Pvt)</y></c> )
    - match one or more instances ( <c><in>+</in></c> ) 
      - of one or more ( <c><r>+</r></c> ) 
      - word characters ( <c><v>\w</v></c> ) 
      - followed by zero or one ( <c><r>?</c></r> )
      - punctuation characters ( <c><g>\p{P}</c></g> )
      - followed by a single whitespace character ( <c><bl>\s</c></bl> )
    - and assign the match to the first capturing group ( <c><o>()</o></c> )
- <c><r>|</r><o>(</o>(<v>\w</v><r>+</r></bl><g>\p{P}</g><r>?</r><bl>\s</bl>)<in>+</in><o>)</o></c>
  - Or if the `Pvt` capturing group does not exist ( <c><r>|</r></c> ),
    - match one or more instances ( <c><in>+</in></c> )
      - of one or more ( <c><r>+</r></c> )
      - word characters ( <c><v>\w</v></c> )
      - followed by zero or one ( <c><r>?</c></r> )
      - punctuation characters ( <c><g>\p{P}</c></g> )
      - followed by a single whitespace character ( <c><bl>\s</c></bl> ) 
- End the match at the end of a line ( <c><r>\r?</c></r> ) or the end of the string ( <c><r>$</c></r> )

Here is the same regular expression pattern again, this time with colorized brackets:

<c>^<r>(</r>?\<Pvt\>\\<PRIVATE\>\s<r>)</r>?<o>(</o>?<y>(</y>Pvt<y>)</y><g>(</g><bl>(</bl>\w+\p{P}?\s<bl>)</bl>+<g>)</g>|<in>(</in><v>(</v>\w+\p{P}?\s<v>)</v>+<in>)</in><o>)</o>\r?$</c>

# Grouping
## Atomic Group
A grouping construct that allows the backtracking engine to guarantee that a subexpression matches only the first match found for that subexpression:  
`(?> subexpression)`

For example, consider the regular expression `(a+)\w`:
- Matches one or more "a" characters ( `a+` )
- along with a word character that follows the sequence of "a" characters ( `\w` )
- and assigns the sequence of "a" characters to the first capturing group ( `()` )

However, if the last character of the input is also an "a", it is matched by `\w` and *not* included in the capture group.
The regular expression `((?>a+))\w` prevents this behavior because all consecutive "a" characters are matched without backtracking.

## Other Grouping Constructs
| Construct                 | Description                                                                                                                             |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `(subexpression)`         | Capture the matched *subexpression* and assign it a 1-based ordinal                                                                     |
| `(?<name> subexpression)` | Capture the matched *subexpression* into a named group                                                                                  |
| `(?'name' subexpression)` | Same                                                                                                                                    |
| `(?: subexpression)`      | A non-capturing group                                                                                                                   |
| `(?> subexpression)`      | An atomic group; allows backtracking engine to guarantee that a subexpression matches only the first match found for that subexpression |

By default, groups are named with a number that matches the sequence in which they appear in the regular expression pattern. For
example, the pattern `(\w+?)` matches one or more (`+`) word characters (`\w`) but as few as possible (`?`).
Refer to this group via `\1`.

# Lookahead & Lookbehind Assertions
Lookahead and lookbehind assertions are anchors that, without moving the pointer, look ahead or behind to test a condition. 

| Construct             | Name                | Description                                                                    | In other words...                                                 | Example use case                                                                   |
| --------------------- | ------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `(?= subexpression)`  | Positive lookahead  | Assert what follows the current position in the string is *subexpression*      | Match the expression if the *subexpression* matches               | Match words that are not followed by punctuation symbols: `@"\b[A-Z]+\b(?=\P{P})"` |
| `(?! subexpression)`  | Negative lookahead  | Assert what follows the current position in the string is NOT *subexpression*  | Match the expression if the *subexpression* <u>fails</u> to match | Match words that do not begin with "non": `@"\b(?!non)\w+\b"`                      |
| `(?<= subexpression)` | Positive lookbehind | Assert what precedes the current position in the string is *subexpression*     |                                                                   |
| `(?<! subexpression)` | Negative lookbehind | Assert what precedes the current position in the string is NOT *subexpression* |

# Quantifiers
*Lazy* quantifiers (`??`, `*?`, `+?`, `{n,m}?`) instruct the backtracking engine to search the minimum number of repetitions first, 
matching as few times as possible. Contrast with *greedy* quantifiers (`+`):
- In `.+(\d+)\.`, the *greedy* quantifier `.+` causes regex engine to capture only the last digit of a number.
- In `.+?(\d+)\.`, the *lazy* quantifier `.+?` causes regex engine to capture entire number. 

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

# Backreference Constructs
*Backreferences* allow a previously matched subexpression to be identified later in the same regular expression.  

| Construct  | Description                                               |
| ---------- | --------------------------------------------------------- |
| `\n`       | Match the value of subexpression *n* where *n* is a digit |
| `\k<name>` | Match the value of subexpression *name*                   |

# [Alternation Constructs](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#alternation-constructs)

# [Substitutions](https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference#substitutions)
| Character  | Description                                                      |
| ---------- | ---------------------------------------------------------------- |
| `$1`       | Substitutes the substring matched by matching group 1            |
| `${foo}`   | Substitutes the substring matched by matching group named `foo`  |
| `$$`       | Substitutes a literal "$" character                              |
| `$&`       | Substitutes a copy of the whole match                            |
| ``` $` ``` | Substitutes all of the text of the input string before the match |
| `$'`       | Substitutes all of the text of the input string after the match  |
| `$+`       | Substitutes the last group that was captured                     |
| `$_`       | Substitutes the entire input string                              |

# Best Practices
## Security
> When processing untrusted input, always pass a timeout.

A threat actor can pass malicious input, knowing that the input will be matched against a regular expression pattern, and cause a denial of service condition
by crafting that input to take excessively long to process.  A timeout mitigates this. 

## Regex vs String Methods
Use `String` methods when searching for a specific string.  
Use `Regex` 

## Use the Best Technique for a Specific Regex Operation
- Validate a match with `IsMatch()`.
- Retrieve a single match with `Match()`. Retrieve subsequent matches with `Match.NextMatch()`.
- Replace matched text with `Replace()`.
- Escape characters that may be interpreted as regex operators with `Escape()`. Or, remove them with `Unescape()`.

## Use Timeouts
- Use the `Regex(string, RegexOptions, TimeSpan)` constructor to pass a timeout value.
- Set application-wide timeout by calling `AppDomain.SetData("REGEX_DEFAULT_MATCH_TIMEOUT", TimeSpan)`.