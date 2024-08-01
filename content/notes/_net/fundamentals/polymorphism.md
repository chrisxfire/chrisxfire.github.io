---
title: polymorphism
date: 2022-02-17T20:22:18-0700
draft: false
weight: 1
---
# Versioning
C# is designed to allow versioning between base and derived classes in different libraries.
This allows for introduction of a new member in a base class with the same name as a member in a derived class.
- override and virtual and new can be used on methods, properties, indexers, and events.

# `virtual`
If a method is virtual, any class inheriting it can implement its own version with override:
```cs
public class Graphics 
{
    public virtual void DrawLine() { } // These method can be implemented in a derived class.
    public virtual void DrawPoint() { }
    public virtual void DrawRectangle() { }
}
```

# `override`
If a method is overridden, it *extends* the base class version. The base class version must be `virtual.`
```cs
public class CustomGraphics : Graphics 
{
    public void override DrawRectangle() { } // Any objects derived from CustomGraphics will use this version
}                                            // of DrawRectangle(). It *extends* the base class version.
```
# `base`
The `base` keyword can be used to call the base class method if an overridden method exists:
```cs
base.DrawRectangle() // This class Graphics.DrawRectangle().

CustomGraphics cg = new();
((Base)cg).DrawRectangle(); // An object of a derived class can call the base class method
 // by casting (Base).
```

# `new`
The new modifier tells the compiler that you are aware that a derived class method hides a base class method of the same name:
```cs
class BC 
{
    public void M1() => "BCM1"
    public void M2() => "BCM2"
}

class DC 
{
    public void M2() => "DCM2" // This results in a warning that BC.M2 is hidden by DC.M2.
}
```
With new:
```cs
class DC 
{
    public new void M2() => "DCM2" // The warning is now suppressed. Behavior remains the same.
}
```
