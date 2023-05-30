---
title: "notes > dotnet > linq > standard query operators > standard query operators"
date: 2022-11-06T09:37:07-0700
draft: true
---
# Overview
The standard query operators are extension methods of `IEnumerable<T>` or `IQueryable<T>`. They are the static methods of the `Enumerable` and `Queryable` classes.

# Manner of Execution
Standard Query Operator methods can execute in *immediate* or *deferred* manner.
If deferred, in *streaming* or *non-streaming* forms.

## Deferred Queries
A deferred query fetches the updated data from the data source each time query results are iterated.
A deferred query can be forced to execute immediately with `Enumerable.ToList` or `Enumerable.ToArray`.

# Query Operators with Equivalent Query Expression Clauses
<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 39%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Query expression</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cast</td>
<td>from int i in numbers</td>
<td>Requires an explicitly typed range variable</td>
</tr>
<tr class="even">
<td>GroupBy</td>
<td><p>group … by</p>
<p>group … by … into …</p></td>
<td><p></p>
<blockquote>
<p></p>
</blockquote></td>
</tr>
<tr class="odd">
<td>GroupJoin</td>
<td>join … in … on … equals … into</td>
<td></td>
</tr>
<tr class="even">
<td>Join</td>
<td>join … in … on … equals …</td>
<td></td>
</tr>
<tr class="odd">
<td>OrderBy</td>
<td>orderby</td>
<td></td>
</tr>
<tr class="even">
<td>Select</td>
<td>select</td>
<td></td>
</tr>
<tr class="odd">
<td>SelectMany</td>
<td>multiple from clauses</td>
<td></td>
</tr>
<tr class="even">
<td>ThenBy</td>
<td>orderby …, …</td>
<td></td>
</tr>
<tr class="odd">
<td>Where</td>
<td>where</td>
<td></td>
</tr>
</tbody>
</table>