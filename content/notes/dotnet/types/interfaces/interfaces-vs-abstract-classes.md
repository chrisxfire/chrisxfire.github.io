---
title: notes > .net > types > interfaces > interfaces vs abstract classes
date: 2022-05-28T21:30:35-0600
draft: false
weight: 1
---
| Topic                           | Interface | Abstract Class            |
|-------------------------------------|---------------|-------------------------------|
| Instantiable                        | No            | No                            |
| May contain constructor             | No            | Yes                           |
| May provide default implementation  | Yes           | Yes                           |
| Implementations override-able       | Must          | May                           |
| Children must implement all members | Yes           | No                            |
| Multiple inheritance                | Yes           | No                            |
| May contains fields                 | No            | Yes (but not abstract fields) |
| May contain static members          | No            | Yes                           |

Interfaces describe *what an object can do*.
Abstract classes describe *what an object is*.
```cs
interface IPet 
{
    void Eat();
    void Play();
    void Sleep();
}

public class Dog : IPet 
{
    public void Eat() { … }
    public virtual void Play() { … }
    public void Sleep() { … }
}
```
Virtual methods define implementations, but those implementations can be overridden in derived classes.
```cs
public class Labrador : Dog 
{
    public override void Play() { … }
}
```
Abstract classes can contain both implemented and non-implemented members.  
Any class that contains an abstract method must also be declared abstract.
