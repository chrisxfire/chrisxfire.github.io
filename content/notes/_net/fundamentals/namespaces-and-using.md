---
title: namespaces-and-using
date: 2022-02-16T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/fundamentals/namespaces
 - kb/dotnet/fundamentals/using
---

# namespaces
Namespaces declare scopes:
```cs
namespace SomeNamespace 
{
	class SomeClass { }
}
```

Namespace declarations can also be file-scoped:
```cs
using SomeNamespace; // Imports all classes from namespace.
```

# Imports (`using` Directive)
```cs
using SomeNamespace;
```

# aliases
The `using` directive can create aliases to namespaces:
```cs
using MyNamespace = Really.Long.Nested.Namespace;
```

> [!IMPORTANT]
> Availability: C# 12

Or, to a type:
```cs
using WpfButton = System.Windows.Controls.Button;
using WinFormsButton = System.Windows.Forms.Button;

var wpfButton = new WpfButton();
var winFormsButton = new WinFormsButton();
```

Including generic types:
```cs
using StringList = System.Collections.Generic.List<string>;

var strings = new StringList { "C#", "TypeScript" };
```	

Even a Tuple:
```cs
using MyTuple = (int Min, int Max);
```

But not a reference type:
```cs
// ILLEGAL
using X = string?;
```

## global
The `global` modifier has the same effect as adding the same `using` directive to every source file in a project:
```cs
global using SomeNamespace;
```

Can also be added to project file instead:
```xml
<Using>namespace</Using>
```

## static
The static modifier imports only the static members and nested types from a namespace:
```cs
static using SomeNamespace;
```

```cs
using static System.Console; // Imports a type's methods, like WriteLine.
```

## [Implicit Using Directives](https://learn.microsoft.com/en-us/dotnet/core/project-sdk/overview#implicit-using-directives)
Some SDKs have implicit using directives. For example, for console applications (`Microsoft.Net.Sdk`):
- `System`
- `System.IO`
- `System.Collections.Generic`
- `System.Linq`
- `System.Net.Http`
- `System.Threading`
- `System.Threading.Tasks`

### disabling
To disable implicit imports, add this line to the project file:
```xml
<ImplicitUsings>disable</ImplicitUsings>
```

To use implicit imports but remove a specific one:
```xml
<ItemGroup>
	<Using Remove="System.Net.Http" />
</ItemGroup>
```

# using statement
The `using` statement generates a `finally` statement that calls the `Dispose()` method on an object that implements `IDisposable`:
```cs
using (FileStream xmlFileStream = File.Create(file.xml)) { … }
```