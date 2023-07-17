---
title: notes > .net > user interfaces > winui 3 > xaml > mvvm pattern > binding visibility with x bind
date: 2022-12-18T19:48:32-0700
draft: false
weight: 1
---
# Bind the Visibility property with x:Bind
`MainViewModel.cs`
```cs
public class MainViewModel : INotifyPropertyChanged
{
    private readonly ICustomerDataProvider _customerDataProvider;
    private CustomerItemViewModel? _selectedCustomer;

    public MainViewModel(ICustomerDataProvider customerDataProvider) 
    { 
        // … 
    }

    public ObservableCollection<CustomerItemViewModel> Customers { get; } = new();

    public CustomerItemViewModel? SelectedCustomer
    {
        get => _selectedCustomer;
        set
        {
            if (_selectedCustomer != null)
            {
                _selectedCustomer = value;
                RaisePropertyChanged();
                RaisePropertyChanged(nameof(IsCustomerSelected));
            }
        }
    }

    public bool IsCustomerSelected => SelectedCustomer is not null;

    public event PropertyChangedEventHandler? PropertyChanged;

    public Task LoadAsync()
    {
        // …

        if (customers is not null)
            foreach (var customer in customers)
                Customers.Add(new CustomerItemViewModel(customer));
    }
    // …
}
```

`MainWindow.xaml`
```xml
<!-- ... -->

<!-- Customer detail -->
<!-- 
    Visibility can be Collapsed or Visible; x:Bind will convert a bool property into these values:
    Set Mode to OneWay so Visibility gets updated every time the IsCustomerSelected property is changed:
-->
<StackPanel Grid.Row="1" Grid.Column="1" Margin="10" Visibility="{x:Bind ViewModel.IsCustomerSelected} Mode=OneWay">
    <TextBox Header="Firstname" Text="{x:Bind ViewModel.SelectedCustomer.FirstName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"/>
    <TextBox Header="Lastname"
        Text="{x:Bind ViewModel.SelectedCustomer.LastName, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}",
        Margin="0 10 0 0"/>
    <CheckBox Margin="0 20 0 0"
        IsChecked="{x:Bind ViewModel.SelectedCustomer.IsDeveloper, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}">
            Is developer
    </CheckBox>
</StackPanel>
```
