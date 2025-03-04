---
title: controls
date: 2023-01-05T19:25:29-0700
draft: false
weight: 1
---

# overview
*Control* — a UI element that displays content or enables interaction.

[Alphabetical Index of Controls](https://learn.microsoft.com/en-us/windows/apps/design/controls/#alphabetical-index)

## 3 steps to using controls
1.  Add a control to the UI
2.  Set properties on the control
3.  Add code to the control's event handlers

# add a control
Use Blend for Visual Studio or Visual Studio XAML Designer or add the control via code.
- Note: controls added via code are not visible in XAML Designer.

# Set the Control's Name and Properties
Set the control's `x:Name` attribute:

```xml
<Button x:Name="Button1" Content="Button"/>
```

Properties can be set in the properties window:  
![Intellisense in XAML part 1](./Controls-image1.png)

Or in XAML:
```xml
<Button x:Name="Button1" Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Foreground="Beige"/>
```
Or in code:
```cs
Button1.Foreground = new SolidColorBrush(Windows.UI.Colors.Beige);
```

# create an event handler
Select the control and then click the Events tab at the top of the Properties window:  
![](./Controls-image2.png)

Or in code:
```cs
private void Button_Click(object sender, RoutedEventArgs e)
{
    Button b = (Button)sender;
    b.Foreground = new SolidColorBrush(Windows.UI.Colors.Blue);
}
```
Or in XAML — then, double-click `<New Event Handler>`:  
![Intellisense for the click event](./Controls-image3.png)

Associate an event with its event handler in code:
```cs
Button1.Click += new RoutedEventHandler(Button_Click);
```
