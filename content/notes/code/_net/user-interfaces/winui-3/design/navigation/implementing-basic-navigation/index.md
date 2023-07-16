---
title: notes > code > .net > user interfaces > winui 3 > design > navigation > implementing basic navigation
date: 2023-01-02T17:38:12-0700
draft: false
---
# A TextBlock
```xml
<TextBlock x:Name="pageTitle" Text="Page 1" />
```

# A HyperlinkButton
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
