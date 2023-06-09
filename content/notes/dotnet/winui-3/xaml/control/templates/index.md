---
title: notes > dotnet > winui 3 > xaml > control > templates
date: 2023-01-01T09:12:52-0700
draft: false
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
<img src="XAML_Control-Templates-image1.png" style="width:6.04167in;height:1.675in" />  

Now:
1.  Assign a `ControlTemplate` with target type `Button` to the `Button`'s `Template` property.
2.  Create the UI for the Button (using any UI element like `Shape`, `Panel`, etc) inside the `ControlTemplate` tag.

You now have an orange circular button:  
<img src="XAML_Control-Templates-image2.png" style="width:6.10833in;height:1.70833in" />  

# Setting the Button's `Background` property to Blue has no effect because it is overriden by the `ControlTemplate`:  
<img src="XAML_Control-Templates-image3.png" style="width:5.975in;height:1.53333in" />  

# Use the `TemplateBinding` static markup extension to reference a property:  
<img src="XAML_Control-Templates-image4.png" style="width:5.975in;height:1.49167in" />  

# A `ControlTemplate` can also be defined in a Style:  
<img src="XAML_Control-Templates-image5.png" style="width:3.825in;height:1.79167in" />  