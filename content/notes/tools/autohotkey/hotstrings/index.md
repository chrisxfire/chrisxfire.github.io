---
title: notes > tools > autohotkey > hotstrings
date: 2023-04-26T14:05:45-0600
draft: false
---
# Definition
```autohotkey
:options:abbreviation::replacement text
```
# Creating
```autohotkey
::btw::by the way
```
Typing "btw" followed by an ending character triggers this hotstring.

```autohotkey
::]d:: ; This hotstring replaces "]d" with the current date and time via the functions below.
{
    SendInput FormatTime(, "M/d/yyyy h:mm tt") ; It will look like 9/1/2005 3:53 PM
}
```

## Ending Characters
`-` `(` `)` `[` `]` `{` `}` ` `:` `;` ` `/` `\` `,` `.` `?` `!` `<enter>` `<tab>`

# Long Replacements
Use paranthesis:
```autohotkey
::text1::
(
Any text between the top and bottom parentheses is treated literally.
By default, the hard carriage return (Enter) between the previous line and this one is also preserved.
By default, the indentation (tab) to the left of this line is preserved.
)
```

# Options
`-` — ending character not required  
`C` — case-sensitive  
`?` — hotstring will be triggered even if its preceding characters are alphanumeric  
`B0` — disable automatic backspacing of abbreviation  
`Kn` — delay between keystrokes (including auto-backspacing and auto replacement)  
- Use k10 for 10ms delay and k-1 for no delay  
`T` — text mode; don't translate <kbd>Enter</kbd> to Enter or ^c to <kbd>Ctrl</kbd> + <kbd>C</kbd>  
`X` — execute; inside of replacement text, the hotstring accepts a function call or expression to execute  

# Context-sensitive Hotstrings
```autohotkey
#HotIf WinActive("ahk_class Notepad")
::btw::This replacement text will appear only in Notepad.
#HotIf
::btw::This replacement text appears in windows other than Notepad.
```
