---
title: "notes > dotnet > winui 3 > xaml > data templates > concepts"
date: 2022-12-28T20:32:09-0700
draft: true
---
# Overview
Data Templates define a user interface for data. It is often defined as a Resource.

# WinUI's Flexible Content Model
## ContentControl
Consider `ContentControl` (the base class of `Button`, `CheckBox`, `ListViewItem`, others).
- `ContentControl` defines the `Content` property which is of type object.
- This is what allows you to assign an arbitrary object (and not just a string) to the `Content` property.

## ContentControl's Content Property
- If a `UIElement` (base class of `Panels` and `Controls`) is assigned to `ContentControl`'s `Content` property, *it is rendered*.
- If any other object is assigned to `ContentControl`'s `Content` property, *the result of its* `ToString` *method is rendered*.

## DataTemplate
Instead of relying on the `ToString` result, you can use a DataTemplate to define a UI for the object. In the DataTemplate:
- UI elements like panels and controls can be used.
- You can bind to the properties of the object that was assigned to the `Content` property.

DataTemplate is an object that is assigned to `ContentTemplate` property of `ContentControl`:
<img src="media/XAML_Data-Templates-(Concepts)-image1.png" style="width:2.3in;height:2.40833in" />

## ItemsControl
`ContentControl` is for a single object. `ItemsControl` is for a collection of objects.
`ItemsControl` is the base class of `ListView`, `ComboBox`, others.

## ItemsControl ItemsSource Property
`ItemsControl` has an `ItemsSource` property to which you can assign a collection of objects.
- The same rules as `ContentControl.Content` apply to `ItemsControl.ItemsSource`.

## DataTemplate
A DataTemplate can be assigned to `ItemsControl`'s `ItemTemplate` property:
<img src="media/XAML_Data-Templates-(Concepts)-image2.png" style="width:2.33333in;height:2.375in" />
