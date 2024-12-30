---
title: overview
date: 2022-04-20T10:06:47-0600
draft: false
weight: -1
tags:
 - kb/dotnet/linq
---

# [Abstract](https://learn.microsoft.com/en-us/dotnet/csharp/linq/)
A *query* is an expression that retrieves data from a data source. SQL is a query language for relational databases. XQuery is a query language for XML. 
LINQ (Language-Integrated Query) is a set of technologies that integrates query capabilities directly into C#. 
It provides language-level querying capabilities and it works across a variety of data sources.

> [!TIP]
> See also: https://learn.microsoft.com/en-us/dotnet/standard/linq/

## architecture
LINQ consists of:
- *Extensions methods* (required) – `Where`, `OrderBy`, `Select`, etc
- *LINQ providers* (required) – LINQ to Objects, LINQ to Entities, LINQ to XML, LINQ to SQL
- *Lambda expressions* (optional) – can be used instead of named methods.
- *LINQ query syntax* (optional) – `from`, `in`, `where`, `orderby`, etc.

# linq query operations
A LINQ query operation consists of three actions:
1. Obtain the data source
2. Create the query (and store it in a *query variable*)
3. Execute the query

Example:
```cs
// 1. Data source.
int[] numbers = [ 0, 1, 2, 3, 4, 5, 6 ];

// 2. Query creation
var numQuery =
    from num in numbers   // from clause specifies the data source
    where (num % 2) == 0  // where clause applies the filter
    select num;           // select clause specifies the type of returned elements

// 3. Query execution
foreach (int num in numQuery) 
    Console.Write("{0,1} ", num);
```

## 1. The data source
*Queryable types* are the set of all types that implement `IEnumerable<T>` or a derivative. Any queryable type is a valid LINQ data source. 

If the data source is not already in memory, the *LINQ provider* must represent it as such.
For example, the *LINQ to XML* provider loads an XML document into an `XElement`, which is a queryable type:
```cs
// using System.Xml.Linq;
XElement contacts = XElement.Load(@"c:\myContactList.xml");
```

## 2. The query
The query specifies what information to retrieve from the data source(s), and, optionally, how it should
be sorted, grouped, or shaped before its returned.

```cs
var numQuery =
    from num in numbers   // from clause specifies the data source
    where (num % 2) == 0  // where clause applies the filter
    select num;           // select clause specifies the type of returned elements
```

The `from`, `where`, and `select` keywords are some of the *Standard Query Operators*. 

LINQ queries vary in their modes of execution:
- Immediate
- Deferred
  - Streaming
  - Non-streaming 

## 3. The execution
### immediate execution standard query operators
In immediate execution, the data is read and the execution is performed at once.
Examples include `Count`, `Max`, `Average` and `First`:
```cs
var evenNumQuery =
    from num in numbers
    where (num % 2) == 0
    select num;

int evenNumCount = evenNumQuery.Count();
```

Additionally, *any* query can be forced to execute immediately using `ToList` or `ToArray`:
```cs
var fooQuery =
    (from num in numbers
    where (num % 2) == 0
    select num).ToList(;)
```

### deferred execution standard query operators
In deferred execution, the data is ready, but execution is deferred until the resulting
query variable is enumerated:

```cs
foreach (int num in numQuery)
{
  // ...
}
```

In this mode, the query variable can be enumerated repeatedly.

**Streaming** standard query operators can yield result elements before all of the source data is read.  
**Non-streaming** standard query operators must read all the data before yielding a result element.  