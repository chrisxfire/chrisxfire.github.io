---
title: notes > asp.net > ef core > models
date: 2023-05-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
EF Core uses a metadata *model* to describe how the app's entity types are mapped to the underlying database.  Models are configured with:
1. Fluent API
2. Data annotations
3. Conventions

Conventions are not covered in these notes.

The above order describes the precedence EF Core takes when applying configuration.

# Fluent API
Override the OnModelCreating method in the derived context and use fluent API to configure the model.  

Fluent API configuration will override *data annotations* and *conventions*.  The configuration is applied in the order the methods are called.  The latest call will override previous calls.
```cs
using Microsoft.EntityFrameworkCore;

namespace SomeNamespace;

internal class SomeContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<Blog>()
            .Property(b => b.Url)
            .IsRequired();
    }
}

public class Blog 
{
    public int BlogId { get; set; }
    public string Url { get; set; }
}
```

## Using a separate class for an entity type
To reduce the size of `OnModelCreating`, configuration for an entity type can be factored out to a separate class:
```cs
public class BlogEntityTypeConfiguration : IEntityTypeConfiguration<Blog>
{
    public void Configure(EntityTypeBuilder<Blog> builder)
    {
        builder
            .Property(b => b.Url)
            .IsRequired();
    }
}
```

Then, in `OnModelCreating`, invoke `Configure`:
```cs
new BlogEntityTypeConfiguration().Configure(modelBuilder.Entity<Blog>());
```
## EntityTypeConfiguration attribute
...

# Data annotations
```cs
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;
using Microsoft.EntityFrameworkCore;

namespace SomeNamespace;

internal class SomeContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }
}

[Table("Blogs")]
public class Blog 
{
    public int BlogId { get; set; }
    [Required]
    public string Url { get; set; }
}
