---
title: relationships
date: 2023-05-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Relationships define how two entities relate to each other.
```cs
public class Blog
{
    public int Id { get; set; } // Primary Key
    public string Name { get; set; }
    public virtual Uri SiteUri { get; set; }

    public ICollection<Post> Posts { get; }
}

public class Post
{
    public string Title { get; set; }
    public string Content { get; set; }
    public DateTime PublishedOn { get; set; }
    public Archived { get; set; }

    public int BlogId { get; set; } // Foreign Key
    public Blog Blog { get; set; }
}
```

Above:
- The `Blog.Posts` property connects `Blog` to `Post.`  
- The `Post.Blog` property connects `Post` to `Blog.`
- This connection is said to be a one-to-one *relationship*.
- These properties are said to be *navigations*.  
- Note that these two *navigations* result in one *relationship*.

