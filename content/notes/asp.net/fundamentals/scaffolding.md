---
title: scaffolding
date: 2023-04-25T00:00:00-06:00
draft: false
weight: 1
---

From Pluralsight/ASP.NET 6 Core Fundamentals

# Overview
ASP.NET Core can *scaffold.*  This creates: 
- a `DbContext` class—the main class that coordinates EF functionality for a given data model.
- Razor pages that handle CRUD operations for an entity.

# How to Scaffold from Visual Studio
1. Create **Pages/*subfolder***
2. In **Solution Explorer** > right-click **Pages/*subfolder*** > **Add** > **New Scaffolded Item**
    a. **Installed** > **Common** > **Razor Pages** > **Razor Pages using Entity Framework (CRUD)** > **ADD**
3. In *Add Razor Pages using Entity Framework (CRUD)* dialog > 
    a. *Model class* drop-down > select **Type**
    b. *Data context class row* > **+**
        i. Change data context name to desired name (should end in "Context") > **Add** > **Add**

# How to Scaffold from Command Line
1. Install required packages:
   ```powershell
   dotnet add package Microsoft.EntityFrameworkCore.SQLite
   dotnet add package Microsoft.EntityFrameworkCore.SqlServer # scaffolding tool requires SQL Server even if app does not
   dotnet add package Microsoft.EntityFrameworkCore.Design
   dotnet add package Microsoft.EntityFrameworkCore.Tools
   dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
   dotnet add package Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore
   ```
2. Create **Pages/*subfolder***
3. Install aspnet-codegenerator scaffolding tool:  
    `dotnet tool install --global dotnet-aspnet-codegenerator`
4. Run scaffolding:   
    `dotnet aspnet-codegenerator razorpage -m Student -dc ContosoUniversity.Data.SchoolContext -udl -outDir Pages\Students --referenceScriptLibraries -sqlite`
		
# What Scaffolding Creates
The above scaffolding operation produce the following:
- Under `Pages/subfolder`:  
&emsp;&emsp;`Create.cshtml` and `Create.cshtml.cs`  
&emsp;&emsp;`Delete.cshtml` and `Delete.cshtml.cs`  
&emsp;&emsp;`Details.cshtml` and `Details.cshtml.cs`  
&emsp;&emsp;`Edit.cshtml` and `Edit.cshtml.cs`  
&emsp;&emsp;`Index.cshtml` and `Index.cshtml.cs`  
- `Data/SomeContext.cs`
- Adds the context to dependency injection in `Program.cs`
- Adds a database connection string to `appsettings.json`
