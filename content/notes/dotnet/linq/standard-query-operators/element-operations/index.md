---
title: "notes > dotnet > linq > standard query operators > element operations"
date: 2022-11-10T20:58:21-0700
draft: true
---
Element operations return a single, specific element from a sequence.

# Methods
<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 58%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
<th>Query expression</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ElementAt(OrDefault)</td>
<td>Returns the element at the specified index</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>First(OrDefault)</td>
<td>Returns the first element of a collection, or the first element that satisfies a condition</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>Last(OrDefault)</td>
<td>Returns the last element of a collection, or the last element that satisfies a condition</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>Single(OrDefault)</td>
<td><p>Returns the only element of a collection that satisfies a condition.</p>
<p>Throws InvalidOperationException if no such element or more than one such element.</p></td>
<td>N/A</td>
</tr>
</tbody>
</table>