---
title: "notes > asp.net > web apps > general > razor syntax > implicit and explicit expressions"
date: 2023-04-24T00:00:00-07:00
draft: false
---

# Implicit Razor Expressions
Implicit Razor expressions start with `@` and are followed by C# code.  These must not contain spaces (except with the await keyword):   
```html
<p>@DateTime.Now</p>
<p>@DateTime.IsLeapYear(2016)</p>
```

# No Generics
Implict expressions cannot contain C# generics:  the characters inside `<` `>` are evaluated as an HTML tag.  
Invalid:  `<p>@GenericMethod<int>()</p>`

To make genric method calls, use explicit Razor expressions.

# Explicit Razor Expressions
Explicit Razor expressions use an `@` symbol and paranthesis:  
```html
<p>Last week this time: @(DateTime.Now - TimeSpan.FromDays(7))</p>
```

Explicit expressions can contain spaces (like above) while implicit expressions cannot:  
Invalid:  `<p>Last week: @DateTime.Now - TimeSpan.FromDays(7)</p>`

Explicit expressions can concatenate text with an expression result:
```cs
@{
    var joe = new Person("Joe", 33);
}
```
```html
<p>Age@(joe.Age)</p>
```

Explicit expressions can render output from generic methods:
```html
<p>@(GenericMethod<int>())</p>
```