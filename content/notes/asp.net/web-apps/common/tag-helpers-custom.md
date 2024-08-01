---
title: tag helpers custom
date: 2023-05-04T00:00:00-07:00
draft: false
weight: 1
---

# Overview
Tag helpers are plain C# classes that inherit from `TagHelper.`  
They can be placed anywhere and must be named `NameOfElementTagHelper`.  
They override Process or `ProcessAsync.`  This method returns HTML which is inserted where the tag helper is invoked.

Example:  
`/TagHelpers/EmailTagHelper.cs`
```cs
public class EmailTagHelper : TagHelper
{
    public void override Process(TagHelperContext context, TagHelperOutput output)
    {
        // mailto links use the anchor tag, so the tag name of this output will be "a"
        output.TagName = "a";
        
        // set the href attribute to the value of mailto:<address>:
        output.Attributes.SetAttribute("href", "mailto:" + Address);
        
        // content goes between the open and closing tags:
        output.Content.SetContent(Content);
        
    }
}
```
Add the Tag Helper to imports:  
`@addTagHelper BethanysPieShop.TagHelpers.*, BethanysPieShop`

# Using Custom Tag Helpers
The above Tag Helper creates a new element called email:
```html
<email
    address="info@@bethanyspieshop.com"
    content="Contact us">
</email>
```

# Testing Tag Helpers
Assuming this tag helper:
```cs
public class EmailTagHelper : TagHelper
{
    public string? Address { get; set; }
    public string? Content { get; set; }

    public override void Process(TagHelperContext context, TagHelperOutput output)
    {
        // mailto links use the anchor tag, so the tag name of this output will be "a"
        output.TagName = "a";
        // set the href attribute to the value of mailto:<address>:
        output.Attributes.SetAttribute("href", "mailto:" + Address);
        // content goes between the open and closing tags:
        output.Content.SetContent(Content);
    }
}
```

Here is a test class for it:
```cs
[Fact]
public void Generates_Email_Link()
{
    // Arrange
    var emailTagHelper = new EmailTagHelper() { Address="test@bethanyspieshop.com", Content="Email" }; ;

    var tagHelperContext = new TagHelperContext(
        new TagHelperAttributeList(),
            new Dictionary<object, object>(), string.Empty);

    var content = new Mock<TagHelperContent>();

    var tagHelperOutput = new TagHelperOutput("a",
        new TagHelperAttributeList(),
        (cache, encoder) => Task.FromResult(content.Object));

    // Act
    emailTagHelper.Process(tagHelperContext, tagHelperOutput);

    // Assert
    Assert.Equal("Email", tagHelperOutput.Content.GetContent());
    Assert.Equal("a", tagHelperOutput.TagName);
    Assert.Equal("mailto:test@bethanyspieshop.com", tagHelperOutput.Attributes[0].Value);
}
```
