---
title: notes > code > software engineering > patterns > creational > fluent interface
date: 2023-03-08T13:29:19-0700
draft: false
---

```cs
// Defines the data context
class Context
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Sex { get; set; }
    public string Address { get; set; }
}

class Customer
{
    private Context _context = new Context(); // Initializes the context

    // set the value for properties
    public Customer FirstName(string firstName)
    {
        _context.FirstName = firstName;
        return this;
    }

    public Customer LastName(string lastName)
    {
        _context.LastName = lastName;
        return this;
    }

    public Customer Sex(string sex)
    {
        _context.Sex = sex;
        return this;
    }

    public Customer Address(string address)
    {
        _context.Address = address;
        return this;
    }

    // Prints the data to console
    public void Print()
    {
        Console.WriteLine($"First name: {_context.FirstName} \nLast name: {_context.LastName} \nSex: {_context.Sex} \nAddress: {_context.Address}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Object creation
        Customer c1 = new Customer();
        // Using the method chaining to assign & print data with a single line
        c1.FirstName("vinod").LastName("srivastav").Sex("male").Address("bangalore").Print();
    }
}
```
