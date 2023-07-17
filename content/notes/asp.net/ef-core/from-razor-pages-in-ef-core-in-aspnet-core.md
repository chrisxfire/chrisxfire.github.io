---
title: notes > asp.net > ef core > from razor pages in ef core in aspnet core
date: 2023-04-25T12:36:11-0600
draft: false
weight: 1
---
Notes from [Razor Pages with Entity Framework Core in ASP.NET Core - Tutorial 1 of 8 | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/data/ef-rp/intro?view=aspnetcore-7.0)

# Creating a Database
`Program.cs`  
```cs
using (var scope = app.Services.CreateScope())
{
    var services = scope.ServiceProvider;

    var context = services.GetRequiredService<SchoolContext>();
    context.Database.EnsureCreated();
    // DbInitializer.Initialize(context);
}
```
The `EnsureCreated` method checks if the database exists. If not, it creates the database and schema.

This allows for the following workflow for data model changes:
1.  Delete the database
2.  Change the data model (ie: add an EmailAddress field)
3.  Run the app
4.  `EnsureCreated` will create a database with the new schema

When data exists that cannot be lost, use *migrations* instead of `EnsureCreated`.

# Connection Strings
Connection strings are passed to `DbContexts` by calling a method on a `DbContextOptions` object.  
In local development, ASP.NET Core reads the string from `appsettings.json` or `appsettings.Development.json`.

# Primary Keys
By default, EF Core interprets a property that's named `ID` or `*classname*ID` as the primary key.

# Navigation Properties
*Navigation properties* are properties in a model that hold other entities related to this entity. For example, a `Student` may have a navigation property of `Enrollments` to hold all the `Enrollment` entities for that `Student`.  

EF Core interprets a property as a foreign key if it's named `<navigation property name><primary key property name>`. For example, `StudentID` is the foreign key for the `Student` navigation property, since the `Student` entity's primary key is ID.
- Foreign key properties can also be named `<primary-key-property-name>` such as `CourseID` since the `Course` entity's primary key is `CourseID`.

# Seeding a Database
Convention: create `Data/DbInitializer.cs` with code to [seed a database with test data](https://learn.microsoft.com/en-us/aspnet/core/data/ef-rp/intro?view=aspnetcore-7.0&tabs=visual-studio#seed-the-database).

# Scaffolding
EF Core's scaffolding engine does not support nullable reference types—the models used in scaffolding cannot use them either.  
Scaffolding will automatically register the Context class it creates with DI.

# Database Context (DbContext)
The database context class derives from `Microsoft.EntityFrameworkCore.DbContext` and specifies which entities are included in the data model. It is the main class that coordinates EF Core functionality for a given data model.

This class lives in `Data/*Some*Context.cs`. This service is registered with DI.

# Entity Set (DbSet)
An *entity set* typically corresponds to a database table.  
An *entity* corresponds to a row in the table.

# Entity States
The `DbContext` keeps track of the sync state between entities in memory and their corresponding rows in the database.
An entity has these states:
- `Added`—entity does not yet exist in database; `SaveChanges` will issue an `INSERT` statement
- `Unchanged`—no changes to this entity
- `Modified`—some or all of the entity's properties have been modified; `SaveChanges` issues an `UPDATE` statement
- `Deleted`—entity marked for deletion; `SaveChanges` issues a `DELETE` statement
- `Detached`—entity is not being tracked by database context

# Visual Studio
Visual Studio can view databases: View > SQL Server Object Explorer (SSOX)

# Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore
This package provides ASP.NET Core middleware for EF Core error pages.

# Asynchronous Programming in EF Core
EF Core uses async operations by default. However:
- Only statements that cause queries or commands to be sent to the database are executed asynchronously.
- An EF Core context is not thread safe — do not execute parallel operations.

# Reading Entities
To read a single entity, prefer `FirstOrDefaultAsync` (which returns null if nothing is found) over:
- `SingleOrDefaultAsync` which throws an exception if there's more than one entity that satisfies the query filter
- `FindAsync` because you cannot use `Include` with this method.

However, when you do not have to use `Include` for related data, prefer `FindAsync` as it is more efficient.
