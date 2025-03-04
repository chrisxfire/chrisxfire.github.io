---
title: concepts
date: 2022-12-28T20:32:09-0700
draft: false
weight: 1
---

# WinUI's Flexible Content Model
Data Templates define a user interface for data. It is often defined as a Resource.

# contentcontrol
Consider `ContentControl` (the base class of `Button`, `CheckBox`, `ListViewItem`, others).
- `ContentControl` defines the `Content` property which is of type object.
- This is what allows you to assign an arbitrary object (and not just a string) to the `Content` property.

# ContentControl's `Content` Property
- If a `UIElement` (base class of `Panels` and `Controls`) is assigned to `ContentControl`'s `Content` property, *it is rendered*.
- If any other object is assigned to `ContentControl`'s `Content` property, *the result of its* `ToString` *method is rendered*.

# datatemplate
Instead of relying on the `ToString` result, you can use a DataTemplate to define a UI for the object. In the DataTemplate:
- UI elements like panels and controls can be used.
- You can bind to the properties of the object that was assigned to the `Content` property.  

`DataTemplate` is an object that is assigned to `ContentTemplate` property of `ContentControl`:  
![](./XAML_Data-Templates-(Concepts)-image1.png)

# itemscontrol
`ContentControl` is for a single object. `ItemsControl` is for a collection of objects.  
`ItemsControl` is the base class of `ListView`, `ComboBox`, others.

# ItemsControl `ItemsSource` Property
`ItemsControl` has an `ItemsSource` property to which you can assign a collection of objects.  
- The same rules as `ContentControl.Content` apply to `ItemsControl.ItemsSource`.

# datatemplate
A DataTemplate can be assigned to `ItemsControl`'s `ItemTemplate` property:  
![](./XAML_Data-Templates-(Concepts)-image2.png)
