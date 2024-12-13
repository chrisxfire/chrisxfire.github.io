---
title: creating substitutes
date: 2023-10-30T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://nsubstitute.github.io/help/creating-a-substitute/)  

# Substitutes
```cs
var substitute = Substitute.For<ISomeInterface>();
// or
var someClass = Substitute.For<SomeClassWithCtorArgs>(5, "hello world");
```

## Substituting for Multiple Types
Substituting for multiple interfaces:
```cs
var command = Substitute.For<ICommand, IDisposable>();
var runner = new CommandRunner(command);

runner.RunCommand();

command.Received().Execute();
((IDisposable)command).Received().Dispose();
```

Substituting for multiple interfaces and a class:
```cs
var substitute = Substitute.For(
		new[] { typeof(ICommand), typeof(ISomeInterface), typeof(SomeClassWithCtorArgs) },
		new object[] { 5, "hello world" }
	);
Assert.IsInstanceOf<ICommand>(substitute);
Assert.IsInstanceOf<ISomeInterface>(substitute);
Assert.IsInstanceOf<SomeClassWithCtorArgs>(substitute);
```

## Substituting for Delegates
```cs
var func = Substitute.For<Func<string>>();

func().Returns("hello");
Assert.AreEqual("hello", func());
```