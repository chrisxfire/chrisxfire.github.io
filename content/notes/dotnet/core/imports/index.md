---
title: "notes > dotnet > core > imports"
date: 2022-02-16T00:00:00-06:00
draft: false
---

# Imports
```cs
using namespace; // Imports all classes from namespace.
using static namespace; // Imports only the static methods from namespace.
using static System.Console; // This allows you to use WriteLine() without having to call Console.WriteLine().
global using namespace;	// Allows importing namespace into one file but available to the whole project.
```

Console applications have these implicit using directives (auto imports):
```cs
using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

Other auto imports can be found in `/obj/Debug/net6.0/TopLevelProgram.GlobalUsings.g.cs`.

# Using Directive
```cs
using namespace;
```

## Aliases
```cs
using SomeAlias = Really.Long.Nested.Namespace;
```

## Global
The global modifier has the same effect as adding the same using directive to every source file in a project:
```cs
global using namespace;
```

Can also be added to project file instead:
```xml
<Using>namespace</Using>
```

## Static
The static modifier imports only the static members and nested types from a namespace:
```cs
static using namespace;
```

# Implicit Using Directives
Implicitly imports:
- `System`
- `System.IO`
- `System.Collections.Generic`
- `System.Linq`
- `System.Net.Http`
- `System.Threading`
- `System.Threading.Tasks`

## Disabling
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

# Using Statement
The `using` statement generates a `finally` statement that calls the `Dispose()` method on an object that implements `IDisposable`:
```cs
using (FileStream xmlFileStream = File.Create(file.xml)) { … }
```

