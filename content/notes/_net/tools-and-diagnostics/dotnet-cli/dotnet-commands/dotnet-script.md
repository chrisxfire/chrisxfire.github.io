---
title: dotnet script
date: 2024-12-09T00:00:00-06:00
draft: false
weight: 1
tags: 
 - kb/dotnet/dotnet-cli/dotnet-script
---

# [Overview](https://github.com/dotnet-script/dotnet-script)
A tool to create and run C# scripts from the .NET CLI including VS Code debugging support.

# Installation
Windows:
```powershell
dotnet tool install -g dotnet-script
```

Linux/OSX:
```bash
curl -s https://raw.githubusercontent.com/dotnet-script/dotnet-script/master/install/install.sh | bash
```

# Creating scaffolding
1. Create a folder (e.g. "/scripts").
2. In that folder, run `dotnet script init`

This creates:
- /scripts/
    - .vscode/
        - launch.json
    - main.csx
    - omnisharp.json

# Writing scripts
This tool implicitly imports the following namespaces:
- System
- System.IO
- System.Collections.Generic
- System.Console
- System.Diagnostics
- System.Dynamic
- System.Linq
- System.Linq.Expressions
- System.Text
- System.Threading.Tasks

On OSX/Linux, ensure the first line in the script is the shebang directive:
```sh
#!/usr/bin/env dotnet-script
```

## Arguments
Arguments passed to scripts can be accessed via the global `Args` collection:
```cs
foreach (var arg in Args)
{
    Console.WriteLine(arg);
}
```

## Importing packages in scripts
Packages can be imported directly in the script:
```powershell
#r "nuget: AutoMapper, 6.1.0"
```

# Executing scripts
## Windows
```powershell
dotnet script file.csx -- arg1 arg2 arg3
```

Or, 
```powershell
dotnet-script file.csx -- arg1 arg2 arg3
```

Or, register dotnet-script in the registry as the tool to process .csx files:
```powershell
dotnet script register
```

Then:
```powershell 
file.csx arg1 arg2 arg3
```

## OSX/Linux
```bash
chmod +x file.csx
file.csx arg1 arg2 arg3
```

# Creating executables from scripts
```powershell
dotnet script
    --output # path where published executable should be placed (default = ./publish)
    --name # name of executable
    --dll # publish to dll instead of executable
    --configuration <release|debug> # configuration to use for publishing (default = debug)
    --debug # enables debug output
    --runtime <runtime> # specifies the runtime to use (default = current runtime)
```

# Running executables
Executables can be run natively.  
DLLS can be run via:
```powershell
dotnet script exec <path> -- arg1 arg2 arg3
```
# Debugging scripts
1. Add this `launch.config`:
    ```json
    {
        "name": ".NET Core Attach",
        "type": "coreclr",
        "request": "attach",
        "processId": "${command:pickProcess}"
    }
    ```
2. Attach the debugger by adding this method to the script:
   ```cs
   public static void WaitForDebugger()
    {
        Console.WriteLine("Attach Debugger (VS Code)");
        while(!Debugger.IsAttached)
        {
        }
    }
    ```
3. Call `WaitForDebugger()` in the script.
4. Set a breakpoint in VS Code.
5. Select the `.NET Core Attach` debugger in VS Code.

# REPL
To start the repl:
```powershell
dotnet script
```

Any expression not terminated with `;` is instead evaluated:
```powershell
> var x = 1;
> x+x
2
```

Uncompleted code blocks are detected and multiline mode (signified by `*`) is automatically entered:
```powershell
> class Foo {
* public string Bar {get; set;}
* }
> var foo = new Foo();
```

## REPL commands
| Command  | Description                                                  |
| -------- | ------------------------------------------------------------ |
| `#load`  | Load a script into the REPL (same as #load usage in CSX)     |
| `#r`     | Load an assembly into the REPL (same as #r usage in CSX)     |
| `#reset` | Reset the REPL back to initial state (without restarting it) |
| `#cls`   | Clear the console screen without resetting the REPL state    |
| `#exit`  | Exits the REPL                                               |

## Seeding REPL with a script
A REPL can be started with the contents of a script:
```powershell
dotnet script foo.csx -i
```

Alternatively, seed the REPL from inside the REPL:
```powershell
#load "foo.csx"
```

# Piping in data
Data can be piped into a script:
```powershell
echo "This is some text" | dotnet script file.csx
```