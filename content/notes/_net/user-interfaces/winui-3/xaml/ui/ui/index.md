---
title: ui
date: 2022-12-10T17:28:28-0700
draft: false
weight: 1
---
# WinUI Layout Panels
# StackPanel
Often used to stack OK/Cancel buttons.  
<img src="XAML_UI-image1.png" style="width:5.1in;height:1.70833in" />  
Note: `StackPanel.Children` can be omitted  

<img src="XAML_UI-image2.png" style="width:5.1in;height:1.69167in" />  

# Grid
Often used for the main layout of a UI.
Displays a UI's elements in rows and columns.

Add `RowDefinition`s to the `Grid.RowDefinitions` property. Specifying two `RowDefinitions` results in two rows.  
The same is true for ColumnDefinitions.  

<img src="XAML_UI-image3.png" style="width:5.04167in;height:2in" />  

`RowDefinition` has a `Height` property; `ColumnDefinition` has a `Width` property.

`ColumnSpan` and `RowSpan` properties span an element across multiple columns or rows.

# Canvas
In a canvas, setting `Left="*n*"` moves the element *n* pixels from the left. `Top`, `Bottom`, and `Right` work the same way:  
<img src="XAML_UI-image4.png" style="width:5.075in;height:1.65833in" />  

Set `Zindex` on a rectangle to a value greater than zero to render that rectangle on top of other elements.

