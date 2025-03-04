---
title: nested types
date: 2022-03-06T18:11:19-0700
draft: false
weight: 1
---

# nested types
A type defined within a *class*, *struct*, or *interface* is a nested type:

```cs
public class Outer 
{
    class Inner 
    {
        Inner() { }
    }
}
```

Nested types default to `private`. They are only accessible from their containing type.

# accessing
To access the outer type, pass it as an argument to the constructor fo the nested type:

```cs
public class Outer 
{
    public class Inner 
    {
        private Outer parent;

        public Inner() { }
        public Inner(Outer parent) 
        {
            this.parent = parent;
        }
    }
}
```

# notes
An inner type has access to all of the members that are accessible to its outer type.  
Nested types can be `partial`, even if the type they are nested within is not `partial`.  
