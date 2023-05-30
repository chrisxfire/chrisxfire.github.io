---
title: "notes > dotnet > winui 3 > xaml > namespaces"
date: 2022-12-12T16:30:39-0700
draft: true
---
<Window
x:Class="WiredBrainCoffee.CustomersApp.MainWindow"
Maps to `Microsoft.UI.Xaml`, `.Controls`, `.Data`, `.Input`, `.Shapes`
This is the *default* namespace because it does not have a prefix:
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
Defines attributes for the XAML language, like the `x:Name` attribute:
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
Designer namespace that defines properties like DesignWidth, DesignHeight; since
XAML does not have a designer, this namespace is not needed:
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
The markup compatibility namespace defines the Ignorable attribute
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
This is the namespace we created for UserControls:
xmlns:controls="using:WiredBrainCoffee.CustomersApp.Controls"
The Ignorable attribute ignores a namespace at runtime:
mc:Ignorable="d">