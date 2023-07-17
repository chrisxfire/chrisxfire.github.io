---
title: notes > code > .net > user interfaces > winui 3 > xaml > mvvm pattern > create another viewmodel
date: 2022-12-14T19:21:02-0700
draft: false
weight: 1
---
# Create a ViewModel for a Customer
`CustomerItemViewModel.cs`
```cs
public class CustomerItemViewModel : ViewModelBase
{
    private readonly Customer _model;

    public CustomerItemViewModel(Customer model)
    {
        _model = model;
    }

    public int Id => _model.Id;
    public string? FirstName
    {
        get => _model.Firstname
        set
        {
            if (_model.Firstname != value)
            {
                _model.Firstname = value;
                RaisePropertyChanged();
            }
        }
    }

    public string? LastName
    {
        get => _model.Lastname
        set
        {
            if (_model.Lastname!= value)
            {
                _model.Lastname= value;
                RaisePropertyChanged();
            }
        }
    }

    public bool IsDeveloper
    {
        get => _model.IsDeveloper;
        set
        {
            if (_model.IsDeveloper != value)
            {
                _model.IsDeveloper = value;
                RaisePropertyChanged();
            }
        }
    }
}
```

`MainViewModel.cs`
```cs
public class MainViewModel : INotifyPropertyChanged
{
    private readonly ICustomerDataProvider _customerDataProvider;
    // Change the type: Customer —> CustomerItemViewModel:
    private CustomerItemViewModel? _selectedCustomer;

    public MainViewModel(ICustomerDataProvider customerDataProvider) { … }

    // Change the type: Customer —> CustomerItemViewModel:
    public ObservableCollection<CustomerItemViewModel> Customers { get; } = new();

    // Change the type: Customer —> CustomerItemViewModel:
    public CustomerItemViewModel? SelectedCustomer { … }

    public event PropertyChangedEventHandler? PropertyChanged;

    public Task LoadAsync()
    {
    // …

        if (customers is not null)
            foreach (var customer in customers)
                // Add a CustomerItemViewModel instead of a Customer:
                Customers.Add(new CustomerItemViewModel(customer));
    }
    // …
}
```

`MainWindow.xaml`
```xml
<ListView Grid.Row="1" x:Name="customerListView"
    ItemsSource="{Binding Customers, Mode=OneWay}"
    SelectedItem="{Binding SelectedCustomer, Mode=TwoWay}"
    DisplayMemberPath="FirstName"
    ScrollViewer.HorizontalScrollMode="Enabled"
    ScrollViewer.HorizontalScrollBarVisibility="Auto"/>

    <!-- Customer detail --->
    <StackPanel Grid.Row="1" Grid.Column="1" Margin="10">
        <!-- The UpdateSourceTrigger property defines when source property should be updated with value of the target property.
        Default is LostFocus; when navigation changes, value of Text property is written into the Firstname property.
        Change this to PropertyChanged: -->
        <TextBox Header="Firstname" Text="{Binding SelectedCustomer.FirstName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"/>
        <!-- Do the same for Lastname: -->
        <TextBox Header="Lastname" Text="{Binding SelectedCustomer.LastName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}", Margin="0 10 0 0"/>
        <!-- And for the "Is developer" checkbox: -->
        <CheckBox Margin="0 20 0 0
            IsChecked="{Binding SelectedCustomer.IsDeveloper, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}">
                Is developer
        </CheckBox>
    </StackPanel>
```
