---
title: notes > dotnet > winui 3 > xaml > mvvm pattern > using viewmodel
date: 2022-12-12T20:58:19-0700
draft: true
---
# Using ViewModel for the MainWindow
MainWindow.xaml:
<Window
…
<!-- Set a name on the grid so we can reference it in the code-behind: -->
<Grid Background="#222222" x:Name="root">

MainWindow.xaml.cs:
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

…
}

MainWindow.xaml:
<ListView Grid.Row="1" x:Name="customerListView"
Used to assign a collection of data to the ListView:
`ItemsSource="{Binding Path=Customers, Mode=OneWay}"`
If the Path property is the first property set on the binding markup extension, it can be omitted:
`ItemsSource="{Binding Customers, Mode=OneWay}"`
Specify a property of an object to display:
DisplayMemberPath="FirstName"
ScrollViewer.HorizontalScrollMode="Enabled"
ScrollViewer.HorizontalScrollBarVisibility="Auto"/>
~~<ListViewItem>Julia</ListViewItem>~~
~~<ListViewItem>Alex</ListViewItem>~~
~~<ListViewItem>Thomas</ListViewItem>~~
~~</ListView>~~
<!-- Customer detail -->
<StackPanel Grid.Row="1" Grid.Column="1" Margin="10">
<TextBox Header="Firstname" Text="{Binding ElementName=customerListView,
<!-- Access the FirstName property of the Customer object to display it when it is selected: -->
Path=`SelectedItem.FirstName, Mode=TwoWay}`"/>
<TextBox Header="Lastname" Margin="0 10 0 0"/>
<CheckBox Margin="0 20 0 0">
Is developer
</CheckBox>
</StackPanel>
# 
