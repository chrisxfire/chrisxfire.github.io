---
title: finalizers
date: 2022-01-03T21:10:32-0700
draft: false
weight: 1
---

# finalizers
Each type can have a single finalizer that is called by the runtime when resources need to be released.  
They release unmanaged resources like windows, files, network connections, or mutexes controlled by the OS.  
They are also known as *destructors* (not *deconstructors*) because they destroy objects in memory.  

Finalizers do not take modifiers and they do not have parameters.  
- They cannot be defined in structs.  
- They cannot be inherited or overloaded.  
- They cannot be called. They are invoked automatically. The timing of invocation cannot be controlled.  

.NET 5 and later no longer calls finalizers as part of application termination.
- To perform cleanup reliably on app termination, register a handler for `System.AppDomain.ProcessExit`.

# example
```cs
public class Animal : IDisposable 
{ // Inheriting IDisposable is optional.
    // … implementation …

    public Animal() 
    { // The constructor
        // … Allocate unmanaged resource(s) …
    }

    ~Animal() 
    { // The finalizer
        // … Deallocate unmanaged resource(s) …
    }

    bool disposed = false; // Have resources been released?

    public void Dispose() 
    { // Called by a developer using this type to deallocate both managed and
        Dispose(true); // unmanaged resources.

        GC.SuppressFinalize(this); // Tell GC it does not need to call the finalizer.
    }

    protected virtual void Dispose(bool disposing) 
    {
        if (disposed) { return; } // The finalizer has already run.

        // … Deallocate *unmanaged* resources …

        if (disposing) 
        {
            // … Deallocate *managed* resources …
        }

        disposed = true;
    }
}
```

# implicit translation
Finalizers are implicitly translated to the following:
```cs
protected override void Finalize() 
{
    try 
    {
        // …cleanup statements…
    }
    finally 
    {
        base.Finalize(); // This ensures all finalizers up the call stack are invoked.
    }
}
```

# `using` Statement
To ensure a type's public `Dispose()` method is called, use a `using` statement:
```cs
using (Animal a = new()) { … }
```

The compiler converts the above to:
```cs
Animal a = new();

try 
{
    // … code that uses the Animal instance …
}
finally 
{
    if (a != null) { a.Dispose(); }
}
```
