---
title: sending keystrokes
date: 2023-04-26T14:21:17-0600
draft: false
weight: 1
---

# sending keystrokes
## sendtext 
To send a string:
```autohotkey
^1::SendText "To whom it may concern"
^2::SendText "Send a "quoted string""
```

## sending long text
```autohotkey
SendText "
(
Leading indentation is stripped out,
based on the first line.
Line breaks are kept
unless you use the "Join" option.
)"
```

## send 
To send keystrokes:  

`^+{Left} `produces <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Left arrow</kbd>  
`^{+}{Left}` produces <kbd>Ctrl</kbd> + <kbd>+</kbd> followed by <kbd>Left arrow</kbd>  
`^+Left` produces <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + `L` followed by `eft`  

`^+"::Send '""{Left}'` — sends to quote marks then moves the cursor to the left once
