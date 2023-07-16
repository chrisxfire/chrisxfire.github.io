---
title: notes > code > .net > user interfaces > winui 3 > xaml > resources
date: 2022-12-28T19:51:32-0700
draft: false
weight: 1
---
# Overview
Every element in XAML has a RequestedTheme property that can be set to either "Dark" or "Light". If the element is not set, it defaults to whatever Windows is currently using.

# Defining and Using Theme Resources
`App.xaml`
```xml
<Application RequestedTheme="Dark">
```

`MainWindow.xaml`
<!-- ... -->
<!-- Resources that end in "*ThemeBrush*" are theme-specific resources.
A StaticResource markup extension would load this brush only once. Instead, use the ThemeResource markup extension: -->
```xml
<Grid RequestedTheme="" x:Name="root" Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    …
    <!-- Header -->
    <controls:HeaderControl Grid.ColumnSpan="3"/>
    <!-- Add a button to toggle between light/dark theme. This button will be installed on the HeaderControl -->
    <Button Grid.ColumnSpan="3" HorizontalAlignment="Right" VerticalAlignment="Top"
        Content="Toggle theme" Margin="10"
        Click="ButtonToggleTheme_Click" />
    …
    <!-- Customer list -->
    <!-- Change the theme of the customer list grid.
    This grid and its children will use Dark theme regardless of theme of parent element of the grid: -->
    <Grid Grid.Row="1" x:Name="customerListGrid Background="333333"
        RequestedTheme="Dark"
        Width="250">
    …
…
```

`MainWindow.xaml.cs`
In the code-behind, set the RequestedTheme property of the root Grid to either ElementTheme.Dark or Light whenever the Button is clicked:
```cs
// …
private void ButtonToggleTheme_Click(object sender, RoutedEventArgs e)
{
    root.RequestedTheme = root.RequestedTheme == ElementTheme.Light
    ? ElementTheme.Dark
    : ElementTheme.Light;
}
// …
```

# Creating Custom Theme Resources
The background of the Navigation does not change to a light background because it is hard-coded to dark grey.

Add the `SolidColorBrush` that is used on the Navigation to the application-wide resources in the `ThemeDictionaries`:
`App.xaml`
```xml
…
</ResourceDictionary.MergedDictionaries>
<ResourceDictionary.ThemeDictionaries>
    <!-- Create a new ResourceDictionary: -->
    <ResourceDictionary x:Key="Dark">
        <SolidColorBrush x:Key="NavigationBackgroundBrush" Color="#333333"/>
    </ResourceDictionary>
    <ResourceDictionary x:Key="Light">
        <SolidColorBrush x:Key="NavigationBackgroundBrush" Color="#BBBBBB"/>
    </ResourceDictionary>
</ResourceDictionary.ThemeDictionaries>
…
```

`MainWindow.xaml`
```xml
<!-- Customer list -->
<!-- Change the background of the customerListGrid to use the newly-created custom theme resource: -->
<Grid Grid.Row="1" x:Name="customerListGrid"
    Background="{ThemeResource NavigationBackgroundBrush}"
    Width="250">
```
