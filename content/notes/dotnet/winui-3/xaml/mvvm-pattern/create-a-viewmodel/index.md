---
title: notes > dotnet > winui 3 > xaml > mvvm pattern > create a viewmodel
date: "2023-05-30T00:00:00-06:00"
date: 2022-12-14T18:55:47-0700
draft: false
---
# Creating
New Folder > ViewModel; MainViewModel.cs

`MainViewModel.cs`
```cs
public class MainViewModel
{
    private readonly ICustomerDataProvider _customerDataProvider;

    // Using an interface prevents MainViewModel from being tightly coupled to DataProvider
    public MainViewModel(ICustomerDataProvider customerDataProvider)
    {
        _customerDataProvider = customerDataProvider;
    }

    // A collection type that notifies the data binding when items are added or removed
    public ObservableCollection<Customer> Customers { get; } = new();

    public Task LoadAsync()
    {
        if (Customers.Any())
            // Customers were loaded already
            return;

        var customers = await _customerDataProvider.GetAllAsync();

        if (customers is not null)
            foreach (var customer in customers)
                Customers.Add(customer);
    }
}
```