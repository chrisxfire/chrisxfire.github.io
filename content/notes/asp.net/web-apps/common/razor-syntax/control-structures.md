---
title: control structures
date: 2023-04-24T00:00:00-07:00
draft: false
weight: 1
---

# `@if`, `else if`, `else`
`@if` controls when code runs; else and else if do not require the `@` symbol:
```html
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
else if (value >= 1337)
{
    <p>The value is large.</p>
}
else
{
    <p>The value is odd and small.</p>
}
```

# `@switch` Statements
Like so:
```html
@switch (value)
{
    case 1:
        <p>The value is 1!</p>
        break;
    case 1337:
        <p>Your number is 1337!</p>
        break;
    default:
        <p>Your number wasn't 1 or 1337.</p>
        break;
}
```

# `@for`, `@foreach`, `@while`, and `@do while`
Templated HTML can be rendered in looping control statements:
```cs
@{
    var people = new Person[]
    {
          new Person("Weston", 33),
          new Person("Johnathon", 41),
          ...
    };
}
```

`Foreach` example:
```html
@foreach (var person in people)
{
    <p>Name: @person.Name</p>
    <p>Age: @person.Age</p>
}
```

# Compound `@using`
In Razor, a `@using` statement is used to create HTML Helpers that contain additional content, like this one that renders a `<form>` tag:
```html
@using (Html.BeginForm())
{
    <div>
        Email: <input type="email" id="Email" value="">
        <button>Register</button>
    </div>
}
```

# `@try`, `catch`, `finally`
Like C#:
```html
@try
{
    throw new InvalidOperationException("You did something invalid.");
}
catch (Exception ex)
{
    <p>The exception message: @ex.Message</p>
}
finally
{
    <p>The finally statement.</p>
}
```

# `@lock`
Like so:
```cs
@lock (SomeLock)
{
    // Do critical section work
}
```
