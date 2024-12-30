---
title: implementing basic navigation
date: 2023-01-02T17:38:12-0700
draft: false
weight: 1
---

# a textblock
```xml
<TextBlock x:Name="pageTitle" Text="Page 1" />
```

# a hyperlinkbutton
```xml
<HyperlinkButton Content="Click to go to page 2" Click="HyperlinkButton_Click" HorizontalAlignment="Center"/>
```
Code-behind:
```cs
// Handle the Click event of the HyperlinkButton:
private void HyperlinkButton_Click(object sender, RoutedEventArgs e)
{
    this.Frame.Navigate(typeof(Page2));
}
```
