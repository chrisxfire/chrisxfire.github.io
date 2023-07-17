---
title: notes > .net > libraries > system.commandline > overview
date: 2022-01-31T20:07:53-0700
draft: false
weight: -1
---
# [System.CommandLine](https://learn.microsoft.com/en-us/dotnet/standard/commandline/)
<o>Pre-release.</o>   
```powershell
dotnet add package system.commandline --pre-release
```

# Model Binding
The process of parsing arguments and providing them to command handler code.  
Of note, any type with a constructor that accepts a single string parameter can be bound (like `FileInfo`).

# Root Command
A root command, represented by `RootCommand`, represents the app executable itself:
```cs
RootCommand rootCommand = new("app description");
```

## Adding Commands to RootCommand
```cs
rootCommand.Add(someCommand);
```

# Commands
Commands are actions performed by the program. They should be verbs.  
Commands are represented by the Command class:  
```cs
Command actionCommand = new Command("actionCommand", "Perform an action.");
```

## Subcommands
Subcommands also use the `Command` class and can be added to a Command or RootCommand.

When commands have subcommands, the commands above them in the hierarchy do nothing:
```powershell
dotnet add # does nothing
dotnet add package # does something
```

Example:
```cs
rootCommand.Add(actionCommand);
Command subCommand = new Command("subcmd");
actionCommand.Add(subCommand);
```

`> myapp cmd subcmd`

Equivalent using collection initializer syntax:
```cs
RootCommand rootCommand = new RootCommand() 
{
    new Command("actionCommand") 
    {
        new Command("subcmd")
    }
};
```

# Options
Options are named parameters that can be passed to commands.

They are represented by the `Option` class:
```cs
Option<int> delayOption = new Option<int>(
    name: "--delay",
    description: "The delay",
    getDefaultValue: () => 3);
```

## Options That Accept Multiple Strings
Use `AllowMultipleArgumentsPerToken`:
```cs
Option<string[]> myOption = new Option<string[]>( … ) { AllowMultipleArgumentsPerToken = true };
```

## Other Parameters
- `isDefault` - If true, if no input is provided for the option, the ParseArgument<T> delegate is called.

## Properties
- `IsHidden` - This option will not be displayed in help or tab-completed.
- `IsRequired` - Boolean if the option is required.
- `AllowMultipleArgumentsPerToken` - Boolean if multiple arguments should be allowed for the option.
  - This is required when an option accepts multiple strings as an argument.

##  Adding Options to Commands
```cs
rootCommand.Add(delayOption)
//or
rootCommand.AddOption(delayOption)
```

## Global Options
Global options are available to the command it's assigned and all its subcommands.

## Style
The default style is POSIX, using `--` prefixes.  
Windows-based prefixes of `/` are also supported.

## Delimiters
A space or `:` or `=` can delimit an option from an argument:
```powershell
myapp --option 123
myapp --option:123
myapp --option=123
```

## Building Commands with Options
Command actionCommand = new Command(
    "actionCommand",
    "Performs an action.") 
    {
        delayOption
    };

# Aliases
Both Commands and Options support aliases:
```cs
var command = new Command("serialize");
command.AddAlias("serialise");

var option = new Option("--verbose");
option.AddAlias("-v");
```

# Arguments
Arguments are values passed to an option or a command.  
Arguments without default values are treated as required arguments.  
Built-in validation errors when arguments don't match default values, expected types, or arity.  

```cs
// This argument will be parsed into an int:
Argument<int> delayArgument = new(
name: "delay",
description: "The delay in seconds.",
getDefaultValue: () => 3); // Arguments with no default value are made required.
```

Arguments are added to Commands, just like Options: 
```cs
rootCommand.AddArgument(delayArgument);
```

## Listing Valid Argument Values
To specify of a list of valid values for an Argument or an Option, either:
1.  Use an `Enum` as the `Option` type, or;
2.  use `FromAmong`:

```cs
var languageOption = new Option<string>(
    "--language",
    "An option that that must be one of the values of a static list.")
    .FromAmong("csharp", "fsharp", "vb", "pwsh", "sql");
```

## Arity
Arity is expressed with a minimum and maximum value. The ArgumentArity struct has these values:  
- `Zero` - No values allowed.
- `ZeroOrOne` - May have one, may have zero.
- `ExactlyOne` - Must have one.
- `ZeroOrMore` - May have multiple, may have zero.
- `OneOrMore` - May have multiple, must have one.

Arity is inferred from the type:
- An int option has arity of `ExactlyOne`
- A `List<int>` option has arity of `OneOrMore`

# Custom Validation of Options and Arguments
Use `.AddValidator`:
```cs
Option<int> delayOption = new("delay");
delayOption.AddValidator(result =>
{
    if (result.GetValueForOption(delayOption) < 1) 
    {
        result.ErrorMessage = "error";
    }
};
```

## Custom Validation and Parsing
Use the `ParseArgument<T>` delegate:
```cs
var delayOption = new Option<int>(
    name: "--delay",
    description: "An option whose argument is parsed as an int.",
    isDefault: true, // This must be set to true for parseArgument to be called when no value is sent.
    parseArgument: result =>
    {
        if (!result.Tokens.Any())
            return 42;

        if (int.TryParse(result.Tokens.Single().Value, out var delay))
            if (delay < 1)
                result.ErrorMessage = "Must be greater than 0";

        return delay;

        else 
        {
            result.ErrorMessage = "Not an int.";
            return 0; // Ignored.
        }
    });
```

# SetHandler
The `SetHandler` is what binds options to command handlers.  
A root command has a `SetHandler` if there are no commands.  
If there are commands, each `Command` has a `SetHandler`:  
```cs
actionCommand.SetHandler(async (int delayOptionValue) 
{
    await PerformAction(delayOptionValue); // The command calls this method.
    return Task.FromResult(int) // Where int is an exit code. If the handler exits normally,
    // it will exit with 0, not this code.
}, delayOption);
```

All options and arguments must be declared in the same order in the lambda and in the parameters that follow the lambda.

# Starting Execution
After defining `SetHandler`:
```cs
rootCommand.Invoke(args);
// or
return rootCommand.InvokeAsync(args).Result;
```

# [Response Files](https://docs.microsoft.com/en-us/dotnet/standard/commandline/syntax#response-files)
