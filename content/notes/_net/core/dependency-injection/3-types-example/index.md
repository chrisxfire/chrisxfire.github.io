---
title: notes > .net > core > dependency injection > 3 types example
date: 2022-08-26T07:37:34-0600
draft: false
---
3 Types of Dependency Injection:
1.  Constructor Injection – Injector class supplies the Service (dependency) through the Client class constructor.
2.  Property Injection – Injector class supplies the Service through a public property of the Client class.
3.  Method Injection – Client class implements an interface which declares the methods to supply the Service (dependency); Injector uses this interface to supply the Service to the Client class.
```cs
interface IService {
    void Serve();
}
public class Service1 : IService {
    public void Serve() => "Service1 is running.";
}
public class Service2 : IService {
    public void Serve() => "Service2 is running.";
}
public class Client {
    private IService _service;

    // The Service is injected into the Client via its constructor:
    public Client(IService service) {
        this._service = service;
    }

    public void ServeMethod() {
        this._service.Server()
    }
}

class Program {
    public static void Main() 
    {
        // Create an object:
        Service1 s1 = new();

        // Pass the dependency:
        Client c1 = new Client(s1);

        // Act:
        c1.ServeMethod();
    }
}
```

# 3 Types of Dependency Injection
```cs
public interface IService 
{
    void Print();
}
public class SomeService : IService 
{
    public void Print() 
    {
        Console.WriteLine("Print from Service1");
    }
}
```

## Constructor Injection
```cs
public class SomeClass 
{
    private IService _service;

    public SomeClass(IService service) 
    {
        this._service = service;
    }
    public void PrintMethod() 
    {
        this._service.Print();
    }
}
```

## Property (Setter) Injection
```cs
public class SomeClass 
{
    private IService _service;

    public IService service 
    {
        set 
        {
            this._service = value;
        }
    }
    public void PrintMethod() 
    {
        this._service.Print();
    }
}
```

## Method Injection
```cs
public class SomeClass 
{
    private IService _service;

    public void PrintMethod(IService service) 
    {
        _service = service;

        this._service.Print();
    }
}
```
