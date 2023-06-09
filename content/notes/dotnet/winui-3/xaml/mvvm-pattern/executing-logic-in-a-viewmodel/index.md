---
title: notes > dotnet > winui 3 > xaml > mvvm pattern > executing logic in a viewmodel
date: 2022-12-18T20:02:53-0700
draft: false
---
# First Technique to Execute Logic in a ViewModel
Bind events to methods with `x:Bind`  

Assume an `Add` method in the ViewModel that should be called every time a `Button` is clicked in the View:

## Okay Approach
Use the `Button`'s `Click` event; install an event handler in the View's code-behind file:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image1.png" style="width:5.63333in;height:3.13333in" />   

Disadvantage: An event handler needs to be installed in the code-behind file for every method of the ViewModel that needs to be called.  

## Better Approach: Bind Events to Methods with x:Bind
Bind the `Click` event to the `Add` method with `x:Bind`:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image2.png" style="width:5.675in;height:3.16667in" />  

`MainViewModel.cs`
```cs
// …

public void Add()
{
    var customer = new Customer { FirstName = "New" };
    var viewModel = new CustomerItemViewModel(customer);
    Customer.Add(viewModel);
    SelectedCustomer = viewModel;
}
```

`MainWindow.xaml`
```xml
<!-- ... -->
<!-- Bind the Click event to the Add method: -->
<Button Margin="10" Click="{x:Bind ViewModel.Add}">
    <StackPanel Orientation="Horizontal">
        <SymbolIcon Symbol="AddFriend"/>
        <TextBlock Text="Add" Margin="5 0 0 0"/>
    </StackPanel>
</Button>
```
# Second Technique to Execute Logic in a ViewModel
Use Commands.

Assume that the user can only use the `Add` method (via the `Button)` when a certain condition is met:  

## Okay Approach
Add a `CanAdd` property to the ViewModel and a `IsEnabled` property to the View, then `x:Bind` them. When the `CanAdd` condition is met, the `Button` is enabled:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image3.png" style="width:5.86667in;height:3.29167in" />  

## Better Approach: Use Commands
Button's have a `Command` property:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image4.png" style="width:5.83333in;height:1.33333in" />  

Create a class that implements this interface. Assign an instance of that class to the `Button`'s `Command` property. When `Button` is clicked, it will call the `Execute` method of its `Command.`  

When `Button`'s `Command` property is set, `Button` will call the `CanExecute` method of `Command.` It uses return value to set its own `IsEnabled` property.  

`Button` subscribes to `CanExecuteChanged` event of the `Command.` When `Command` raises this event, `Button` will call `CanExecute` method again.  

Note that `CanExecute` and `Execute` accept a parameter of type `object.`  

Optionally, set the `Button`'s `CommandParameter` property to specify the parameter's type:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image5.png" style="width:1.725in;height:1.125in" />  

To use the `Command`, create an `AddCommand` property in the ViewModel of type `ICommand`.
Then, bind the `Button`'s `Command` property in the View to the `AddCommand` property in the ViewModel:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image6.png" style="width:6.03333in;height:3.425in" />  

To trigger the `Add` method when the `AddCommand` property is set:
- Build a `DelegateCommand : ICommand` class (the `DelegateCommand` might also be called `ActionCommand` or `RelayCommand`
- The ViewModel creates an instance of this class and assigns it to its own `AddCommand` property
- ViewModel, when constructing DelegateCommand, will pass an Action delegate that points to the Add method of the ViewModel:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image7.png" style="width:6.025in;height:2.25833in" />

When the `Button` is clicked, the `Execute` method of `DelegateCommand` is called.  
The `Execute` method calls the `Action` delegate which points to the `Add` method of the ViewModel:  
<img src="XAML_MVVM-Pattern_Executing-Logic-in-a-ViewModel-image8.png" style="width:6.075in;height:2.28333in" />  

