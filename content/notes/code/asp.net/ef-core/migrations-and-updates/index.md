---
title: notes > code > asp.net > ef core > migrations and updates
date: 2023-05-16T00:00:00-06:00
draft: false
weight: 1
---

# Migrate a Database via a SQL File
Create a SQL file that migrates a database already in production:
```powershell
PM> script-migration
```

This outputs a SQL file.

# Apply Migrations at Runtime
This is not recommended in production; development only.  

`Program.cs`
```cs
// ...
var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    await EnsureDatabaseIsMigrated(app.Services);

    async Task EnsureDatabaseIsMigrated(IServiceProvider services)
    {
        using var scope = services.CreateScope();
        using var ctx = scope.ServiceProvider.GetService<EmployeeManagerDbContext>();

        // if database does not exist, create it, and then run all pending migrations:
        if (ctx is not null)
            await ctx.Database.MigrateAsync();
    }
}
// ...
```

# Seeding a Database via Migrations
1. Override the `OnModelCreating` method:  
`EmployeeManagerDbContext.cs`
```cs
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    base.OnModelCreating(modelBuilder);

    // specify data to be entered into the database:
    modelBuilder.Entity<Department>().HasData(
        new Department() { Id = 1, Name = "Finance" },
        new Department() { Id = 2, Name = "Sales" },
        new Department() { Id = 3, Name = "Marketing" },
        new Department() { Id = 4, Name = "Hunman Resources" },
        new Department() { Id = 5, Name = "IT" });

    modelBuilder.Entity<Employee>().HasData(
        new Employee() { Id = 1, FirstName = "Anna", LastName = "Rockstar", DepartmentId = 2 },
        new Employee() { Id = 2, FirstName = "Julia", LastName = "Developer", DepartmentId = 5, IsDeveloper = true },
        new Employee() { Id = 3, FirstName = "Thomas", LastName = "Huber", DepartmentId = 5, IsDeveloper = true },
        new Employee() { Id = 4, FirstName = "Sara", LastName = "Metroid", DepartmentId = 1 },
        new Employee() { Id = 5, FirstName = "Ben", LastName = "Rockstar", DepartmentId = 4 });
}
```
2. Add the migration  
`PM> add-migration SeedDatabase`

3. Update the database  
`PM> update-database`
