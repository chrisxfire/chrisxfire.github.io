---
title: notes > .net > user interfaces > winui 3 > xaml > control > create a controltemplate
date: 2023-01-01T09:54:59-0700
draft: false
weight: 1
---
# Create a Control Template
Create a copy of the default `ControlTemplate` for `CheckBox`:  

Solution Explorer > **Dependencies** > **Packages** > **Microsoft.WindowsAppSDK** …  
This package contains the WinUI library and a generic.xaml file that contains all the styles for the controls of WinUI.  

… Right-click **Microsoft.WindowsAppSDK** > **Open file in Explorer** > **lib** > **net6.0-windows.10.x.y.z** > **Microsoft.WinUI** > **Themes** > **generic.xaml**  

`generic.xaml`  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image1.png" style="width:7.25833in;height:3.25in" />  
Copy the above Style.  

`Resources/Styles.xaml`  
Paste the style for the `CheckBox` copied from generic.xaml:

<img src="XAML_Control-Templates_Create-a-ControlTemplate-image2.png" style="width:5.59167in;height:2.45833in" />  

`Resources/Styles.xaml`  
The `CheckBox` is actually a `Grid`:  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image3.png" style="width:5.04167in;height:1.45833in" />  

The `VisualStateGroups` define the UI of the `CheckBox` based on its state. For example, if the `CheckBox` is unchecked, then `UncheckedNormal` is active:  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image4.png" style="width:4.275in;height:2.425in" />  

The `CheckBox` (`Grid`) contains two column defintions:  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image5.png" style="width:2.88333in;height:0.91667in" />  

The first `ColumnDefinition` has a `Rectangle` and a `FontIcon` which is actually the checkmark (defined in its `Glyph` property):  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image6.png" style="width:5.65833in;height:2.35833in" />  

This `ContentPresenter` displays the `Content` of the `CheckBox`:  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image7.png" style="width:5.53333in;height:1.65833in" />  

To change the checkmark, go to the **FontIcon** > right-click **SymbolThemeFontFamily** > **Go to definition**:  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image8.png" style="width:5.61667in;height:2.40833in" />  

This takes you to `generic.xaml`  
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image9.png" style="width:6.45833in;height:1.75in" />  

Searching for these fonts takes you to [Microsoft Docs](https://docs.microsoft.com/en-us/windows/apps/design/style/segoe-fluent-icons-font) with other icons and descriptions. The one we want is the X which has a Unicode point of `e711`.

`Styles.xaml`  
Change the `Glyph`, which currently uses Unicode point `E001` to `E711`:
<img src="XAML_Control-Templates_Create-a-ControlTemplate-image10.png" style="width:5.625in;height:2.31667in" />





