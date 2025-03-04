---
title: singleton
date: 2023-03-05T15:30:17-0700
draft: false
weight: 1
---

# singleton
Type: Creational  
Purpose: Ensure that a class has only one instance while providing a global access point to this instance.  
Use to:
- Solve for needing a single instance of a class available to all clients (like a database instance).
- Provide strict control over global variables.  
Principles: Violates Single Responsibility Principle  
Complexity: 1/3  
Popularity: 2/3  

<r>This pattern is not natively thread-safe.</r>

# overview
![The structure of the Singleton pattern](./Creational_Singleton-image2.png)

1.  The Singleton class declares the static method getInstance that returns the same instance of its own class.

The Singleton’s constructor should be hidden from the client code. Calling the getInstance method should be the only way of getting the Singleton object.

# Implementing (non-thread-safe)
```cs
public sealed class Singleton
{
    // Add a private static field to the class for storing the singleton instance.
    private static Singleton _instance;

    // Make the constructor of the class private.
    private Singleton() { }

    // Declare a public static creation method for getting the singleton instance.
    public static Singleton GetInstance()
    {
        // Implement *lazy initialization* inside the static method. The method must create a new object on its first call and put it into the static field. The method must always return that instance on all subsequent calls.
        if (_instance is null)
            _instance = new Singleton();

        return _instance;
    }

    // Business logic that can be executed on the singleton instance:
    public void someBusinessLogic()
    {
        // …
    }
}
```
# Implementing (thread safe)
```cs
// double locking is used to reduce the overhead of the synchronized method
public static ThreadSafeSingleton getInstanceDoubleLocking() 
{
    if (instance == null) 
    {
        synchronized (ThreadSafeSingleton.class) 
        {
            if (instance == null)
                instance = new ThreadSafeSingleton();
        }
    }
    return instance;
}
```