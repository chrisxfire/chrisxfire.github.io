---
title: notes > code > .net > user interfaces > winui 3 > xaml > mvvm pattern > x bind vs binding
date: 2022-12-18T19:13:17-0700
draft: false
weight: 1
---
# Overview
Prefer `x:Bind` over `Binding` whenever possible.

# Binding
```xml
<TextBlock Text={"Binding Path=…}"/>
```
- Resolves binding path at *runtime*

## Data Sources
- `ElementName`, `Source`, or `RelativeSource`
- Uses `DataContext` if none of the above are set

# x:Bind
```xml
<TextBlock Text={"x:Bind Path=…}"/>
```
- Resolves binding path a *compile time*
- Creates C# code behind the scenes

## Data Sources
- Does not use data sources.
- Uses Root object of XAML document (an instance of the class that is specified with the x:Class attribute)

# Advantages of x:Bind
- Better performance
- Compile-time errors
- Better debugging experience (ability to step into genereated data binding code)

# Example with x:Bind
`MainWindow.xaml.cs`
```cs
public sealed partial class MainWindow : Window
{
    public MainViewModel ViewMode { get; }

    public MainWindow()
    {
        this.InitializeComponent();

        Title = "Customers App";
        // Set the ViewModel property to the MainViewModel:
        ViewModel = new MainViewModel(new CustomerDataProvider());
        // Not needed when using x:Bind:
        // root.DataContext = ViewModel;
        root.Loaded += Root_Loaded;
    }
}
```

`MainWindow.xaml`
```xml
<!-- Change from Binding to x:Bind: -->
<ListView Grid.Row="1" x:Name="customerListView"
    ItemsSource="{x:Bind ViewModel.Customers,Mode=OneWay}"
    SelectedItem="{x:Bind ViewModel.SelectedCustomer,Mode=TwoWay}"
    DisplayMemberPath="FirstName"
    ScrollViewer.HorizontalScrollMode="Enabled"
    ScrollViewer.HorizontalScrollBarVisibility="Auto"/>

    <!-- Customer detail --->
    <StackPanel Grid.Row="1" Grid.Column="1" Margin="10">
        <TextBox Header="Firstname" 
            Text="{x:Bind ViewModel.SelectedCustomer.FirstName, Mode=TwoWay UpdateSourceTrigger=PropertyChanged}"/>
        <TextBox Header="Lastname"
            Text="{x:Bind ViewModel.SelectedCustomer.LastName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}",
            Margin="0 10 0 0"/>
        <CheckBox Margin="0 20 0 0"
            IsChecked="{x:Bind ViewModel.SelectedCustomer.IsDeveloper, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}">
            Is developer
        </CheckBox>
    </StackPanel>
```
