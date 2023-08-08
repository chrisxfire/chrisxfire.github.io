---
title: dynamic
date: 2022-02-17T19:03:02-0700
draft: false
weight: 1
---
# Dynamic Type
Namespace: `System.Dynamic`  
Type: `DynamicObject`  

Characteristics:
- Bypasses static type checking.
- Functions like it has type object.
- At compile time, an element typed dynamic is assumed to support any operation.

# Conversions
## Converting to Dynamic
```cs
dynamic d1 = 7;
dynamic d2 = "a string";
```

## Converting From Dynamic
```cs
int i = d1;
string s = d2;
```

# Uses
## HTML DOM
Use a dynamic object to reference the HTML DOM, which can contain any combination of valid HTML and attributes.  
Because each HTML document is unique, the members for a particular HTML document are determined at run time.

Example: To reference the id attribute of HTML element `<div id="Div1">`:
- Obtain a reference to the `<div>` element, then:
```cs
dynamic divElem = divElement.GetProperty("id");
divElem.id // returns "Div1"
```
