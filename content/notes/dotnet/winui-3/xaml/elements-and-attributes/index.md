---
title: notes > dotnet > winui 3 > xaml > elements and attributes
date: 2022-12-09T20:33:41-0700
draft: true
---
<img src="media/XAML_Elements-&-Attributes-image1.png" style="width:3.175in;height:2.09167in" />
# Elements & Attributes
## <u>Attribute Syntax</u>
`Button` is an *element*; in XAML, elements are mapped to Classes.
<Button
Content="Add customer"
</Button>
^ Closing element tag.

Since the element has no content between the opening/closing
tags, it can instead be written as a self-closing element:
<Button
x:Name="btnAddCustomer" This is a a special XAML attribute.
Content="Add customer" `Content` is an *attribute*; in XAML, attributes can map to *properties*.
Clicked="Button_Click" /> This attribute is mapped to an *event* of the button, `Button_Click`.

If this were C#, the corresponding code would be:
var btnAddCustomer = new Button {
Content = "Add customer"
};

btnAddCustomer.Click += Button_Click;

## <u>Property-element Syntax</u>
Use when you need to assign a complex object to a property.

This `Button` element maps to the `Button` class; it *creates an object of type `Button`*; it is known as an *object element*.
<Button x:Name="btnAddCustomer"
…
This element is in *Class.Property* form; it maps to the `Content` property of the `Button` class; it is known as a *property element*.
<Button.Content> Using *property element syntax*, we can assign a complex object to this property.
<StackPanel Orientation="Horizontal"> "Horizontal" means align the SymbolIcon and the TextBlock horizontally.
<SymbolIcon Symbol="AddFriend"/>
The Margin property uses format left right top bottom:
<TextBlock Text="Add customer" Margin="5 0 0 0"/>
</StackPanel>
</Button.Content>

The resulting Button:
<img src="media/XAML_Elements-&-Attributes-image2.png" style="width:1.84167in;height:0.59167in" />

## <u>Content Syntax</u>
Use to set content directly in an object element.

How it works:
<img src="media/XAML_Elements-&-Attributes-image3.png" style="width:5.425in;height:3.49167in" />

Content syntax is always used when you put content in an object element without the property element.

## <u>Collection Syntax</u>
Instead of assigning a value to a property, the XAML parser calls the Add method on the collection to add every element to the collection:
<img src="media/XAML_Elements-&-Attributes-image4.png" style="width:5.40833in;height:2.625in" />

`ContentControl` is a base class of `Button`.

