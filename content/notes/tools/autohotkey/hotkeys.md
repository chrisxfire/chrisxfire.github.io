---
title: hotkeys
date: 2023-04-26T13:57:43-0600
draft: false
weight: 1
---

# hotkeys
```autohotkey
hotkey-name::action

hotkey-name::
{
    if condition
    action ; comment
    else
    action
}
```

## examples
```autohotkey
#n:: Run "notepad" ; Win + N to run notepad.exe
#n::MsgBox ThisHotkey ; returns "#n"
```
`LButton` — left mouse button
`RButton` — right mouse button

# modifiers
- `LWin` — Left Winkey  
- `^` — Ctrl  
- `<^` — Left Ctrl  
- `!` — Alt  
- `!` Up — only fire when Alt is released (vs pressed)  
- `+` — Shift  
- `-` — hotkey will fire even if extra modifier keys are held  
- `~` — prevents hotkey from blocking the key's native function  
- `$` — if the script uses the Send function to send the keys that comprise of the hotkey itself, use this.  

Note: `:` is not a valid modifier

# Context-sensitive Hotkeys
```autohotkey
#HotIf WinActive("Notepad")
^a::MsgBox "You pressed Ctrl-A while Notepad is active. Pressing Ctrl-A in any other window will pass the Ctrl-A keystroke to that window."
#c::MsgBox "You pressed Win-C while Notepad is active."

#HotIf
#c::MsgBox "You pressed Win-C while any window except Notepad is active."
```

Use `WinExist` instead of `WinActive` to test for the presence of the app, even if it is not in focus

# custom hotkey combinations
`Numpad0 & Numpad1::` — fires when Numpad 0 and 1 are both depressed

Note: `Numpad0` will lose its native function—it is now a prefix key.
