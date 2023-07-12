---
title: notes > code > asp.net > web apps > blazor > components > childcontent renderfragment and templated components
date: 2023-07-12T00:00:00-06:00
draft: false
---

# Child Components via `ChildContent`
Components can set the content of another Component.

## Creating
Define a `ChildContent` component parameter of type `RenderFragment`:
`Shared/SomeChild.razor`
```cs
<div class="card w-25" style="margin-bottom:15px">
    <div class="card-header font-weight-bold">Child content</div>
    <div class="card-body">@ChildContent</div>
</div>

@code {
    [Parameter]
    public RenderFragment? ChildContent { get; set; }
}
```

The Component that uses the child component provides the content that it renders:
```html
@page "/render-fragment-parent"

<h1>Render child content</h1>

<SomeChild>
    Content of the child component is supplied
    by the parent component.
</SomeChild>
```

## Considerations
### Event Callbacks
Event callbacks are not supported in `RenderFragment`.

### Child components and `for` loops
Rendering components inside a `for` loop require a local index variable if that loop variable is used to render the child component's content:
```cs
<h1>Three children with an index variable</h1>

@for (int c = 0; c < 3; c++)
{
    var current = c;

    <SomeChild>
        Count: @current
    </SomeChild>
}
```

Alternatively, use a `foreach` loop and `Enumerable.Range`:
```cs
@foreach (var c in Enumerable.Range(0,3))
{
    <SomeChild>
        Count: @c
    </SomeChild>
}
```

# `RenderFragment`
`RenderFragment` is a built-in type that represents a fragment of UI content.  It allows one Component to set the content of another.

`ProfilePicture.razor.cs`
```cs
public partial class ProfilePicture
{
    [Parameter]
    public RenderFragment? ChildContent { get; set; }
}
```
`ProfilePicture.razor`
```html
<div class="profile-picture">
    @ChildContent
</div>
```
When this Component is used, the content of the Component (the value between the open/close tags) is pushed to the `ChildContent` property, which is then rendered in HTML `@ChildContent`:  

`SomeComponent.razor`
```html
<ProfilePicture>
    <img src="images/pic.jpg">
</ProfilePicture>
```

## Limitations
* The property receiving the `RenderFragment` content **must** be named `ChildContent`.
* Event callbacks are not supported with `RenderFragment`.

# Templated Components
Components that receive one or more UI templates as parameters.  These parameters can be used as rendering logic in the Component.  This allows you to create higher-level components that can be reused, like:
 * A table component that allows users to specify templates for the table's headers, rows and footer.
 * A list component that allows users to specify a template for rendering items in a list.

## Creating
Create a templated component by specifying one or more parameters of type `RenderFragment` or `RenderFragment<TValue>`.  Templated components are often generically typed.  

A `TableTemplate` component is created:  

`Shared/TableTemplate.razor`
```cs
@typeparam TItem
@using System.Diagnostics.CodeAnalysis

<table class="table">
    <thead>
        <tr>@TableHeader</tr>
    </thead>
    <tbody>
        @foreach (var item in Items)
        {
            if (RowTemplate is not null)
            {
                <tr>@RowTemplate(item)</tr>
            }
        }
    </tbody>
</table>

@code {
    [Parameter]
    public RenderFragment? TableHeader { get; set; }

    [Parameter]
    public RenderFragment<TItem>? RowTemplate { get; set; }

    [Parameter, AllowNull]
    public IReadOnlyList<TItem> Items { get; set; }
}
```

Here, the templated component is used.  The template parameters are specified using child elements that match the name of the parameters:  

`Pages/Pets1.razor`
```cs
@page "/pets1"

<h1>Pets</h1>
<!-- TableTemplate.Items expects a IReadOnlyList<T>, so we supply a List<Pet> here. 
     The TableTemplate element's Context attribute is set to the content parameter name for implicit
     child content.  It applies to all RenderFragment<TValue> template parameters: -->
<TableTemplate Items="pets" Context="pet">
    <!-- This child element matches the name of the TableTemplate component's TableHeader parameter.
         TableTemplate.TableHeader expects a RenderFragment, so we supply one:  -->
    <TableHeader>
        <th>ID</th>
        <th>Name</th>
    </TableHeader>
    <!-- Since Context="pet" is defined as an attribute on the TableTemplate element, and since
         RowTemplate expects a RenderFragment<ITem>, the parameter name "pet" is used: -->
    <RowTemplate>
        <td>@pet.PetId</td>
        <td>@pet.Name</td>
    </RowTemplate>
</TableTemplate>

@code {
    private List<Pet> pets = new()
    {
        new Pet { PetId = 2, Name = "Mr. Bigglesworth" },
        new Pet { PetId = 4, Name = "Salem Saberhagen" },
        new Pet { PetId = 7, Name = "K-9" }
    };

    private class Pet
    {
        public int PetId { get; set; }
        public string? Name { get; set; }
    }
}
```

The Component's generic type is inferred whenever possible, but can also be set explicitly:
```html {hl_lines=2}
<!-- ... -->
<TableTemplate Items="pets" TItem="Pet">
    <TableHeader>
        <th>ID</th>
        <th>Name</th>
    </TableHeader>
    <RowTemplate>
        <td>@context.PetId</td>
        <td>@context.Name</td>
    </RowTemplate>
</TableTemplate>
<!-- ... -->
```

Rather than setting the `Context` attribute on the component's element, we can set it on the child element to set the parameter name:
```html {hl_Lines=2}
<!-- ... -->
    <RowTemplate Context="pet">
        <td>@pet.PetId</td>
        <td>@pet.Name</td>
    </RowTemplate>
<!-- ... -->
```

Or, component arguments of type `RenderFragment<TValue>` has an implicit `context` parameter that can be used:
```html
<!-- ... -->
    <RowTemplate>
        <td>@context.PetId</td>
        <td>@context.Name</td>
    </RowTemplate>
<!-- ... -->
```
