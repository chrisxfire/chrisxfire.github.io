---
title: design patterns
date: 2022-11-14T09:55:57-0700
draft: false
weight: 1
---

# the 23 design patterns from the gang of four
<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 26%" />
<col style="width: 26%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><strong></strong></th>
<th><strong>Creational</strong></th>
<th><strong>Structural</strong></th>
<th><strong>Behavioral</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Class</strong></td>
<td>Factory Method</td>
<td>Adapter (class)</td>
<td><p>Interpreter</p>
<p>Template Method</p></td>
</tr>
<tr class="even">
<td><strong>Object</strong></td>
<td><p>Abstract Factory</p>
<p>Builder</p>
<p>Prototype</p>
<p>Singleton</p></td>
<td><p>Adapter (object)</p>
<p>Bridge</p>
<p>Composite</p>
<p>Decorator</p>
<p>Facade</p>
<p>Flyweight</p>
<p>Proxy</p></td>
<td><p>Chain of Responsibility</p>
<p>Command</p>
<p>Iterator</p>
<p>Mediator</p>
<p>Memento</p>
<p>Observer</p>
<p>State</p>
<p>Strategy</p>
<p>Visitor</p></td>
</tr>
</tbody>
</table>


![](./Design-Patterns-image1.png)

![](./Design-Patterns-image2.png)

# concepts
Factory—a method or class that produces something:
- A method that creates a GUI
- A class that creates users
- A static method that calls a class constructor in a certain way

Creation Method—a method that creates objects.
- Every *factory method* is a *creation method*, but not every *creation method* is a *factory method*.
- It is a wrapper around a constructor call. This can prevent the constructor from needing to be changed.  

Static Creation Method—a *creation method* declared static. 

Simple Factory Pattern—a class that has one creation method with a large conditional that, based on method parameters, chooses which product class to instantiate and then return.  

Factory Method Pattern—a creational design pattern that provides an interface for creating objects but allows subclasses to alter the type of an object that will be created.  

Abstract Factory Pattern—a creational design pattern that allows producing families of related (or dependent) objects without specifying their concrete classes.  
