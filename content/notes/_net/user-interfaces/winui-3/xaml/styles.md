---
title: styles
date: 2022-12-31T09:16:27-0700
draft: false
weight: 1
---
# Overview
Styles allow you to apply the same property values to multiple elements in XAML.

# Benefits of Styles
Styles allow you to apply common style property values to multiple controls without having to define them on each control individually.

# Creating Styles
Styles can be created in the Resources property of the parent element of the elements being styled:

`MainWindow.xaml`
```xml
<!-- ... -->
<!-- Customer detail -->
<StackPanel Grid.Row="1" Grid.Column="1" Margin="10"
Visibility="{x:Bind ViewModel.IsCustomerSelected, Mode=OneWay}">
<StackPanel.Resources>
    <!-- The TextBox TargetType defines this style as a style for TextBox elements -->
    <Style x:Key="TextBoxStyle" TargetType="TextBox">
    <!-- The Setters property is defined on the Style class as a ContentProperty making this element optional: -->
    <Style.Setters>
    <Setter Property="Padding" Value="8"/>
    <Setter Property="CornerRadius" Value="8"/>
    <Setter Property="PlaceholderForeground" Value="LightCoral"/>
    </Style.Setters>
    </Style>
</StackPanel.Resources>
<!-- ... -->
<TextBox Header="Firstname" Text="{x:Bind ViewModel.SelectedCustomer.FirstName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}" Style="{StaticResource TextBoxStyle}" PlaceholderText="Firstname"/>
<TextBox Header="Lastname" Margin="0 10 0 0"
    Text="{x:Bind ViewModel.SelectedCustomer.LastName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"
    Style="{StaticResource TextBoxStyle}"
    PlaceholderText="Firstname"/>
<!-- ... -->
```

# Inherit a Style from Another Style
`MainWindow.xaml`
```xml
<StackPanel.Resources>
    <Style x:Key="TextBoxBaseStyle" TargetType="TextBox">
        <Setter Property="Padding" Value="8"/>
    </Style>
    <Style x:Key="TextBoxStyle" TargetType="TextBox" BasedOn="{StaticResource} TextBoxBaseStyle}">
        <Style.Setters>
            <!-- <Setter Property="Padding" Value="8"/> -->
            <Setter Property="CornerRadius" Value="8"/>
            <Setter Property="PlaceholderForeground" Value="LightCoral"/>
        </Style.Setters>
    </Style>
</StackPanel.Resources>
```

# Explicit and Implicit Styles
Explicit styles are referenced via the StaticResource markup extension.

`MainWindow.xaml`
```xml
<StackPanel.Resources>
    <Style x:Key="TextBoxBaseStyle" TargetType="TextBox">
        <Setter Property="Padding" Value="8"/>
    </Style>
    <!-- Implicit styles are created by omitting the x:Key attribute. The Style is added to the StackPanel. -->
    <Style>
        <Style.Setters>
        <Setter Property="CornerRadius" Value="8"/>
        <Setter Property="PlaceholderForeground" Value="LightCoral"/>
        </Style.Setters>
    </Style>
</StackPanel.Resources>
<!-- ... -->

<!-- You can then remove the Style properties from the TextBox's: -->
<TextBox Header="Firstname" 
    Text="{x:Bind ViewModel.SelectedCustomer.FirstName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}" 
    PlaceholderText="Firstname"/>
<TextBox Header="Lastname" Margin="0 10 0 0"
    Text="{x:Bind ViewModel.SelectedCustomer.LastName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"
    PlaceholderText="Firstname"/>
```

# Define an Application-wide TextBox Style
**Resources** > **New item** > *WinUI* > **Resource Dictionary** > "Styles.xaml"

`Styles.xaml`
```xml
<ResourceDictionary>
    <Style x:Key="TextBoxBaseStyle" TargetType="TextBox">
        <Setter Property="Padding" Value="8"/>
    </Style>
    <Style TargetType="TextBox" BasedOn="{StaticResource} TextBoxBaseStyle}">
        <Style.Setters>
        <Setter Property="CornerRadius" Value="8"/>
        <!-- You can reference resources from other ResourceDictionary's that are part of the MergedDictionaries.  This HeaderBackgroundBrush is from Brushes.xaml: -->
        <Setter Property="PlaceholderForeground"
        Value="{StaticResource HeaderBackgroundBrush}"/>
        </Style.Setters>
    </Style>
</ResourceDictionary>
```

`App.xaml`
```xml
<!-- ... -->
<ResourceDictionary.MergedDictionaries>
    <XamlControlResources xmlns="using:Microsoft.UI.Xaml.Controls" />
    <ResourceDictionary Source="/Resources/Brushes.xaml"/>
    <!-- Add the newly-created Styles.xaml to the MergedDictionaries: -->
    <ResourceDictionary Source="/Resources/Styles.xaml"/>
</ResourceDictionary.MergedDictionaries>
<!-- ... -->
```

# Styling Controls
- `CornerRadius` — rounds the corners of the control
- `Padding` — 
- `PlaceholderForground` — color of the PlaceholderText
- `PlaceholderText` — for TextBox
