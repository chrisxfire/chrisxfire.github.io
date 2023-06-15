---
title: notes > .net > fundamentals > object oriented programming > abstract classes
date: 2022-02-17T20:25:50-0700
draft: false
---
# Abstract Classes
Abstract classes and members are incomplete and <u>must</u> be implemented in a derived class.
- They cannot be directly instantiated.
- They cannot be static.
- They *may* contain constructors.

# Abstract, Concrete, Virtual, and Static Members
Abstract classes may contain abstract, concrete, virtual, and static members:
- Abstract members have no implementation.
  - They <u>must</u> be implemented in the derived class. Use the override keyword.
  - A field cannot be abstract.
  - They cannot be static.
- Concrete members have an implementation. They are inherited in the derived class like normal.
  - They *may* be re-implemented in the derived class with the new keyword.
  - They *may* be static.
- Virtual members have an implementation. They are inherited in the derived class like normal.
  - They *may* be re-implemented in the derived class with the override keyword.
  - They cannot be static.
- Static members have an implementation.
  - They may be re-implemented in the derived class with the new keyword.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 26%" />
<col style="width: 23%" />
<col style="width: 16%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Member</strong></p>
<p><strong>Modifier</strong></p></th>
<th><p><strong>Default</strong></p>
<p><strong>Implementation</strong></p></th>
<th><strong>Re-implement</strong></th>
<th><strong>Keyword</strong></th>
<th><strong>Static</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>abstract</td>
<td>No</td>
<td>Must</td>
<td>override</td>
<td>No</td>
</tr>
<tr class="even">
<td>virtual</td>
<td>Yes</td>
<td>May</td>
<td>override</td>
<td>No</td>
</tr>
<tr class="odd">
<td>(concrete)</td>
<td>Yes</td>
<td>May</td>
<td>new</td>
<td>May</td>
</tr>
<tr class="even">
<td>static</td>
<td>Yes</td>
<td>May</td>
<td>new</td>
<td>Yes</td>
</tr>
</tbody>
</table>


# Sealed
The sealed keyword prevents inheritance of a class, or of class members that were previously marked virtual.
Because a sealed class cannot be the base class of a derived class, it also cannot be abstract.
