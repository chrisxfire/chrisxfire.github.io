---
title: interfaces explicit implementation
date: 2022-03-06T18:29:31-0700
draft: false
weight: 1
---
# Explicit Interface Implementation
[Internal Interface Classes in C# | Alex Franchuk](https://alexfranchuk.com/blog/internal-interface-classes-in-csharp/)
Interfaces can be explicitly implemented. Assume a case where a class implements two interfaces that have a member with the same signature:
```cs
public interface IControl { void Paint(); }
public interface ISurface { void Paint(); }

public class SampleClass : IControl, ISurface 
{
    public void Paint();
}

SampleClass sample = new SampleClass();
IControl control = sample;
ISurface surface = sample;
```

These all call the same method:
```cs
sample.Paint();
control.Paint();
surface.Paint();
```

To call a different implementation depending on which interface is in use, implement an interface member explicitly:
```cs
public class SampleClass : IControl, ISurface 
{
    void IControl.Paint() { // …implementation… }
    void ISurface.Paint() { // …implementation… }
}

SampleClass sample = new SampleClass();
IControl control = sample;
ISurface surface = sample;
```

Now:
```cs
sample.Paint(); // This call fails.
control.Paint();
surface.Paint();
```

# Explicit Interface Member Implementation
```cs
interface IDimensions 
{
    float GetLength();
    float GetWidth();
}

class Box : IDimensions 
{
    float lengthInches;
    float widthInches;

    Box(float length, float width) 
    {
        lengthInches = length;
        widthInches = width;
    }

    // Explicit interface member implementation:
    float IDimensions.GetLength() { return lengthInches; }
    float IDimensions.GetWidth() { return widthInches; }
}
```
