---
title: "notes > ahk > scripting"
date: 2023-04-26T13:15:39-0600
draft: true
---
# Comments
; This is a comment

/* This is also a comment */ …but the comment does not end here.

# Escapes
`" escapes a quote
`t tab
`n linefeed
`r carriage return

# Variables
## Assignment
`MyVar := "Some text"`

`"The value is " MyVar` ; this will be implicitly concatenated

## Format function
To format strings:
`MsgBox Format("You are using AutoHotkey v{1} {2}-bit.", A_AhkVersion, A_PtrSize*8)`

# Operators
## Ternary
`condition ? valueIfTrue : valueIfFalse`

# Functions
Parentheses can be omitted if a function call is a single line:
`MsgBox "This doesn't need parantheses."`

`GetKeyState("Shift")` ; returns 1 if true

## Optional Parameters
`Run "notepad.exe", "C:\`
`Run "notepad.exe",, "Min"` ; the delimiting comma is needed to make "Min" the 3rd argument
`Run("notepad.exe", , , &notepadPID)`