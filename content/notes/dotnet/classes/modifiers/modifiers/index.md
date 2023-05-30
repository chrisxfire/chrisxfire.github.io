---
title: "notes > dotnet > classes > modifiers > modifiers"
date: 2022-02-17T20:57:51-0700
draft: true
---
# Access Modifiers
publicAccess is unrestricted.
private Access is limited to this type in this assembly only.
protectedAccess is limited to this type or derivatives, or derivatives in a referenced assembly.
internalAccess is limited to this assembly only.
protected internalCombination of protected + internal.
private protectedCombination of private + protected.


<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 19%" />
<col style="width: 19%" />
<col style="width: 24%" />
<col style="width: 22%" />
</colgroup>
<thead>
<tr class="header">
<th>Modifer</th>
<th><p>This Assembly</p>
<p>Derived Type</p></th>
<th><p>This Assembly</p>
<p>Other Type</p></th>
<th><p>External Assembly</p>
<p>Derived Type</p></th>
<th><p>External Assembly</p>
<p>Other Type</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public</td>
<td>yes</td>
<td>yes</td>
<td>yes</td>
<td>yes</td>
</tr>
<tr class="even">
<td>private</td>
<td>no</td>
<td>no</td>
<td>no</td>
<td>no</td>
</tr>
<tr class="odd">
<td>protected</td>
<td>yes</td>
<td>no</td>
<td>yes</td>
<td>no</td>
</tr>
<tr class="even">
<td>internal</td>
<td>yes</td>
<td>yes</td>
<td>no</td>
<td>no</td>
</tr>
<tr class="odd">
<td><p>protected</p>
<p>internal</p></td>
<td>yes</td>
<td>yes</td>
<td>yes</td>
<td>no</td>
</tr>
<tr class="even">
<td><p>private</p>
<p>internal</p></td>
<td>yes</td>
<td>no</td>
<td>no</td>
<td>no</td>
</tr>
</tbody>
</table>

# Other Modifiers
virtualThis member *may* be overridden in a derived type.
abstractThis type <u>must</u> be overridden in a derived type.
- It has no implementation.
- It cannot be instantiated.
overrideThis member provides a new implementation of the base type's virtual or abstract member.
sealedThis type cannot be further overridden in a derived type.
- Only overridden types can be sealed.