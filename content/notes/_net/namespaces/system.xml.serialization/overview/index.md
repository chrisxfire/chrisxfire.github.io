---
title: notes > _net > namespaces > system.xml.serialization > overview
date: 2021-12-23T16:29:42-0700
draft: false
---
# [System.Xml.Serialization Namespace](https://docs.microsoft.com/en-us/dotnet/api/system.xml.serialization?view=net-6.0)

# Serializing
When serializing a type with `XmlSerializer`, only public fields and properties are included, and the type must have a parameterless constructor.

```cs
List<Person> people = … // Create an object graph of Person objects in a List of Persons.
XmlSerializer xs = new(people.GetType()); // Create object that formats a List of Persons as XML.
using (FileStream stream = File.Create(path))
{
    xs.Serialize(stream, people); // Serialize the object graph to the stream.
}
```
# Deserializing
```cs
using (FileStream xmlLoad = File.Open(path, FileMode.Open))
{
    List<Person>? loadedPeople = xs.Deserialize(xmlLoad) as List<Person>; // Deserialize and cast object graph
}
```
# Decorators
- `[XmlAttribute("shortname")]` — Use  to specify a short name for properties.