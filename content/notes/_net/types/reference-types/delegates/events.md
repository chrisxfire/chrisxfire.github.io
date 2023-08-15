---
title: events
date: 2021-11-06T11:28:28-0600
draft: false
weight: 1
---
# Events
[Events in C# (tutorialsteacher.com)](https://www.tutorialsteacher.com/csharp/csharp-event)  
[Events in C# - Code Maze (code-maze.com)](https://code-maze.com/csharp-events/)  
[Events in C# explained. Everyone that understands English knows… | by Dinesh Jethoe | Medium](https://medium.com/@dinesh.jethoe/events-in-c-explained-4a464b110fdc)  

Events are notifications sent by one class to another that some event has occurred. They are specialized delegates.  
Events are commonly used in GUIs; you subscribe to events raised by controls such as buttons.  
Events are encapsulated delegates.  

The class that sends (*raises*) an event is the *publisher*; the class that receives (*handles*) the event is the *subscriber*.  
When an event has many subscribers, the event handlers are invoked synchronously when the event is raised.  

# Subscribe to Events via Visual Studio
1.  **Design view** > right-click form/control for which you want an event handler > **Properties** > **Events** icon
2.  Double-click the event you want to create, such as Load.
3.  This is the auto-generated *event handler* that is invoked when the event is raised:
```cs
private void Form1_Load(object sender, System.EventArgs e) 
{
    // …
}
```

4.  This is the auto-generated *subscription* to the event:
```cs
this.Load += new System.EventHandler(this.Form1_Load);
```

# Subscribe to Events Programmatically
// Define an event handler method whose signature matches the delegate signature for the event:
```cs
void HandleCustomEvent(object sender, System.EventArgs e) 
{
    // …
}

// Assume an object `publisher` has an event named `RaiseCustomEvent`.
// Register the event handler with the event:
publisher.RaiseCustomEvent += HandleCustomEvent;
```

# Subscribe to Events with an Anonymous Function
```cs
// ONLY use an anonymous function if you don't have to unsubscribe from the event later:
publisher.RaiseCustomEvent += (object o, System.EventArgs e) => 
{
    string s = o.ToString() + " " + e.ToString();
    Console.WriteLine(s);
}
```

# Unsubscribing
Unsubscribe from events before you dispose of subscriber objects to prevent resource leaks.
```cs
// Like so:
publisher.RaiseCustomEvent -= HandleCustomEvent;
```

# Publish Events Based on EventHandler Pattern
All events in the .NET class library are based on the `EventHandler` delegate, which is defined as follows:
```cs
public delegate void EventHandler(object sender, EventArgs e);
```

Remember that `EventHandler` is a delegate, not an actual *event handler*. The *event handler* is a method whose signature matches the `EventHandler` delegate definition and is invoked when the event is raised.

1.  (Optional if sending custom data with event).
```cs
// At a scope visible to your publisher AND subscriber classes, declare the class for your custom data and add members
// to hold the data:
public class CustomEventArgs : EventArgs 
{
    public CustomEventArgs(string message) 
    {
        Message = message;
    }

    public string Message { get; set; }
}
```

2.  (Optional if using the non-generic version of EventHandler).
```cs
// Declare a delegate in the publishing class (with a name ending in "EventHandler"):
public delegate void CustomEventHandler(object sender, CustomEventArgs args);
```

3.  Declare the event in the publishing class 1 of 3 ways:
3a. If you have no custom `EventArgs` class:
```cs
// The event type is the non-generic EventHandler delegate.
public event EventHandler RaiseCustomEvent;
// The delegate need not be defined because it is already in the System namespace.
```
3b. If you are using the non-generic EventHandler and have a custom class derived from EventArgs:
```cs
// Use the delegate from step 2 as the type:
public event CustomEventHandler RaiseCustomEvent;
```

3c. If you are using the generic version, you do not need a custom delegate.
In the publishing class, specify your event type as `EventHandler<CustomEventArgs>` (where `CustomEventArgs`
is the name of your own class).
```cs
public event EventHandler<CustomEventArgs> RaiseCustomEvent;
```

# Complete Example
```cs
// Define a class to hold custom event info:
public class CustomEventArgs : EventArgs 
{
    public CustomEventArgs(string message) { Message = message; }

    public string Message { get; set; }
}

// Class that defines the event and publishes it for subscription:
class Publisher 
{
    // Declare the event using EventHandler<T>:
    public event EventHandler<CustomEventArgs> RaiseCustomEvent;

    public void DoSomething() 
    {
    // …

    OnRaiseCustomEvent(new CustomEventArgs("Event triggered"));
    }
}

// Wrap event invocations with protected virtual method to allow derived classes to override event invocation behavior
protected virtual void OnRaiseCustomEvent(CustomEventArgs e) 
{
    // Make a temporary copy of the event to avoid possibility of a race condition if the last subscriber unsubscribes
    // immediately after the null check and before the event is raised:
    EventHandler<CustomEventArgs> raiseEvent = RaiseCustomEvent;

    // If the event is not null (meaning there *are* subscribers):
    if (raiseEvent != null) 
    {
        // Format the string to send inside the CustomEventArgs parameter:
        e.Message += $" at {DateTime.Now}";

        // Raise the event.
        raiseEvent(this, e);
    }
}

// Class that subscribes to an event and handles the event:
class Subscriber 
{
    private readonly string _id;

    public Subscriber(string id, Publisher pub) 
    {
        _id = id;

        // Subscribe to the event:
        pub.RaiseCustomEvent += HandleCustomEvent;
    }

    // Define what actions to take when the event is raised:
    void HandleCustomEvent(object sender, CustomEventArgs e) 
    {
        Console.WriteLine($"{_id} received this message: {e.Message}");
    }
}

class Program 
{
    static void Main() 
    {
        var pub = new Publisher();
        var sub1 = new Subscriber("sub1", pub);
        var sub2 = new Subscriber("sub2", pub);

        // Call the method that raises the event.
        pub.DoSomething();

        // Keep the console window open
        Console.WriteLine("Press any key to continue...");
        Console.ReadLine();
    }
}
```

# Event Modifiers
`virtual`

# Other Examples (somewhat confusing)
## Example 1
```cs
public class Person 
{
    // … more implementation …

    public event EventHandler? Shout; // Delegate field.
    public int AngerLevel;  // Data field.

    public void Poke() 
    {
        AngerLevel++;

        if (AngerLevel >= 3) 
        {
            if (Shout != null) 
            { // If there is an event handler…
                Shout(this, EventArgs.Empty); // …then call the delegate.
            }
        }
    }
}
```
The inner if statement can be simplified like this:
```cs
Shout?.Invoke(this, EventArgs.Empty);
```
```cs
static void Harry_Shout(object? sender, EventArgs e) 
{ // The Event Handler(?).
    if (sender is null) { return; } // It has a signature that matches that of the delegate.
    
    Person p = (Person)sender; // Cast the Object type to a Person type.
    
    Console.WriteLine($"{p.Name} is this angry: {p.AngerLevel}.");
}

harry.Shout += Harry_Shout; // Assigns the method to the delegate field. Note the += operator.
```

## Example 2
```cs
public class MyList<T> 
{
    // …
    protected virtual void OnChanged() =>// This method raises the Changed event.
    Changed?.Invoke(this, EventArgs.Empty);
    // …
    public event EventHandler Changed; // Event declaration; the type must be a delegate.
}

class EventExample 
{
    static int s_changeCount;
    static void ListChanged(object sender, EventArgs e) 
    {
        s_changeCount++;
    }
    public static void Usage() 
    {
        var names = new MyList<string>();
        names.Changed += new EventHandler(ListChanged); // Event Handlers are attached with +=. This
        names.Add("Liz"); // attaches an event handler to the Changed event.
        names.Add("Martha");
        Console.WriteLine(s_changeCount); // "3"
    }
}
```
Event handlers are detached with `-=`.
