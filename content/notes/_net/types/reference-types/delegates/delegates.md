---
title: delegates
date: 2022-01-02T20:36:26-0700
draft: false
weight: 1
---

# Delegates
Delegates represent references to *methods* with the same signature as the *delegate*.  
- Note: Unlike in overloading, for delegates, a method must have the same return type as the delegate.  
They provide another way (instead of the dot operator) to call a method.  
They are defined in namespace scope (like a class).  
They support chaining (multiple methods can be called on a single event).  
Delegates have built-in support for async operations that run on a different thread.  
Delegates can also encapsulate a named or anonymous method.  

# Uses
- Passing methods as arguments to other methods.
- Defining *callback* methods.
- Events.

# Creating Delegates
```cs
// Declare a delegate:
public delegate void Del(string str);

public static void Notify(string name) 
{
    Console.WriteLine($"Notification received for {name}");
}

// Instantiate a delegate:
Del del1 = new Del(notify);

// OR
Del del2 = Notify;
```

## Example
```cs
public delegate `int` Del(`int n1, int n2`); // Create a delegate.

public class SomeClass 
{
    // …

    public `int` Add(`int n1, int n2`) 
    {
        return n1 + n2;
    }

    Del `d` = Add; // Instantiate the delegate.
    // Because the instantiated delegate is an object, it can be passed as a parameter, or assigned to a property.

    int result = `d`(1, 2); // Call the Delegate, which calls the method.

    result; // 3
}
```

## Anonymous Delegates
Anonymous delegates allow you to create a delegate inline without having to define it elsewhere:
```cs
Del del3 = delegate(string name) 
{
    Console.WriteLine($"Notification received for {name}");
};

// Or:
List<int> list = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

List<int> result = list.FindAll(
    delegate (int num) 
    {
        return (num % 2 == 0);
    }
);
```

## Lambda Expressions
Lambda Expressions are just a convenient syntax for using delegates. They have a parameter list and method body but no formal identity:
```cs
Del del4 = name => 
{
    Console.WriteLine($"Notification received for {name}");
};

// Or:
List<int> list = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

List<int> result = list.FindAll(x => x % 2 == 0);
```

# Callbacks
Because instantiated delegates are objects, they can be passed as arguments to some method. The receiving method can then call the delegate sometime later. This is known as a *callback*.

```cs
// Use the SomeDelegate type as a parameter:
public static void CallbackMethod(int p1, int p1, Del callback) 
{
    callback($"{p1 - p2}");
}

// Pass the delegate created above to the method:
int result = CallbackMethod(5, 4, `d`);
```

# Multicasting
Multicasting is a delegate calling more than one method when invoked.

## Adding Methods to a Delegate's Invocation List
Methods are added to a delegate's list of methods with the + operator:
```cs
public class C 
{
    public void M1(string message) { Console.WriteLine($"M1: {message}"); }
    public void M2(string message) { Console.WriteLine($"M2: {message}"); }
    public void M3(string message) { Console.WriteLine($"M3: {message}"); }
}

var obj = new C();
Del d1 = obj.M1;
Del d2 = obj.M2;
Del d3 = obj.M3;

Del multiDel = d1 + d2;
multiDel += d3; // dWithAllMethods now has M1, M2, and M3 in its invocation list.

multiDel("foo bar baz");
```

## Invoke Methods in a Delegate's Invocation List
- When invoked, all 3 methods are called in order.
- If a delegate uses reference parameters, the reference is passed sequentially to each of the 3 methods.
- If a method throws an exception not caught in that method, it is passed to the caller of the delegate and no more methods in the invocation list are called.
- If a delegate has a return value, it returns the return value and parameters of the last method invoked.

## Removing Methods from a Delegate's Invocation List
Use the `-` operator:
```cs
multiDel -= d3; // dWithAllMethods now only has M1 and M2 in its invocation list.
```

# Delegates with Named Methods
```cs
// Declare a delegate:
public delegate void Del(int i, int j);

public class MathClass 
{
    public static void Main() 
    {
        MathClass m = new MathClass();

        // Instantiate a delegate of MultiplyNumbers():
        Del d = m.MultiplyNumbers; // Delegate d is mapped to the MultiplyNumbers instance method.

        // Invoke the delegate object.
        d(6, 6); // This runs MultiplyNumbers(6, 6)
    }

    public void MultiplyNumbers(int m, int n) 
    {
        Console.Writeline($"{m * n}");
    }
}
```

# Comprehensive Example
```cs
namespace Bookstore;

public struct Book 
{
    public string Title;
    public string Author;
    public decimal Price;
    public book Paperback;

    public Book(string title, string author, decimal price, bool paperBack) 
    {
        Title = title;
        Author = author;
        Price = price;
        Paperback = paperBack;
    }
}

// Declare the delegate:
public delegate void ProcessBookCallback(Book book);

public class BookDB 
{
    ArrayList list = new();

    public void AddBook(string title, string author, decimal price, bool paperBack) 
    {
        list.Add(new Book(title, author, price, paperBack));
    }

    // Call a passed-in delegate on each book to process it:
    public void ProcessPaperbackBooks(ProcessBookCallback processBook) 
    {
        foreach (Book b in list)
            if (b.Paperback)
                processBook(b);
    }
}
```

# Delegates as Events
There are two pre-defined *delegates* to use as *events*:
```cs
public delegate void EventHandler(object? sender, EventArgs e);

public delegate void EventHandler<TEventArgs>(object? sender, TEventArgs e);
```

# Delegates vs. Interfaces
Use delegates for:
- Events
- Encapsulating a static method
- Easy composition
- A class that may need more than one implementation of a method.

Use interfaces for:
- A group of related methods that need to be called.
- A class that needs only one implementation of a method.
