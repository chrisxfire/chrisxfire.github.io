---
title: "notes > code > asp.net > web apps > blazor > components > generic types"
date: 2023-06-13T00:00:00-06:00
draft: false
---

# Generically-typed Parameters
Use `@typeparam` directive:
```html
@typeparam TItem
<!-- or: -->
@typeparam TEntity where TEntity : IEntity
```

## Example
`Shared/ListGenericTypeItems.razor`
```html
<!-- This Component, ListGenericTypeItems, will be typed as TExample: -->
@typeparam TExample

@if (ExampleList is not null)
{
    <ul>
        @foreach (var item in ExampleList)
        {
            <li>@item</li>
        }
    </ul>
}
```
```cs
@code {
    [Parameter]
   
    public IEnumerable<TExample>? ExampleList{ get; set; }
}
```

This allows you to set the type parameter of a Component that renders a `ListGenericTypeItems`:  
`Pages/GenericTypeExample.razor`
```html
@page "/generic-type-example-1"

<h1>Generic Type Example 1</h1>

<ListGenericTypeItems ExampleList="@(new List<string> { "Item 1", "Item 2" })" 
                       TExample="string" />

<ListGenericTypeItems ExampleList="@(new List<int> { 1, 2, 3 })" 
                       TExample="int" />
```

# Cascaded Generic Type Support
Add `@attribute [CascadingTypeParameter(...)]` to a Component.  By doing so, the specified generic type argument is automatically used in descendant Components that: are nested as child content in the same `.razor` file; also declare a @typeparam with the exact same name; do not have another value explicitly supplied or implicitly inferred for that type parameter.

Notes:
- Descendants obtain cascaded type parameter values from the closest ancestor that has a `CascadingTypeParameterAttribute` with a matching name.
- Matching is only performed by name. For this reason, <o>avoid cascaded generic type parameters with generic names like `T` or `TItem`.

For the following examples, consider the `ListGenericTypeItems` above and:
`Shared/ListDisplay.razor`
```html
@typeparam TExample

@if (ExampleList is not null)
{
    <ul style="color:blue">
        @foreach (var item in ExampleList)
        {
            <li>@item</li>
        }
    </ul>
}
```
```cs
@code {
    [Parameter]
    public IEnumerable<TExample>? ExampleList { get; set; }
}
```

## Example: Explicit generic types based on ancestor Components
The `GenericTypeExample2` Component sets the child content (`RenderFragment`) of two `ListGenericTypeItems` Components and specifies `ListGenericTypeItems` types (`TExample`) which are then cascaded to child Components, one with string data and one with integer data:

`Pages/GenericTypeExample2.razor`
```html
@page "/generic-type-example-2"

<h1>Generic Type Example 2</h1>

<ListGenericTypeItems TExample="string">
    <ListDisplay ExampleList="@(new List<string> { "Item 1", "Item 2" })" />
    <ListDisplay ExampleList="@(new List<string> { "Item 3", "Item 4" })" />
</ListGenericTypeItems>

<ListGenericTypeItems TExample="int">
    <ListDisplay ExampleList="@(new List<int> { 1, 2, 3 })" />
    <ListDisplay ExampleList="@(new List<int> { 4, 5, 6 })" />
</ListGenericTypeItems>
```

## Example: Infer generic types based on ancestor Components
This `GenericTypeExample3` Component infers the type of `ListGenericTypeItems`:
`Pages/GenericTypeExample3.razor`
```html
@page "/generic-type-example-3"

<h1>Generic Type Example 3</h1>

<ListGenericTypeItems ExampleList="@(new List<string> { "Item 5", "Item 6" })">
    <ListDisplay1 ExampleList="@(new List<string> { "Item 1", "Item 2" })" />
    <ListDisplay2 ExampleList="@(new List<string> { "Item 3", "Item 4" })" />
</ListGenericTypeItems>

<ListGenericTypeItems ExampleList="@(new List<int> { 7, 8, 9 })">
    <ListDisplay1 ExampleList="@(new List<int> { 1, 2, 3 })" />
    <ListDisplay2 ExampleList="@(new List<int> { 4, 5, 6 })" />
</ListGenericTypeItems>
```
