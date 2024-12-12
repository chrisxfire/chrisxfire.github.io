---
title: templates
date: 2023-01-01T09:12:52-0700
draft: false
weight: 1
---

# Overview
There are *user controls* and *custom controls*:
- User controls have hardcoded UI's in their XAML files
- Custom controls have UIs defined in a ControlTemplate.
  - Set the Template property to change the UI of a custom control.
  - This allows for changing the UI even if you don't own the code for the control.
- All WinUI controls (Button, TextBox, CheckBox, etc) are implemented as custom controls.

# Define the Look of a Custom Control
Starting with a normal grey button…  
![](./XAML_Control-Templates-image1.png)

Now:
1.  Assign a `ControlTemplate` with target type `Button` to the `Button`'s `Template` property.
2.  Create the UI for the Button (using any UI element like `Shape`, `Panel`, etc) inside the `ControlTemplate` tag.

You now have an orange circular button:  
![](./XAML_Control-Templates-image2.png)

# Setting the Button's `Background` property to Blue has no effect because it is overriden by the `ControlTemplate`:  
![](./XAML_Control-Templates-image3.png)

# Use the `TemplateBinding` static markup extension to reference a property:  
![](./XAML_Control-Templates-image4.png)

# A `ControlTemplate` can also be defined in a Style:  
![](./XAML_Control-Templates-image5.png)
