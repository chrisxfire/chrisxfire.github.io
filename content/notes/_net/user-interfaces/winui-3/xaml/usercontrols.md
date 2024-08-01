---
title: usercontrols
date: 2022-12-12T13:39:26-0700
draft: false
weight: 1
---
# UserControls
UserControls compartmentalize XAML.

# Creating
New folder > "Controls" > New item > WinUI > User Control (WinUI 3) > "HeaderControl"

`HeaderControl.xaml`
```xml
<!-- Create a UserControl tag to hold the control: -->
<UserControl
    x:Class="WiredBrainCoffee.CustomersApp.Controls.HeaderControl"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WiredBrainCoffee.CustomersApp.Controls"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">
    <Grid Background="#F05A28">
        <StackPanel HorizontalAlignment="Center" Orientation="Horizontal">
            <Image Source="/Images/logo.png" Width="100" Margin="5"/>
            <TextBlock Text="Customers App" FontSize="30"
                VerticalAlignment="Center"
                Foreground="White"/>
            <TextBlock Text="Version 1.0" FontSize="16"
                VerticalAlignment="Bottom"
                Margin="10 0 0 22"
                Foreground="#333333"/>
        </StackPanel>
    </Grid>
</UserControl>
```

`HeaderControl.xaml.cs` code-behind:
```cs
namespace WiredBrainCoffee.CustomersApp.Controls
{
    public sealed partial class HeaderControl : UserControl // Note that inheritance from UserControl
    {
        public HeaderControl()
        {
            this.InitializeComponent();
        }
    }
}
```

`MainWindow.xaml`
```xml
<Window
    …
    xmlns:controls="using:WiredBrainCoffee.CustomersApp.Controls"
    …
    <!-- Header -->
    <controls:HeaderControl Grid.ColumnSpan="3"/>
```
