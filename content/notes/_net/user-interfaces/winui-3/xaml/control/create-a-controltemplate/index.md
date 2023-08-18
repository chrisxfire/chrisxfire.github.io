---
title: create a controltemplate
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
<img alt="A screenshot of generic.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image1.png" width="50%" height="50%" />  
Copy the above Style.  

`Resources/Styles.xaml`  
Paste the style for the `CheckBox` copied from `generic.xaml`:

<img alt="A screenshot of Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image2.png" width="50%" height="50%" />  

The `CheckBox` is actually a `Grid`:  
<img alt="A screenshot of the BootGrid in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image3.png" width="50%" height="50%" />  

The `VisualStateGroups` define the UI of the `CheckBox` based on its state. For example, if the `CheckBox` is unchecked, then `UncheckedNormal` is active:  
<img alt="A screenshot of the VisualStateGroups in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image4.png" width="50%" height="50%" />  

The `CheckBox` (`Grid`) contains two column definitions:  
<img alt="A screenshot of the column definitions in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image5.png" width="50%" height="50%" />  

The first `ColumnDefinition` has a `Rectangle` and a `FontIcon` which is actually the checkmark (defined in its `Glyph` property):  
<img alt="A screenshot of the first ColumnDefinition in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image6.png" width="50%" height="50%" />  

This `ContentPresenter` displays the `Content` of the `CheckBox`:  
<img alt="A screenshot of the ContentPresenter in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image7.png" width="50%" height="50%" />  

To change the checkmark, go to the **FontIcon** > right-click **SymbolThemeFontFamily** > **Go to definition**:  
<img alt="A screenshot of the FontIcon property in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image8.png" width="50%" height="50%" />  

This takes you to `generic.xaml`  
<img alt="A screenshot of the FontIcon property in generic.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image9.png" width="50%" height="50%" />  

Searching for these fonts takes you to [Microsoft Docs](https://docs.microsoft.com/en-us/windows/apps/design/style/segoe-fluent-icons-font) with other icons and descriptions. The one we want is the X which has a Unicode point of `e711`.

`Styles.xaml`  
Change the `Glyph`, which currently uses Unicode point `E001` to `E711`:
<img alt="A screenshot of the Glyph in Styles.xaml" src="XAML_Control-Templates_Create-a-ControlTemplate-image10.png" width="50%" height="50%" />





