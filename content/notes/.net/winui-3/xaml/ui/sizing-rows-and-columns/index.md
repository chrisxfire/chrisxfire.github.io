---
title: notes > .net > winui 3 > xaml > ui > sizing rows and columns
date: 2022-12-11T18:40:59-0700
draft: false
---
# Sizing
Setting `Height` to `"*"` for both `RowDefinitions` results in both rows growing proportionally:  
<img src="XAML_UI_Sizing-Rows-&-Columns-image1.png" style="width:5.075in;height:2.075in" />  

# Star Sizing
Setting the first `RowDefinition` to `"3*"` results in a total of 4 stars for the two `RowDefinition`s, 3 of which go to the first `RowDefinition`:  
<img src="XAML_UI_Sizing-Rows-&-Columns-image2.png" style="width:5.075in;height:2.03333in" />  

# Absolute Sizing
Absolute sizing uses pixels.

Here, the first `RowDefinition` is 100 pixels; the other two split the remaining space evenly:  
<img src="XAML_UI_Sizing-Rows-&-Columns-image3.png" style="width:5.13333in;height:2.125in" />  

Setting the third row of the grid to `"Auto"` results in the row using the height of the tallest element in the row (in this case, the orange rectangle):  
<img src="XAML_UI_Sizing-Rows-&-Columns-image4.png" style="width:5.00833in;height:2.06667in" />  

# Sizing with Attribute Syntax
`<Grid RowDefinitions="100,*,Auto">`

