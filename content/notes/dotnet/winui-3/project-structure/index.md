---
title: notes > dotnet > winui 3 > project structure
date: 2023-01-02T16:54:04-0700
draft: true
---
# App Class
- The `App` class is the app's entry point
- Defined in <u>App.xaml</u> and <u>App.xaml.cs</u>
- Derives from `Microsoft.UI.Xaml.Application`
- `InitializeComponent` method parses contents of <u>App.xaml</u>
- `OnLaunched` method is invoked when app is launched creates and activates a new instance of `MainWindow`

<u>App.xaml</u>
<Application
x:Class="LuckyNumbers.App"
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:local="using:LuckyNumbers">
<Application.Resources>
<ResourceDictionary>
<ResourceDictionary.MergedDictionaries>
<XamlControlsResources xmlns="using:Microsoft.UI.Xaml.Controls" />
<!-- Other merged dictionaries here -->
</ResourceDictionary.MergedDictionaries>
<!-- Other app resources here -->
</ResourceDictionary>
</Application.Resources>
</Application>

<u>App.xaml.cs</u>
public partial class App : Application
{
public App()
{
this.InitializeComponent();
}

/// <param name="args">Details about the launch request and process.</param>
protected override void OnLaunched(Microsoft.UI.Xaml.LaunchActivatedEventArgs args)
{
m_window = new MainWindow();
m_window.Activate();
}

private Window m_window;
}

# MainWindow Class
- `MainWindow` class is the main window of the application
- Defined in <u>MainWindow.xaml</u> and <u>MainWindow.xaml.cs</u>
- Constructor calls its own `InitializeComponent` method to parse MainWindow.xaml into a graph of UI objects

<u>MainWindow.xaml</u>
<Window
x:Class="LuckyNumbers.MainWindow" <!-- The fully-qualified class name. -->
xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:local="using:LuckyNumbers"
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d">

<StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center">
<Button x:Name="myButton" <!-- This element needs a name in order to be referenced in the code-behind file -->
Click="MyButton_Click">Click Me</Button>
</StackPanel>
</Window>

<u>MainWindow.xaml.cs</u>
public sealed partial class MainWindow : Window
{
public MainWindow()
{
this.InitializeComponent();
// Set the title bar:
this.Title = "Title text";
}

private void MyButton_Click(object sender, RoutedEventArgs e)
{
myButton.Content = "Clicked";
}
}

