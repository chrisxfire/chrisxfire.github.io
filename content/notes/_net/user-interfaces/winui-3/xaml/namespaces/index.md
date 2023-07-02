---
title: notes > .net > user interfaces > winui 3 > xaml > namespaces
date: 2022-12-12T16:30:39-0700
draft: false
---

```xml
<!-- x:Class maps to `Microsoft.UI.Xaml`, `.Controls`, `.Data`, `.Input`, `.Shapes` -->
<!-- xmlns — This is the *default* namespace because it does not have a prefix -->
<!-- xmlns:x — Defines attributes for the XAML language, like the `x:Name` attribute -->
<!-- xmlns:d — Designer namespace that defines properties like DesignWidth, DesignHeight; since
XAML does not have a designer, this namespace is not needed -->
<!-- xmlns:mc — The markup compatibility namespace defines the Ignorable attribute -->
<!-- xmlns:controls — This is the namespace we created for UserControls -->
<!-- mc:Ignorable — The Ignorable attribute ignores a namespace at runtime -->
<Window
    x:Class="WiredBrainCoffee.CustomersApp.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:controls="using:WiredBrainCoffee.CustomersApp.Controls"
    mc:Ignorable="d">
```