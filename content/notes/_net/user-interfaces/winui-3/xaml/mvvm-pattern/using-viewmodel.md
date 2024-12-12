---
title: using viewmodel
date: 2022-12-12T20:58:19-0700
draft: false
weight: 1
---

# Using ViewModel for the MainWindow
`MainWindow.xaml`
```xml
<!-- Set a name on the grid so we can reference it in the code-behind: -->
<Window … <Grid Background="#222222" x:Name="root">
```

`MainWindow.xaml.cs`
```cs
public sealed partial class MainWindow : Window
{
    public MainViewModel ViewModel { get; }

    public MainWindow()
    {
        this.InitializeComponent();
        Title = "Customers App";
        ViewModel = new MainViewModel(new CustomerDataProvider());

        root.DataContext = ViewModel; // <— Assign the ViewModel to the DataContext

        root.Loaded += Root_Loaded; // <— Load the data of the ViewModel when the View gets loaded:
    }

    // This event handler gets called when root Grid is loaded:
    private async void Root_Loaded(object sender, RoutedEventArgs e)
    {
        await ViewModel.LoadAsync();
    }
    // …
}
```

`MainWindow.xaml`
```xml
<!-- Used to assign a collection of data to the ListView.
     If the Path property is the first property set on the binding markup extension, it can be omitted:
-->
<ListView Grid.Row="1" x:Name="customerListView"
    ItemsSource="{Binding Path=Customers, Mode=OneWay}"
    ItemsSource="{Binding Customers, Mode=OneWay}"
    DisplayMemberPath="FirstName"
    ScrollViewer.HorizontalScrollMode="Enabled"
    ScrollViewer.HorizontalScrollBarVisibility="Auto"/>
    <!-- Customer detail -->
    <!-- Access the FirstName property of the Customer object to display it when it is selected: -->
    <StackPanel Grid.Row="1" Grid.Column="1" Margin="10">
        <TextBox Header="Firstname" Text="{Binding ElementName=customerListView,
            Path=SelectedItem.FirstName, Mode=TwoWay}"/>
        <TextBox Header="Lastname" Margin="0 10 0 0"/>
        <CheckBox Margin="0 20 0 0">
            Is developer
        </CheckBox>
    </StackPanel>
```
