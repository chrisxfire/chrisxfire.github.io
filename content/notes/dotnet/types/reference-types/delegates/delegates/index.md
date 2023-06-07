---
title: notes > dotnet > types > reference types > delegates > delegates
date: 2022-01-02T20:36:26-0700
draft: true
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
// Declare a delegate:
public delegate void Del(string str);

public static void Notify(string name) {
Console.WriteLine($"Notification received for {name}");
}

// Instantiate a delegate:
Del del1 = new Del(notify);

// OR
Del del2 = Notify;

## <u>Example</u>
public delegate `int` Del(`int n1, int n2`); // Create a delegate.

public class SomeClass {
…

public `int` Add(`int n1, int n2`) {
return n1 + n2;
}

Del `d` = Add; // Instantiate the delegate.
// Because the instantiated delegate is an object, it can be passed as a parameter, or assigned to a property.

int result = `d`(1, 2); // Call the Delegate, which calls the method.

result; // 3
}

## <u>Anonymous Delegates</u>
Anonymous delegates allow you to create a delegate inline without having to define it elsewhere:

Del del3 = delegate(string name) {
Console.WriteLine($"Notification received for {name}");
};

Or:
List<int> list = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

List<int> result = list.FindAll(
delegate (int num) {
return (num % 2 == 0);
}
};

## <u>Lambda Expressions</u>
Lambda Expressions are just a convenient syntax for using delegates. They have a parameter list and method body but no formal identity:

Del del4 = name => {
Console.WriteLine($"Notification received for {name}");
};

Or:
List<int> list = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

List<int> result = list.FindAll(x => x % 2 == 0);

# Callbacks
Because instantiated delegates are objects, they can be passed as arguments to some method. The receiving method can then call the delegate sometime later. This is known as a *callback*.

// Use the SomeDelegate type as a parameter:
public static void CallbackMethod(int p1, int p1, Del callback) {
callback($"{p1 - p2}");
}

// Pass the delegate created above to the method:
int result = CallbackMethod(5, 4, `d`);

# Multicasting
Multicasting is a delegate calling more than one method when invoked.

## <u>Adding Methods to a Delegate's Invocation List</u>
Methods are added to a delegate's list of methods with the + operator:
public class C {
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

## <u>Invoke Methods in a Delegate's Invocation List</u>
- When invoked, all 3 methods are called in order.
- If a delegate uses reference parameters, the reference is passed sequentially to each of the 3 methods.
- If a method throws an exception not caught in that method, it is passed to the caller of the delegate and no more methods in the invocation list are called.
- If a delegate has a return value, it returns the return value and parameters of the last method invoked.

## <u>Removing Methods from a Delegate's Invocation List</u>
Use the - operator:
multiDel -= d3; // dWithAllMethods now only has M1 and M2 in its invocation list.

# Delegates with Named Methods
// Declare a delegate:
public delegate void Del(int i, int j);

public class MathClass {
public static void Main() {
MathClass m = new MathClass();

// Instantiate a delegate of MultiplyNumbers():
Del d = m.MultiplyNumbers; // Delegate d is mapped to the MultiplyNumbers instance method.

// Invoke the delegate object.
d(6, 6); // This runs MultiplyNumbers(6, 6)
}

public void MultiplyNumbers(int m, int n) {
Console.Writeline($"{m * n}");
}
}

# Comprehensive Example
namespace Bookstore;

public struct Book {
public string Title;
public string Author;
public decimal Price;
public book Paperback;

public Book(string title, string author, decimal price, bool paperBack) {
Title = title;
Author = author;
Price = price;
Paperback = paperBack;
}
}

// Declare the delegate:
public delegate void ProcessBookCallback(Book book);

public class BookDB {
ArrayList list = new();

public void AddBook(string title, string author, decimal price, bool paperBack) {
list.Add(new Book(title, author, price, paperBack));
}

// Call a passed-in delegate on each book to process it:
public void ProcessPaperbackBooks(ProcessBookCallback processBook) {
foreach (Book b in list)
if (b.Paperback)
processBook(b);
}
}

# Delegates as Events
There are two pre-defined *delegates* to use as [*events*](onenote:#Events&section-id={92395629-C009-4FE2-B427-3AE65B5329AA}&page-id={61A81183-0181-4E37-98AD-A83C14CC0AD4}&end&base-path=https://d.docs.live.net/1489beaac91cb6b6/Documents/Notebooks/Code/C%20Sharp.one):
public delegate void EventHanlder(object? sender, EventArgs e);

public delegate void EventHandler<TEventArgs>(object? sender, TEventArgs e);

# Delegates vs. Interfaces
Use delegates for:
- Events
- Encapsulating a static method
- Easy composition
- A class that may need more than one implementation of a method.

Use interfaces for:
- A group of related methods that need to be called.
- A class that needs only one implementation of a method.
