---
title: notes > code > asp.net > web apps > blazor > components > parameters
date: 2023-05-06T00:00:00-06:00
draft: false
---

# Component Parameters
Parameters allow Components to pass data from one another.  The `[Parameter]` attribute on a public auto property (no get/set logic) of a receiving Component defines it as a parameter:  
`PanelBody.cs`
```cs
public class PanelBody
{
    public string? Text { get; set; }
    public string? Style { get; set; }
}
```
`Shared/ParameterChild.razor`
```html
<div class="card w-25" style="margin-bottom:15px">
    <div class="card-header font-weight-bold">@Title</div>
    <div class="card-body" style="font-style:@Body.Style">
        @Body.Text
    </div>
</div>
```
```cs
@code {
    [Parameter]
    public string Title { get; set; } = "Set By Child";

    [Parameter]
    public PanelBody Body { get; set; } =
        new()
        {
            Text = "Set by child.",
            Style = "normal"
        };
}
```
`Pages/ParameterParent.razor`
```html
@* this component renders two ParameterChild components *@
@page "/parameter-parent"

<ParameterChild /> @* this component's Title will be "Set by Child" and Body.Text will be "Set by child." *@

<ParameterChild Title="Set by Parent"
                Body="@(new PanelBody() { Text = "Set by parent.", Style = "italic" })" />
```
`Pages/ParameterParent2.razor`
```html
@page "/parameter-parent-2"

<ParameterChild Title="@title" /> @* from field *@
<ParameterChild Title="@GetTitle()" /> @* from method *@
<ParameterChild Title="@DateTime.Now.ToLongDateString()" /> @* from implicit C# expression *@
<ParameterChild Title="@panelData.Title" /> @* from panelData's Title property *@
```
```cs
@code {
    private string title = "From Parent field";
    private PanelData panelData = new();

    private string GetTitle() => "From Parent method";

    private class PanelData
    {
        public string Title { get; set; } = "From Parent object";
    }
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
