---
title: notes > .net > winui 3 > xaml > data templates > applying
date: 2022-12-28T20:58:21-0700
draft: false
---
# Data Templates
Use a Data Template for the `ListView` in the Navigation so that you can see the first AND last name of the customers.

# Defining a Data Template
`MainWindow.xaml`
```xml
<!-- ... -->
    <ListView Grid.Row="1"
        ItemsSource="{x:Bind ViewModel.Customers, Mode=OneWay}"
        SelectedItem="{x:Bind ViewModel.SelectedCustomer, Mode=TwoWay}"
        DisplayMemberPath="FirstName"
        ScrollViewer.HorizontalScollMode="Enabled"
        ScrollVIewer.HorizontalScrollBarVisibility="Auto"/>
        <!-- Set the ListView's ItemTemplate property: -->
        <ListView.ItemTemplate>
        <!-- Use any UI element inside this DataTemplate: -->
            <DataTemplate>
                <StackPanel Orientation="Horizontal">
                    <!-- Bind to the DataContext: -->
                    <TextBlock Text="{Binding FirstName, Mode=OneWay}" FontWeight="Bold"/>
                    <TextBlock Text="{Binding LastName, Mode=OneWay}" Margin="5 0 0 0"/>
                </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</Grid>
```

You now have a single item of the `ViewModel.Customers` property (which contains a collection of `CustomerItem` `ViewModels)` in the `DataContext` of the `DataTemplate`.

# Defining a Data Template as a Resource
Instead of defining the `DataTemplate` directly on the `ListView`, you can create it as a resource:

`MainWindow.xaml`
```xml
<Window … >
    <Grid x:Name="root" Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.Resources>
        <DataTemplate x:Key="CustomerDataTemplate">
            <StackPanel Orientation="Horizontal">
                <!-- Bind to the DataContext: -->
                <TextBlock Text="{Binding FirstName, Mode=OneWay}" FontWeight="Bold"/>
                <TextBlock Text="{Binding LastName, Mode=OneWay}" Margin="5 0 0 0"/>
            </StackPanel>
        </DataTemplate>
    </Grid.Resources>
    …
    …
    <ListView Grid.Row="1"
        ItemsSource="{x:Bind ViewModel.Customers, Mode=OneWay}"
        SelectedItem="{x:Bind ViewModel.SelectedCustomer, Mode=TwoWay}"
        ItemTemplate="{StaticResource CustomerDataTemplate}"
        ScrollViewer.HorizontalScollMode="Enabled"
        ScrollVIewer.HorizontalScrollBarVisibility="Auto"/>
```

# Use `x:Bind` in a Data Template
`x:Bind` resolves the binding path at compile time instead of runtime. If you specify an invalid binding path, you would know at compile time instead of runtime.  

`x:Bind` needs to know for which type the Data Template will be used:

`MainWindow.xaml`
```xml
<Window>
    <!-- ... -->   
    <!-- Add the customer ViewModel so we can reference it in the x:DataType attribute below: -->
    xmlns:viewModel="using:WiredBrainCoffee.CustomersApp.ViewModel"
    <!-- ... -->
    <!-- Set the x:DataType attribute, telling Xaml that the data type of this DataTemplate is a CustomerItemViewModel: -->
    <DataTemplate x:Key="CustomerDataTemplate"    
        x:DataType="viewModel:CustomerItemViewModel">
        <StackPanel Orientation="Horizontal">
            <!-- Replace the binding with x:Bind -->
            <TextBlock Text="{x:Bind FirstName, Mode=OneWay}" FontWeight="Bold"/>
            <TextBlock Text="{x:Bind LastName, Mode=OneWay}" Margin="5 0 0 0"/>
            <TextBlock Text="(Dev)" Margin="5 0 0 0" Opacity="0.5"
                Visibility="{x:Bind IsDeveloper, Mode=OneWay}"
        </StackPanel>
    </DataTemplate>
    <!-- ... -->
```