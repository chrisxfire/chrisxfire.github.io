---
title: notes > .net > user interfaces > winui 3 > xaml > mvvm pattern > refactor logic into a viewmodelbase class
date: 2022-12-14T19:09:48-0700
draft: false
---

# Refactor Logic into a ViewModelBase Class
Move the `INotifyPropertyChanged` interface into a base class so that it can be moved into other ViewModels:

`MainViewModel.cs`
```cs
public class MainViewModel : INotifyPropertyChanged { … }
```

`ViewModelBase.cs`
```cs
public class ViewModelBase : INotifyPropertyChanged
{
    // Moved from MainViewModel:
    public event PropertyChangedEventHandler? PropertyChanged;

    // Moved from MainViewModel:
    // Change access modifier to protected to call this from subclasses:
    protected virtual void RaisePropertyChanged(string? propertyName = null)
    {
        // The sender is this MainViewModel instance;
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

`MainViewModel.cs`
```cs
public class MainViewModel : ViewModelBase { … }
```