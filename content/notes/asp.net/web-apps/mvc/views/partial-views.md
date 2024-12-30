---
title: partial views
date: 2023-03-20T00:00:00-06:00
draft: false
weight: 1
---

From Pluralsight/ASP.NET Core 6 Fundamentals

# partial views
A partial view is a regular view that's used as part of another view.  Partial views exist both in MVC apps (`Views/`) and Razor Pages apps (`Pages/`).  They can also be placed in `/Views/Shared/`.  By convention, their filename starts with `_`.

Partial views depend on data passed to them from a calling (parent) view.  They do not depend on code to execute to render content.
Use partial views to break up large markup files into smaller components.
```html
@model Pie
<div>
	<div class="thumbnail">
		<img src="@Model.ImageThnumbnailUrl" alt="">
		<h3>@Model.Price.ToString("c")</h3>
	</div>
</div>
```

# define a partial view
In MVC, a `ViewResult` can return either a view or a partial view.  
In Razor Pages, a `PageModel` can return a partial view as a `PartialViewResult` object.  
Partial views do not run `_ViewStart.cshtml`.

# referencing partial views
In an MVC View:
```html
<partial name="_PieCard" mode="pie" />
```

In a Razor Pages `PageModel`:
```cs
public IActionResult OnGetPartial() =>
    Partial("_AuthorPartialRP");
```

# use a partial view
## with partial tag helper
```html
@foreach (var pie in Model.Pies)
{
	<!-- the model="pie" tells the partial view to use that object in the view -->
	<partial name="_pieCard" model="pie" />
}
```

## with asynchronous html helper 
Uses `PartialAsync` and returns an `IHtmlContent` object wrapped in a `Task<TResult>`:
```cs
@await Html.PartialAsync("_PartialName")
```
Or, with `RenderPartialAsync` which streams the output directly to the response:
```cs
@{
    await Html.RenderPartialAsync("_AuthorPartial");
}
```
The Razor code block is required since this method returns no data.  
This method performs better than `PartialAsync` in some cases.

# access data from partial views
Partial views receive a copy of the parent's `ViewData` dictionary.  `ViewData` changes in a partial view are lost when the partial view returns.
Pass an instance of `ViewDataDictionary` to a partial view:
```cs
@await Html.PartialAsync("_PartialName", customViewData)
```

Pass a model into a partial view:
```cs
@await Html.PartialAsync("_PartialName", model)
```
or to `RenderPartialAsync` which streams the content to the output.

# partial view example
`Pages/Shared/_AuthorPartialRP.cshtml` (the first partial view):
```html
@model string
<div>
    <h3>@Model</h3>
    This partial view from /Pages/Shared/_AuthorPartialRP.cshtml.
</div>
```

`Pages/ArticlesRP/_ArticleSectionRP.cshtml` (the second partial view):
```html
@using PartialViewsSample.ViewModels
@model ArticleSection
 
<h3>@Model.Title Index: @ViewData["index"]</h3>
<div>
    @Model.Content
</div>
```

## razor pages
`Pages/ArticlesRP/ReadRP.cshtml`
```html
@model ReadRPModel

<h2>@Model.Article.Title</h2>
```
```cs
// Pass the author's name to Pages\Shared\_AuthorPartialRP.cshtml 
@await Html.PartialAsync("../Shared/_AuthorPartialRP", Model.Article.AuthorName)
@Model.Article.PublicationDate

/* Loop over the Sections and pass in a section and additional ViewData to 
   the strongly typed Pages\ArticlesRP\_ArticleSectionRP.cshtml partial view. */
@{
    var index = 0;

    foreach (var section in Model.Article.Sections)
    {
        // Passes a model and a ViewData to the partial view:
        await Html.PartialAsync("_ArticleSectionRP", 
                                section,
                                new ViewDataDictionary(ViewData)
                                {
                                    { "index", index }
                                });

        index++;
    }
}
```

## mvc
`Views/Articles/Read.cshtml`
```html
@model PartialViewsSample.ViewModels.Article

<h2>@Model.Title</h2>
```
```cs
// Pass the author's name to Views\Shared\_AuthorPartial.cshtml 
@await Html.PartialAsync("_AuthorPartial", Model.AuthorName)
@Model.PublicationDate

/* Loop over the Sections and pass in a section and additional ViewData to 
   the strongly typed Views\Articles\_ArticleSection.cshtml partial view. */
@{
    var index = 0;

    foreach (var section in Model.Sections)
    {
        @(await Html.PartialAsync("_ArticleSection", 
                                section,
                                new ViewDataDictionary(ViewData)
                                {
                                    { "index", index }
                                }))

        index++;
    }
}
```
