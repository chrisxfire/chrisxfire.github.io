---
title: notes > .net > user interfaces > winui 3 > xaml > mvvm pattern > notify data binding when property changes
date: 2022-12-14T18:56:52-0700
draft: false
---
# Notify the Data Binding when Property Changes
Implement the `INotifyPropertyChanged` interface on the ViewModel:

`MainViewModel.cs`
```cs
public class MainViewModel : INotifyPropertyChanged
{
    private readonly ICustomerDataProvider _customerDataProvider;
    private Customer? _selectedCustomer;

    // Using an interface prevents MainViewModel from being tightly coupled to DataProvider
    public MainViewModel(ICustomerDataProvider customerDataProvider) { … }

    // A collection type that notifies the data binding when items are added or removed
    public ObservableCollection<Customer> Customers { get; } = new();

    public Customer? SelectedCustomer 
    {
        get => _selectedCustomer;
        set
        {
            // If the passed in value is not the current value, set it and then raise the event:
            if (_selectedCustomer != value)
            {
                _selectedCustomer = value;
                RaisePropertyChanged();
            }
        }
    }

    public event PropertyChangedEventHandler? PropertyChanged;

    public Task LoadAsync() { … }

    // The CallerMemberName attribute injects the name of the method that is calling this one:
    private void RaisePropertyChanged([CallerMemberName] string? propertyName = null)
    {
        // The sender is this MainViewModel instance;
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```