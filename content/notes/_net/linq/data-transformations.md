---
title: type relationships and transformations
date: 2022-11-05T22:14:36-0600
draft: false
weight: 1
tags:
 - kb/dotnet/linq
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/get-started/type-relationships-in-linq-query-operations)
LINQ query operations are strongly typed in the source data, the query itself, and in query execution. This strong typing
guarantees that type errors are caught at compile time.

LINQ query operations can also transform ("project") data into different types.

# a query with no transformations
In the following:
- Since each element in the data source, `names`, is a `string`...
  - the type of the range variable, `n`, is `string`.
- Since the type of the object selected, `n`, is `string`...
  - the type of of the query variable, `nameQuery`, is `IEnumerable<string>`.

```cs
List<string> names = new() { "John", "Jane", "Mark", "Molly" };

IEnumerable<string> nameQuery = from n in names 
                                where n[0] == 'M'
                                select n; 
```

# a query that transforms the source data
Consider this LINQ to SQL query operation:
- Since each element in the data source, `Customers`, is a `Customer`, the type of the range variable, `cust`, is `Customer`.
- Since the type of the object selected, `cust.Name`, is `string`, the type of the query variable, `custNameQuery`, is `string`.

```cs
Table<Customer> Customers = db.GetTable<Customers>();

IQueryable<string> custNameQuery = from cust in customers
                                   where cust.City == "London"
                                   select cust.Name;
```

# another query that transforms the source data
Consider this more complex transformation:
- Since each element in the data source, `Customers`, is a `Customer`, the type of the range variable, `cust`, is `Customer`.
- Since the type of the object selected creates an anonymous type, the query variable, `namePhoneQuery`, must be implicitly typed with `var`.

```cs
Table<Customer> Customers = db.GetTable<Customers>();

var namePhoneQuery = from cust in Customers
                     where cust.City == "London"
                     select new { name = cust.Name, phone = cust.Phone };
```

# Another transformation: join multiple inputs into one output sequence
Assume:

```cs
class Student(string First, string Last, int ID, string Street, string City, List<int> Scores);
class Teacher(string First, string Last, int ID, string City);

List<Student> students = new() { … };
List<Teacher> teachers = new() { … };

string peopleInDenver = (
    from student in students
    where student.City == "Denver"
    select student.Last)
    .Concat(
        from teacher in teachers
        where teacher.City == "Denver"
        select teacher.Last);

foreach (var person in peopleInDenver)
    Console.WriteLine(person);
```

## selecting a subset of each source element
```cs
var query1 = from cust in customers
select cust.City; // This select just one member of the source element

var query2 = from cust in customers
select new { Name = cust.Name, City = cust.City }; // This creates an anonymous type that holds two properties of the source element.
```
# \L
