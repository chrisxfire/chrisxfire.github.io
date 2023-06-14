---
title: notes > .net > linq > overview > queries
date: 2022-11-05T21:40:53-0600
draft: false
---
# Query
A *query* is an expression that specifies what information to retrieve from a data source. Optionally, it also specifies how the resulting data should be sorted, grouped, and shaped when returned.

A query and the results it produces are distinct.

A query is stored in a query variable and initialized with a query expression.

## 3 Parts of a Query Operation<
```cs
int[] numbers = new int[7] { 0, 1, 2, 3, 4, 5, 6 }; // (1) Obtain the data source

// The *query expression* in *query syntax*:
IEnumerable<int> numQuery = // (2) Create the query and store it in the *query variable* (`numQuery`)
from num in numbers // Must begin with `from`
    where (num % 2) == 0
    select num; // Must end with `select` or `group`

foreach (int num in numQuery) 
{ // (3) Execute the query (data retrieved here)
    Console.Write("{0,1} ", num);
}
```

## Query Variable
A *query variable* stores a query instead of the results of a query. It is always an enumerable type.
