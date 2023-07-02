---
title: notes > .net > user interfaces > winui 3 > controls
date: 2023-01-05T19:25:29-0700
draft: false
---
# Overview
*Control* — a UI element that displays content or enables interaction.

[Alphabetical Index of Controls](https://learn.microsoft.com/en-us/windows/apps/design/controls/#alphabetical-index)

## 3 Steps to Using Controls
1.  Add a control to the UI
2.  Set properties on the control
3.  Add code to the control's event handlers

# Add a Control
Use Blend for Visual Studio or Visual Studio XAML Designer or add the control via code.
- Note: controls added via code are not visible in XAML Designer.

# Set the Control's Name and Properties
Set the control's `x:Name` attribute:

```xml
<Button x:Name="Button1" Content="Button"/>
```

Properties can be set in the properties window:  
<img src="Controls-image1.png" style="width:3.25833in;height:1.80833in" alt="Intellisense in XAML part 1" />  

Or in XAML:
```xml
<Button x:Name="Button1" Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Foreground="Beige"/>
```
Or in code:
```cs
Button1.Foreground = new SolidColorBrush(Windows.UI.Colors.Beige);
```

# Create an Event Handler
Select the control and then click the Events tab at the top of the Properties window:  
<img src="Controls-image2.png" style="width:3.54167in;height:1.35in" />  

Or in code:
```cs
private void Button_Click(object sender, RoutedEventArgs e)
{
    Button b = (Button)sender;
    b.Foreground = new SolidColorBrush(Windows.UI.Colors.Blue);
}
```
Or in XAML — then, double-click `<New Event Handler>`:  
<img src="Controls-image3.png" style="width:4.2in;height:1.20833in" alt="Intellisense for the click event" />

Associate an event with its event handler in code:
```cs
Button1.Click += new RoutedEventHandler(Button_Click);
```
