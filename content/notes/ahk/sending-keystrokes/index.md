---
title: "notes > ahk > sending keystrokes"
date: 2023-04-26T14:21:17-0600
draft: true
---
# Sending Keystrokes
## SendText 
To send a string:
`^1::SendText "To whom it may concern"`
`^2::SendText "Send a `"quoted string`""`

## Sending Long Text
`SendText "`
`(`
`Leading indentation is stripped out,`
`based on the first line.`
`Line breaks are kept`
`unless you use the "Join" option.`
`)"`


## Send 
To send keystrokes:
`^+{Left}` produces `Ctrl` + `Shift` + `Left arrow`
`^{+}{Left}` produces `Ctrl` + `+` followed by `Left arrow`
`^+Left` produces `Ctrl` + `Shift` + `L` followed by "eft"

`^+"::Send '""{Left}'` — sends to quote marks then moves the cursor to the left once