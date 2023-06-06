---
title: "notes > dotnet > types > modifiers"
date: 2022-11-25T21:11:47-0700
draft: false
---

# `file` Modifier
Restricts top-level type's scope and visibility to the file in which it is declared.  
Declares a file-local type.  
Generally applied to types written by a source generator.  

`Classes.cs`:
```cs
// Only visible in Classes.cs
file class HiddenClass 
{
    // ...   
}
```