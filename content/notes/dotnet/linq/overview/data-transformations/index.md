---
title: "notes > dotnet > linq > overview > data transformations"
date: 2022-11-05T22:14:36-0600
draft: true
---
# Data Transformations
LINQ can transform data. It can use a source sequence as input, modify it, and create a new output sequence.

# Join Multiple Inputs into One Output Sequence
Assume:
class Student(string First, string Last, int ID, string Street, string City, List<int> Scores)
class Teacher(string First, string Last, int ID, string City)

List<Student> students = new() { … };
List<Teacher> teachers = new() { … };

string peopleInDenver =
(from student in studnets
where student.City == "Denver"
select student.Last)
.Concat(from teacher in teachers
where teacher.City == "Denver"
select teacher.Last);

foreach (var person in peopleInDenver)
Console.WriteLine(person);

Selecting a Subset of each Source Element
var query1 = from cust in customers
select cust.City; // This select just one member of the source element

var query2 = from cust in customers
select new { Name = cust.Name, City = cust.City }; // This creates an anonymous type that holds
// two properties of the source element.