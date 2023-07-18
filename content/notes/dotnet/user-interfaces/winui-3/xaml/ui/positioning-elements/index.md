---
title: notes > .net > user interfaces > winui 3 > xaml > ui > positioning elements
date: 2022-12-11T19:00:58-0700
draft: false
weight: 1
---
# Positioning Elements with Layout Properties
<img src="XAML_UI_Positioning-Elements-image1.png" style="width:4.79167in;height:1.95in" />  

`HorizontalAlignment` property has values of `Left`, `Center`, `Right`, `Stretch`  
`VerticalAlignment` property has values of `Top`, `Center`, `Bottom`, `Stretch`  

When `Width` and `Height` properties are set, the element will not grow or shrink:  
<img src="XAML_UI_Positioning-Elements-image2.png" style="width:4.85in;height:1.99167in" />  

## Margin
`Margin="<Left Top Right Bottom>"`  
`Margin="50"` results in a margin of 50 pixels on all sides.  
`Margin="50 10"` results in 50 pixels for left and right margins and 10 pixels for top and bottom margins.  

