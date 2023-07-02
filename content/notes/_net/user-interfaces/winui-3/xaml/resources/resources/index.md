---
title: notes > .net > user interfaces > winui 3 > xaml > resources > resources
date: 2022-12-28T19:11:14-0700
draft: false
---
# Overview
In XAML, every element has a `Resources` property of type `ResourceDictionary`.

`HeaderControl.xaml`
```xml
<!-- ... -->
<!-- Instead of hard-coding this value, it can be stored in a resource: -->
<Grid Background ="F05A28">
<!-- ... -->
```
# Defining Resources
Application-wide resources are stored in App.xaml:
`App.xaml`
```xml
<!-- ... -->
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <XamlControlResources xmlns="using:Microsoft.UI.Xaml.Controls" />
            <!-- Other merged dictionaries here -->
        </ResourceDictionary.MergedDictionaries>
        <!-- Other app resources here -->
        <!-- Since the Resources property is a ResourceDictionary, it needs a Key and a Value.
        The key is defined using x:Key: -->
        <SolidColorBrush x:Key="HeaderBackgroundBrush" Color="F05A28"/>
        <SolidColorBrush x:Key="HeaderForegroundBrush" Color="White"/>
    </ResourceDictionary>
</Application.Resources>
<!-- ... -->
```

If we wanted to put the Resources in HeaderControl.xaml instead of App.xaml, we could put them inside a `<UserControl.Resources>` tag.

# Using Resources
`HeaderControl.xaml`
```xml
    <!-- Use the StaticResource markup extension: -->
    <Grid Background="{StaticResource HeaderBackgroundBrush}">
        <!-- ... -->
    <!-- ... -->
    <TextBlock Text="Customers App" FontSize="30" VerticalAlignment="Center"
    Foreground="{StaticResource HeaderForegroundBrush}">
        <!-- ... -->
    <!-- ... -->
<!-- ... -->
```
# Resources in a Window
`MainWindow.xaml`
A `Window` does not have a `Resources` property. Instead of defining resources on a `Window`, use the `Resources` property of the root `Grid` instead.

# Defining Resources in a Dedicated Resources File
Visual Studio: right-click Project > **Add** > **New Folder** > "Resources"
right-click **Resources** > **New Item** > *WinUI* > **Resource Dictionary** > "Brushes.xaml"

`Brushes.xaml`
```xml
<ResourceDictionary
    xmlns="<!-- ... -->"
    xmlns:x="<!-- ... -->">
    <SolidColorBrush x:Key="HeaderBackgroundBrush" Color="F05A28"/>
    <SolidColorBrush x:Key="HeaderForegroundBrush" Color="White"/>
</ResourceDictionary>
```

`App.xaml`
```xml
<!-- ... -->
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <XamlControlResources xmlns="using:Microsoft.UI.Xaml.Controls" />
            <!-- Other merged dictionaries here -->
            <ResourceDictionary Source="/Resources/Brushes.xaml" />
        </ResourceDictionary.MergedDictionaries>
        <!-- Other app resources here -->
    </ResourceDictionary>
</Application.Resources>
<!-- ... -->
```