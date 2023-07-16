---
title: notes > code > .net > user interfaces > winui 3 > xaml > dependency injection
date: 2022-12-29T21:44:48-0700
draft: false
---
# Overview
The `MainWindow` knows how to create the MainViewModel with a customer data provider.  
This is problematic because `MainWindow`'s responsibility is only to be the `MainWindow` of our application. Knowing how to instantiate a MainViewModel is outside of its scope.  
`MainViewModel` is a dependency that `MainWindow` needs (and stores in its `MainViewModel` property below).

# Manually Inject the `MainViewModel` Dependency into `MainWindow`
Adjust MainWindow so its constructor takes a `MainViewModel` as a parameter (required for DI):

`MainWindow.xaml.cs`
```cs
// …
public MainWindow()
{
    this.InitializeComponent();
    Title = "Customers App";
    ViewModel = new MainViewModel(new CustomerDataProvider());
    root.Loaded += Root_Loaded;
}

public MainViewModel ViewModel { get; }
// …
```

To correct this:
```cs
// Take a MainViewModel as a parameter on the constructor:
public MainWindow(MainViewModel viewModel)
{
    this.InitializeComponent();
    Title = "Customers App";
    ViewModel = viewModel;
    root.Loaded += Root_Loaded;
}
// …
```

`App.xaml.cs`
```cs
// …
protected override void OnLaunched(Microsoft.Ui.Xaml.LaunchActivatedEventArgs args)
{
    // Inject the MainViewModel dependency into the constructor of MainWindow (manually):
    m_window = new MainWindow(new MainViewModel(new CustomerDataProvider()));
    m_window.Activate();
}
// …
```

# Using Dependency Injection
`App.xaml.cs`
```cs
public partial class App : Application
{
    private Window? m_window;
    private readonly ServiceProvider _serviceProvider;

    public App()
    {
        this.InitializeComponent();
        // Add a new ServiceCollection:
        ServiceCollection services = new();
        ConfigureServices(services);
        _serviceProvider = services.BuildServiceProvider;
    }

    private void ConfigureServices(ServiceCollection services)
    {
        // Register the dependencies:
        services.AddTransient<MainWindow>();
        services.AddTransient<MainViewModel>();
        // When an ICustomerDataProvider object is required, DI will create an instance of CustomerDataProvider:
        services.AddTransient<ICustomerDataProvider, CustomerDataProvider>();
    }

    protected override void OnLaunched(Microsoft.UI.Xaml.LaunchActivatedEventArgs args)
    {
        m_window = new MainWindow(new MainViewModel(new CustomerDataProvider()));
        m_window = serviceProvider.GetService<MainWindow>();
        m_window?.Activate();
    }
}
```
`MainWindow.xaml.cs`
```cs
public sealed partial class MainWindow : Window
{
    // ICustomerDataProvider can now be injected into the constructor of any class
    // (for illustration only; no need to do this)
    public MainWindow(MainViewModel viewModel, ICustomerDataProvider dataProvider)
    {
        // No further changes beside the constructor are required.
        // …
    }
    // …
}
```
