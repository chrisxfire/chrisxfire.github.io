---
title: troubleshooting cs0436 with shared projects in visual studio
date: 2023-04-05T19:06:48-06:00
draft: false
---

### overview
I recently ran into [compiler warning cs0436](https://learn.microsoft.com/en-us/dotnet/csharp/misc/cs0436) while working on a [solution](https://learn.microsoft.com/en-us/visualstudio/ide/solutions-and-projects-in-visual-studio?view=vs-2022) with a [shared project](https://learn.microsoft.com/en-us/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) in VS2022. If you run into the same, this might help you troubleshoot. 

### scenario
You're working on a solution that contains a project, `alpha` (which is also the name of its namspace). That project contains a [project reference](https://learn.microsoft.com/en-us/visualstudio/ide/managing-references-in-a-project?view=vs-2022) to another project, `bravo`:  

```powershell
alpha
  |--bravo
```

Shared project, `charlie`, contains code that is used by `alpha`, `bravo`, and other projects. Because of this, a [shared project reference](https://learn.microsoft.com/en-us/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager?view=vs-2022#shared-projects-tab) from `bravo` to `charlie` already exists. You also add a shared project reference from `alpha` to `charlie`:  

```powershell
alpha
  |--bravo
  |----|--charlie
```

### problem
If the references to `charlie` were [project-to-project references](https://learn.microsoft.com/en-us/visualstudio/ide/managing-references-in-a-project?view=vs-2022#project-to-project-references), there would be no issue. In such a case, `charlie` is essentially a [portable class library](https://learn.microsoft.com/en-us/xamarin/cross-platform/app-fundamentals/pcl?tabs=windows) and Visual Studio references its DLL. However, `charlie` is a shared project, which means its code is compiled into the executable project (`alpha` and/or `bravo`) just as if it were included natively in that project. This now result in a cs-0436 that reads:  
<br>

> The type 'SomeType' in 'alpha' conflicts with the imported type 'SomeType2' in 'alpha'. Using the type defined in 'alpha'.  

<br>

Since `bravo` references `charlie`, it imports `charlie`s types. Since `alpha` also references `charlie`, it imports `charlie`s types *twice*: once directly from `charlie` and once through its reference to `bravo`.

### solution
The solution is simple: remove the shared project reference from `alpha` to `charlie`.  Code in `alpha` that needs types in `charlie` need simply include a using statement:  

```cs
using charlie
```

The final reference map should then look like this:  

```powershell
alpha
  |--bravo
       |--charlie
```