---
title: attached properties
date: 2022-12-12T13:16:42-0700
draft: false
weight: 1
---

# in xaml
`Grid.Column` is an *attached property*; it is a property defined in the `Grid` class but set on the `Rectangle.`  
![](./XAML_UI_Attached-Properties-image1.png)

Set `Grid.Row="1"` to move to the second row of the grid.  

![](./XAML_UI_Attached-Properties-image2.png)

# In C#
```cs
var btn = new Button();
btn.SetValue(Grid.RowProperty, 1);

var row = (int)btn.GetValue(Grid.RowProperty);
```
