---
title: "notes > swe > patterns > creational > abstract factory"
date: 2023-03-04T18:52:25-0700
draft: true
---
# Abstract Factory
Type:Creational
Purpose:Produce families of related objects without specifying their concrete classes.
Use when:You have a class with a set of factory methods that blur its primary responsibility.
Principles:Single Responsibility Principle; Open/Closed Principle
Complexity:2/3
Popularity:3/3
# In .NET:`IHttpClientFactory`
# 
# Overview
<img src="media/Creational_Abstract-Factory-image1.png" style="width:5.65in;height:3.53333in" alt="Abstract Factory design pattern" />

# 
1.  Abstract Products declare interfaces for a set of distinct but related products which make up a product family.
2.  Concrete Products are various implementations of abstract products, grouped by variants. Each abstract product (chair/sofa) must be implemented in all given variants (Victorian/Modern).
3.  The Abstract Factory interface declares a set of methods for creating each of the abstract products.
4.  Concrete Factories implement creation methods of the abstract factory. Each concrete factory corresponds to a specific variant of products and creates only those product variants.
5.  Although concrete factories instantiate concrete products, signatures of their creation methods must return corresponding abstract products. This way the client code that uses a factory doesn’t get coupled to the specific variant of the product it gets from a factory. The Client can work with any concrete factory/product variant, as long as it communicates with their objects via abstract interfaces.
# 
# Implementing
Create a matrix of distinct product types and their variants.
<img src="media/Creational_Abstract-Factory-image2.png" style="width:4.25in;height:3.53333in" />

Declare abstract product interfaces for all product types. Make all concrete product classes implement these.
public interface IChair
{
void SitOn();
}

public class VictorianChair : IChair
{
void SitOn()
{
…
}
}

public class ArtDecoCHair : IChair { … }

public class ModernChar : IChair { … }

public interface ISofa { … }

…

public interface ICouch { … }

…

Declare the abstract factory interface with a set of creation methods for all abstract products.
public interface IFactory
{
IChair CreateChair();
ICouch CreateCouch();
ITable CreateTable();
}

Implement a set of concrete factory classes, one for each product variant.
public class ArtDecoFactory: IFactory
{
public IChair CreateChair() { … }
public ICouch CreateCouch() { … }
public ITable CreateTable() { … }
}

public class VictorianFactory : IFactory { … }

public class ModernFactory : IFactory { … }

Create factory initialization code. It should instantiate one of the concrete factory classes. Pass this object to all classes that construct products.
public class Client
{
public void Main()
{
SomeMethod(new ArtDecoFactory());
}

public void SomeMethod(IAbstractFactory factory)
{
var chair = factory.CreateChair();
var couch = factory.CreateCouch();
var table = factory.CreateTable();

chair.SitOn();
}
}

Refactor existing code: Scan through code and find all direct class to product constructors. Replace them with calls to the appropriate creation method on the factory object.
<img src="media/Creational_Abstract-Factory-image3.png" style="width:5.25in;height:3.95in" />

