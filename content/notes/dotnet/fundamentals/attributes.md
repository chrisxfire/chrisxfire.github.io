---
title: notes > .net > fundamentals > attributes
date: 2022-01-01T00:00:00-06:00
draft: false
weight: 1
---

# Overview
`Object` –> `Attribute`  
- Attributes associate metadata with code.  Once associated, attributes can be queried at runtime using reflection.  
- Attributes from the .NET library trigger certain behaviors in the compiler.  
- User-defined attributes only act as metadata.

## Targets
Attributes are generally declared above the code they are associated to.  Attributes can be called with a target using this form:  
`[target : attribute1, attribute2, …]`  
Attributes can target:
- assembly (place under the `using` directives)
- module   (place under the `using` directives)
- field
- event
- method
- parameters
- property
- return
- type

Associating to a parameter:  
```cs
int MethodX([ValidatedContract] string contract) { return 0; }
```

Associating to a return value:
```cs
[return: ValidatedContract]
int MethodY() { return 0; }
```

## Usage
```cs
[SomeAttribute("argument")]
```
By convention, attributes end in the `Attribute.`  This is not required.

Examples:
```cs
[Serializable]
```

With a named parameter:
```cs
[DllImport("user32.dll", SetLastError=false)]
```

This attribute marks the class obsolete:
```cs
[Obsolete("SomeClass is obsolete.  Use SomeOtherClass instead.")]
public class SomeClass { }
```

This is equivalent to:
```cs
var attr = new ObsoleteAttribute("string")
```

## Common Uses
- Marking methods using `WebMethodAttribute` in web services to indicate that they method should be callable over SOAP.
- Calling unmanaged code using `DLLImportAttribute.`
- Describing an assembly's title, version, description, or trademark.
- Describing which members of a class to serialize for persistence.

## Common Attributes
```cs
[AssemblyVersion]
[AssemblyInformationalVersion]
[AssemblyFileVersion]
[Serializable]
[NonSerialized]
[Obsolete] // Issues a compiler warning.
[CallerMemberName] // Used on parameters; injects the name of the method that is calling another.
[RequiresPreviewFeatures] // Indicates the assembly, type, or member uses preview features.  Issues a compiler warning.
```

# Creating Attributes
Attributes are created by defining a class that inherits from Attribute.  
```cs
[AttributeUsage(AttributeTargets.Class |	// This restricts the attribute to Classes
	AttributeTargets.Struct,			    // …and Structs.
	AllowMultiple=true)]					// This parameter of AttributeUsage makes it multiuse.

public class AuthorAttribute : System.Attribute {	// This class defines the attribute.
	private string name;	// This is a positional parameter for the attribute.
	public double version; 	// This is a named parameter (since it's public).

	public AuthorAttribute(string name) {
		this.name = name;
		version = 1.0;
	}
}
```

## Using a Created Attribute
```cs
using System.Runtime.CompilerServices
[Author("C. H.", version = 0.1)]
class SampleClass { … }
```

Conceptually, this is equivalent:
```cs
Author anonymousAuthorObject = new Author("C. H.");
anonymousAuthorObject.version = 0.1;
```

## Accessing Attributes
Attributes are accessed using `GetCustomAttributes()`.  When accessed, anAuthor object is constructed and initialized as above.  It returns an array:  
`System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);`

# Generic Attributes (C# 11)
Create:
```cs
public class SomeAttribute<T> : Attribute { }
```
Access:
```cs
[SomeAttribute<string>()]
public string Method() => default
```
