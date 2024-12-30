---
title: code reuse
date: 2023-09-08T00:00:00-06:00
draft: false
weight: 1
---

# overview
These notes discuss the differences between *project references*, *file references*, *class libraries*, and *shared projects* in Visual Studio.

# references 
A *reference* is an entry in a project file that Visual Studio uses to locate a code component.

Consider buildable project `A` which references buildable project `B`. Since `B` (like `A`) produces an assembly, you can reference either the *project* (*project reference*) or the *assembly* (*file reference*). 

## project references 
A *project reference* is a references to a project's code even if it contains an assembly.  

If `A` references `B`'s project, this creates a dependency between the two in the build system:
- If a build is requested on `A`:
  - If `B` has changed since the last time `A` was built:
    - `B` will be rebuilt
  - `A` will be built.

In Visual Studio, project references are added from **Reference Manager > Projects**.

## file references
If `A` references `B`'s assembly (*file reference*), this does not create a dependency. However, this also means that `A` could be referencing an outdated version of `B`.

With *project references*, `A` is always referring to the latest version of `B`'s code.  
With *file references*, `A` refers to a specific point-in-time binary output of `B`.  

In Visual Studio, file references are added from **Reference Manager > Browse**.

# class libraries
*Class libraries* are also called *.NET standard class libraries*.  Formerly, they were known as *Portable Class Libraries*.

In Visual Studio, class libraries are referenced from **Reference Manager > Projects**.

# shared projects
*Shared projects* are code that is not compiled into an independent, buildable project.  Instead, the code is referenced by—and compiled into—a buildable project.

Consider project buildable project `X` and shared project `Y`. If `X` references `Y`, when `X` is compiled, the code in `Y` will be compiled into `X`'s assembly.

Shared projects allow for compiler directives that can help incorporate platform-specific functionality into a shared codebase. For example, you may have a shared codebase that is used for a mobile app that runs in iOS and Android. The shared project can contain compiler directives to indicate that only certain sections of the code are to be compiled based on the target operating system.

In Visual Studio, shared projects are referenced from **Reference Manager > Shared Projects**.