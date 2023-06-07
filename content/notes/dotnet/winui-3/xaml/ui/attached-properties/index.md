---
title: notes > dotnet > winui 3 > xaml > ui > attached properties
date: 2022-12-12T13:16:42-0700
draft: true
---
# In XAML
`Grid.Column` is an *attached property*; it is a property defined in the `Grid` class but set on the `Rectangle.`
<img src="media/XAML_UI_Attached-Properties-image1.png" style="width:5.00833in;height:2.06667in" />

Set `Grid.Row="1"` to move to the second row of the grid.

<img src="media/XAML_UI_Attached-Properties-image2.png" style="width:5.025in;height:2.61667in" />

# In C#
var btn = new Button();
btn.SetValue(Grid.RowProperty, 1);

var row = (int)btn.GetValue(Grid.RowProperty);

## Access Attached Properties with Static Methods

