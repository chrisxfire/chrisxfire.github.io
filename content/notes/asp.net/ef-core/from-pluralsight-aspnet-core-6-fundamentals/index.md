---
title: from pluralsight aspnet core 6 fundamentals
date: 2023-05-01T13:34:12-0600
draft: false
weight: 1
---

(Notes from Pluralsight/ASP.NET Core 6 Fundamentals)

# Overview
Prior to Entity Framework Core, the approach to bring data into a web app was ADO.NET. This was low-level and required developers to know a lot of SQL. EF Core makes this easier.

<img alt="" src="Notes-from-ASP.NET-Core-6-Fundamentals-Pluralsight-course-image1.png" style="width:7.09167in;height:1.38333in" />

EF Core looks for a property named `Id` or `ClassNameId` and makes that the Primary Key in the database.

# EF Core Change Tracking
The EF Core Data context keeps tracks of changes in data objects and updates them in the database.

# Adding EF Core to an App
1.  Add packages
    1.  `Microsoft.EntityFrameworkCore.SqlServer`
    2.  `Microsoft.EntityFrameworkCore.Tools` for various commands and support for migrations
2.  Create domain classes
    1.  Table names are created on the plural of the model class
    2.  Columns are created based on the properties of the model class
    3.  EF Core will create a Foreign Key for any other type used in this model class
3.  Create a Database Context
    1.  `DbContext` is the bridge between the app's code and the database
    2.  It manages entity objects during application runtime
    3.  It persists data back to the database
    ```cs
    public class BethanysPieShopDbContext : DbContext  
    {
        public BethanysPieShopDbContext(DbContextOptions<BethanysPieShopDbContext> options)
        {
            // a DbSet signals to EF Core that there will be a table (Pie) in the database.
            // This property allows us to access records in that table.
            public DbSet<Pie> Pies { get; set; }
        }
    }
    ```
4.  Add a connection string
The connection string tells the code how to connect to the database.
It is placed in `appsettings.json:`  
    ```json
    {
        "ConnectionStrings": {
            "Server=(localdb)\mssqllocaldb;
            Database=BethanysPieShop;
            Trust_Connection=True;
            MultipleActiveResultsSets=true"
        }
    }
    ```
5.  Wire up the database in `Program.cs`
    ```cs
    builder.Services.AddDbContext<BethanysPieShopDbContext>(
        options => {
            options.UseSqlServer(
            builder.Configuration["ConnectionStrings:BethanysPieShopDbContextConnection"]);
        })
    ```

# Querying for Data Using LINQ
```cs
_bethanysPieShopDbContext.Pies // return Pies
    .Include(c => c.Category) // including the Category to which they belong (a different table)
    .Where(p => p.IsPieOfTheWeek); // but only the pies that are PieOfTheWeek
```
