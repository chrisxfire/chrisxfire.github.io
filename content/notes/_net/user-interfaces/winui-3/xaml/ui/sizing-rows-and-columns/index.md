---
title: sizing rows and columns
date: 2022-12-11T18:40:59-0700
draft: false
weight: 1
---

# Sizing
Setting `Height` to `"*"` for both `RowDefinitions` results in both rows growing proportionally:  
![](./XAML_UI_Sizing-Rows-&-Columns-image1.png)

# Star Sizing
Setting the first `RowDefinition` to `"3*"` results in a total of 4 stars for the two `RowDefinition`s, 3 of which go to the first `RowDefinition`:  
![](./XAML_UI_Sizing-Rows-&-Columns-image2.png)

# Absolute Sizing
Absolute sizing uses pixels.

Here, the first `RowDefinition` is 100 pixels; the other two split the remaining space evenly:  
![](./XAML_UI_Sizing-Rows-&-Columns-image3.png)

Setting the third row of the grid to `"Auto"` results in the row using the height of the tallest element in the row (in this case, the orange rectangle):  
![](./XAML_UI_Sizing-Rows-&-Columns-image4.png)

# Sizing with Attribute Syntax
`<Grid RowDefinitions="100,*,Auto">`

