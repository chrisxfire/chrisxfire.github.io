---
title: notes > code > .net > user interfaces > winui 3 > xaml > building a layout
date: 2022-12-11T18:27:01-0700
draft: false
---

`MainWindow.xaml`
```xml
<Window
    x:Class="WiredBrainCoffee.CustomersApp.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WiredBrainCoffee.CustomersApp"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">
    <!-- A `Grid` with two columns and three rows: -->
    <Grid Background="#222222">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto"/>
            <ColumnDefinition Width="*"/>
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <!-- For the header: -->
            <RowDefinition Height="Auto"/>
            <!-- For Navigation and Customer Details -->
            <RowDefinition Height="*"/>
            <!-- For the border element: -->
            <RowDefinition Height="Auto"/>
        </Grid.RowDefinitions>

        <!-- Header: a horizontal `StackPanel` with an image and two TextBlocks: ---->
        <!-- This grid defines the background: -->
        <Grid Grid.ColumnSpan="3" Background="#F05A28">
            <StackPanel Orientation="Horizontal" HorizontalAlignment="Center">
                <!-- Images/logo.png needs a Build Action of Content -->
                <Image Source="/Images/logo.png" Width="100" Margin="5"/>
                <TextBlock Text="Customers App" FontSize="30" 
                    Foreground="White" VerticalAlignment="Center"/>
                <TextBlock Text="Version 1.0" FontSize="16"
                    Foreground="#333333" VerticalAlignment="Bottom" Margin="10 0 0 22"/>
            </StackPanel>
        </Grid>

        <!-- Customer list: originally, a horizontal `StackPanel` with 3 `Buttons` and a `ListView` with 3 items: --->
        <!-- Instead of a `StackPanel`, use a `Grid` in order to get the `ListViewItems` to display a scroll bar when the window shrinks -->
        <Grid Grid.Row="1" x:Name="customerListGrid"
            Grid.Column="2"
            Background="#333333"
            Width="250">
            <Grid.RowDefinitions>
            <!-- This row definition contains the StackPanel: -->
            <RowDefinition Height="Auto"/>
            <!-- This row definition contains the ListView: -->
            <RowDefinition /> <!-- We omit the Height property because we want Height="*", which is the default -->
            <StackPanel Orientation="Horizontal">
                <Button Margin="10">
                    <StackPanel Orientation="Horizontal">
                        <SymbolIcon Symbol="AddFriend"/>
                        <TextBlock Text="Add" Margin="5 0 0 0"/>
                    </StackPanel>
                </Button>
                <Button Margin="0 10 10 10">
                    <StackPanel Orientation="Horizontal">
                        <SymbolIcon Symbol="Delete"/>
                        <TextBlock Text="Delete" Margin="5 0 0 0"/>
                    </StackPanel>
                </Button>
                <Button Margin="0 10 10 10" Click="ButtonMoveNavigation_Click">
                    <SymbolIcon Symbol="Forward" x:Name="symbolIconMoveNavigation"/>
                </Button>
            </StackPanel>
            <ListView Grid.Row="1"
                ScrollViewer.HorizontalScollMode="Enabled"
                ScrollViewer.HorizontalScrollBarVisibility="Auto"> <!-- Display the horizontal scroll bar when needed. -->
                <ListViewItem>Julia</ListViewItem>
                <ListViewItem>Alex</ListViewItem>
                <ListViewItem>Thomas</ListViewItem>
            </ListView>
        </Grid>

        <!-- Customer detail: a StackPanel with two TextBoxes and a CheckBox: -->
        <StackPanel Grid.Row="1" Grid.Column="1" Margin="10">
            <TextBox Header="Firstname"/>
            <TextBox Header="Lastname" Margin="0 10 0 0"/>
            <CheckBox Margin="0 20 0 0">
                Is developer
            </CheckBox>
        </StackPanel>

        <!-- Statusbar: a TextBlock: --->
        <!-- Sets this border in the 3rd row of the grid: -->
        <Border Grid.Row="2" Grid.ColumnSpan="3" Background="#444">
            <TextBlock Text=" (c) Wired Brain Coffee" Foreground="White" Margin="5"/>
        </Border>
    </Grid>
    <!-- These elements are all drawn on top of each other -->
</Window>
```

`MainWindow.xaml.cs`
```cs
public sealed partial class MainWindow : Window
{
    public MainWindow()
    {
        this.InitializeComponent();
        Title = "Customers App";
    }

    // Allows the navigation to be moved from one side of the application to the other:
    private void ButtonMoveNavigation_Click(object sender, RoutedEventArgs e)
    {
        // GetValue returns an object, but Grid.ColumnProperty is of type int, so this can be cast:
        var column = (int)customerListGrid.GetValue(Grid.ColumnProperty);
        // OR:
        var column = Grid.GetColumn(customerListGrid);

        var newColumn = column == 0 ? 2 : 0; // If the column is currently at 0, set it to 2; otherwise, leave at 0

        customerListGrid.SetValue(Grid.ColumnProperty, newColumn);
        // OR:
        Grid.SetColumn(customerListGrid, newColumn);

        symbolIconMoveNavigation.Symbol = newColumn == 0 ? Symbol.Forward : Symbol.Back;
    }
}
```
