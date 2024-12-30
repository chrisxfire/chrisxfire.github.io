---
title: scripting
date: 2023-04-26T13:15:39-0600
draft: false
weight: 1
---

# comments

; This is a comment

/* This is also a comment */ …but the comment does not end here.

# escapes
- ``"` escapes a quote  
- ``t` tab  
- ``n` linefeed  
- ``r` carriage return  

# variables
## assignment
```autohotkey
MyVar := "Some text"

"The value is " MyVar ; this will be implicitly concatenated
```

## format function
To format strings:
```autohotkey
MsgBox Format("You are using AutoHotkey v{1} {2}-bit.", A_AhkVersion, A_PtrSize*8)
```

# operators
## ternary
```autohotkey
condition ? valueIfTrue : valueIfFalse
```

# functions
Parentheses can be omitted if a function call is a single line:
```autohotkey
MsgBox "This doesn't need parantheses."

GetKeyState("Shift") ; returns 1 if true
```

## optional parameters
```autohotkey
Run "notepad.exe", "C:\
Run "notepad.exe",, "Min" ; the delimiting comma is needed to make "Min" the 3rd argument
Run("notepad.exe", , , &notepadPID)
```
