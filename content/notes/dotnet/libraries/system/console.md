---
title: notes > .net > libraries > system > console
date: 2021-11-19T15:50:28-0700
draft: false
weight: 1
---
# [System.Console](https://docs.microsoft.com/en-us/dotnet/api/system.console?view=net-6.0)
`STDIN`, `STDOUT`, `STDERR` streams.  
`Object` –> `Console`

# Properties
- `BufferHeight` - Get or set the buffer height
- `BufferWidth`
- `CursorSize` - Get or set the size of the console cursor.
- `WindowHeight` - Get or set the console window height
- `WindowWidth`
- `WindowTop` - Get or set the top position of the console window.
- `WindowsLeft` - Get or set the left position of the console window.

# Colors
```cs
BackgroundColor = ConsoleColor.color
ForegroundColor = ConsoleColor.color
```

# Static Methods
- `Beep`
- `Beep(n, m)` - Beep at n frequency for m duration
- `Clear`
- `ResetColor`
- `ReadKey` - Read an individual character.
- `ReadLine` - Read a line of input.
- `SetBufferSize`
- `SetWindowSize`

# Reading Input
```cs
ConsoleKeyInfo key = ReadKey();
key.Key // returns key that was pressed
key.KeyChar // returns case-sensitive character that was pressed
key.Modifiers // returns modifiers (Control, Alt, Shift)
```

# Replace Line of Output
```cs
Console.Write("\r"); // Carrier Return; moves cursor back to position #1 on current line
```
