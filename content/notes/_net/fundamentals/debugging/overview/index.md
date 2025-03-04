---
title: overview
date: 2022-01-01T00:00:00-06:00
draft: false
weight: -1
---

# breakpoint
Stop execution when this is reached to allow you to inspect the state.

## Add/remove a breakpoint
Click to left of line number (red dot).

# conditional breakpoint
Stop execution only if condition is true.

## Add/remove a conditional breakpoint
Right-click to the left of the line number.

# watch panel
Track a variable state across time or functions.
- Click **+** button to add a variable to watch, or;
- Right-click variable in Variables panel and select **Add to watch**.
	
# call stack panel
![call stack panel](./call-stack-panel.png)  
Shows stack trace but only those from the code (not the runtime).

## control execution
- **Continue**/**pause**
- **Step over** – execute the next code statement.
- **Step into** – like Step over, but if next statement is a function call, move to the first code statement of this function.
- **Step out** – if in a function, execute the remaining code in the function then move to the statement after the function call.
- **Restart**
- **Stop**

Debug Console – <kbd>Ctrl+Shift+Y</kdb>
- You can enter expressions into the console which will be evaluated against the current state.

# defensive programming
- A way of programming where the application behaves in a consistent, predictable manner, regardless of input.
- All edge cases are tested and functions have clear requirements.
- Input is validated.

# methods
```cs
Assert(condition, "message");
Write
WriteLine
WriteIf(condition, "message");
WriteLineIf(condition, "message");
```
