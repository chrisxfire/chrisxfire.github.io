---
title: "notes > dotnet > linq > overview > query operators"
date: 2022-11-05T22:15:01-0600
draft: true
---
# Query Operations
LINQ queries can be filtered, sorted (ordered), grouped, joined, and selected:
## 
# Filtering & Sorting (Ordering)
var queryA = from cust in customers
where cust.City == "London" // this is the *filter*
orderby cust.Name ascending // this is the *sorter*
select cust;

# Grouping
The `group` clause results in `queryG` being typed `IEnumerable<IGrouping<string, Customer>>`.
Each group itself contains a key and a sequence that consists of all members of that group:
var queryG = from cust in customers
group cust by cust.City; // `cust.City` is the key for `groupby`

To iterate over a query that produces a sequence of groups, use a nested `foreach` loop:
foreach (var customerGroup in queryG)
foreach (Customer customer in customerGroup)
…

## Grouping with into
To refer to the results of a `group` operation directly, use `into` to create an identifier:
var queryG = from cust in customers
group cust by cust.City into custGroup // the `custGroup` identifier can be queried further
where custGroup.Count() > 2
orderby custGroup.Key
select custGroup;

# Joining
Join operations create associations between sequences that do not otherwise exist:
var queryJ = from cust in customers
join dist in distributors on cust.City equals dist.City
select new { CustomerName = cust.Name, DistributorName = dist.Name };

# Selecting
The `select` clause produces the query and specifies the "shape" or type of each element returned.
A `select` clause that produces a different shape than the source element is a projection.

# Type Relationships within a Query
List<`string`> names = new() { "John", "Rick", "Maggie", "Mary" };
