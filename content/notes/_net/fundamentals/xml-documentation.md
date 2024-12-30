---
title: xml documentation
date: 2023-11-07T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/)  

C# source files can contain structured comments (*XML doc)* that produce API documentation for the types contained therein. 
The compiler creates an XML files that contains structured data representing the comments and the API signatures. 
Other tools can process these XML files to produce human-readable documentation.

# generating xml documentation
To enable XML documentation:  
`.csproj`
```xml
<PropertyGroup>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
</PropertyGroup>
```

With this switch enabled, the compiler generates warning CS1591 for any publicly visible member without XML doc.

# xml comment style guide
- All public types and their public members should be documented.
- At minimum, types and their members should have a `<summary>` tag.
- Private members can be documented, but consider that this exposes the inner workings of a type.
- Documentation text should be written using complete sentences with full stops.
- Partial classes are fully supported and the documentation is concatenated into a single entry for each type.

# general constructs
- `///` — Single-line delimiter. Any following whitespace is ignored.
- `/** */` — Multi-line delimiter. Used for comments. Comments are not included in the compiled assembly.
- `cref` — A tag meaning "code reference." Specifies that the text is a code element (a type, method, property, etc).
- `href` — A reference to a web page. Used to link directly to a web page.

# general tags
## `<summary>`
- Describes a type or a type member.
- The text in this tag is the only source of information for IntelliSense.

```xml
<summary>description</summary>
```

## `<remarks>`
- Adds additional information about a type or a type member.

```xml
<remarks>
    additional information
</remarks>
```

# member tags
## `<returns>`
- Used in the comment for a method declaration to describe the return value.

```xml
<returns>description</returns>
```

## `<param>`
- Used in the comment for a method declaration to describe one of the parameters of that method.
- Use multiple tags to document multiple parameters.
- The `name` parameter must match the API signature.

```xml
<param name="name">description</param>
```

## `<paramref>`
- Used to indicate that a word in the comments (like in a `<summary>` tag) refers to a parameter.
- `"name"` is the name of the actual method parameter.

```xml
<paramref name="name"/>
```

## `<exception>`
- Used to specify which exceptions can be thrown.

```xml
<exception cref="member">description</exception>
```

## `<value>`
- Used to describe the value that a *property* represents. 

```xml
<value>property-description</value>
```

# formatting tags
## `<para>`
- Used inside other tags to create a double-spaced paragraph.
- Use `<br />` for a single-spaced paragraph.

```xml
<remarks>
    <para>
        This is an introductory paragraph.
    </para>
    <para>
        This paragraph contains more details.
    </para>
</remarks>
```

## `<list>`
- Used to define a bulleted list, numbered list, definition list, or table.

| List type       | Requires `<listheader>`? | Required <`listheader`> members | Required `<item>` members       |
| --------------- | ------------------------ | ------------------------------- | ------------------------------- |
| Table           | Yes                      | `<term>`                        | `<description>`                 |
| Definition List | Yes                      | N/A                             | `<term>` <br /> `<description>` |
| Other lists     | No                       | N/A                             | `<description>`                 |

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>Assembly</term>
        <description>The library or executable built from a compilation.</description>
    </item>
</list>
```

## `<c>` and `<code>`
- Used to indicate that text within a description should be marked as code.
- Use `<c>` for single lines and `<code>` for multiple lines.

```xml
<c>text</c>
```

```xml
<code>
    var index = 5;
    index++;
</code>
```

## `<example>`
- Used to show how to use a method or other member.

```xml
<example>
This shows how to increment an integer.
<code>
    var index = 5;
    index++;
</code>
</example>
```

# tags for generic types and methods
## `<typeparam>`
- Used in the comment for a generic type or method to describe a type parameter.

```xml
<typeparam name="TResult">The type returned from this method</typeparam>
```

## `<typeparamref>`
- Used to enable consumers of the resulting documentation file to format the word in a distinct way (perhaps italicized, for example).

```xml
<typeparamref name="TKey"/>
```

# reusing documentation text
## `<inheritdoc>`
- Inherits XML comments from base classes, interfaces, and similar methods (such as `MethodName` and `MethodNameAsync`).
 - With no arguments, this inheritance is automatic.
- `cref` — the member to inherit documentation from.
- `path` — the XPath used to filter the tags to include or exclude from the inherited documentation.

```xml
<inheritdoc [cref=""] [path=""]/>
```

## `<include>`
- References comments in another file.
- `file` — the name of the XML file containing the documentation with a path relative to the source code file.
  - Note that the file name is in single quotes.

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## `<see>`
- Used to specify a link from within the text.
- `cref` — a reference to a member to create hyperlinks to documentation pages for code elements. For example:
  - `cref="IDictionary{T, U}"`
- `href` — a clickable link to a URL.
- `langword` — a language keyword such as `true`

```xml
<see cref="member"/>
<!-- or -->
<see cref="member">Link text</see>
<!-- or -->
<see href="link">Link Text</see>
<!-- or -->
<see langword="keyword"/>
```

## `<seealso>`
- Like `<see>` but specifies the text should appear in the See Also section.