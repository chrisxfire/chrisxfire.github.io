---
title: project structure
date: 2023-01-02T16:54:04-0700
draft: false
weight: 1
---
# App Class
- The `App` class is the app's entry point
- Defined in `App.xaml` and `App.xaml.cs`
- Derives from `Microsoft.UI.Xaml.Application`
- `InitializeComponent` method parses contents of App.xaml
- `OnLaunched` method is invoked when app is launched creates and activates a new instance of `MainWindow`

`App.xaml`
```xml
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
```

`App.xaml.cs`
```cs
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
```

# MainWindow Class
- `MainWindow` class is the main window of the application
- Defined in MainWindow.xaml and MainWindow.xaml.cs
- Constructor calls its own `InitializeComponent` method to parse MainWindow.xaml into a graph of UI objects

`MainWindow.xaml`
```xml
<!-- x:Class is the fully-qualified class name. -->
<Window
    x:Class="LuckyNumbers.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:LuckyNumbers"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <!-- This Button element needs a name in order to be referenced in the code-behind file -->
    <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center">
        <Button x:Name="myButton" Click="MyButton_Click">Click Me</Button>
    </StackPanel>
</Window>
```

`MainWindow.xaml.cs`
```cs
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
```
