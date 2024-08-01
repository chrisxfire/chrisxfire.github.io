---
title: another example
date: 2022-08-26T07:36:43-0600
draft: false
weight: 1
---
Using DI, we move the creation and binding of dependent objects outside of the class that depends on them.
It involves 3 classes:
(1) Client class – class which depends on the Service.
(2) Service class – class that provides the Service that the Client class depends on.
(3) Injector class – creates a Service class object and injects it into the Client object.

## Non-DI Example
```cs
public interface ICustomerDataAccess 
{
    string GetCustomerName(int id);
}

public class CustomerDataAccess: ICustomerDataAccess 
{
    public CustomerDataAccess() { }

    public string GetCustomerName(int id) => "Dummy Customer Name";
}

public class DataAccessFactory 
{
    public static ICustomerDataAccess GetCustomerDataAccessObj() => new CustomerDataAccess();
}

public class CustomerBusinessLogic 
{
    ICustomerDataAccess _custDataAccess;

    public CustomerBusinessLogic() 
    {
        // DataAccessFactory is used here. This is problematic: If there is another implementation of ICustomerDataAccess
        // that we want to use, the source code here will need to change.
        _custDataAccess = DataAccessFactory.GetCustomerDataAccessObj();
    }

    public string GetCustomerName(int id) => return _custDataAccess.GetCustomerName(id);
}
```

## Constructor Injection Example
```cs
// Client class:
public class CustomerBusinessLogic 
{
    ICustomerDataAccess _dataAccess;

    // This constructor has one parameter of type ICustomerDataAccess. When this class is called,
    // an object of type ICustomerDataAccess will be injected:
    public CustomerBusinessLogic(ICustomerDataAccess custDataAccess) 
    {
        _dataAccess = custDataAccess;
    }

    public CustomerBusinessLogic() 
    {
        _dataAccess = new CustomerDataAccess();
    }

    public string ProcessCustomerData(int id) => _dataAccess.GetCustomerName(id);
}

interface ICustomerDataAccess 
{
    string GetCustomerName(int id);
}

// Service class:
public class CustomerDataAccess: ICustomerDataAccess 
{
    public CustomerDataAccess() { }

    public string GetCustomerName(int id) => return "Dummy Customer Name";
}

// Example of calling this class:
// Injector class – this class creates and injects a CustomerDataAccess object into the CustomerBusinessLogic class:
public class CustomerService 
{
    CustomerBusinessLogic _customerBL;

    public CustomerService() 
    {
        _customerBL = `new CustomerBusinessLogic(new CustomerDataAccess());`
    }

    public string GetCustomerName(int id) => return _customerBL.ProcessCustomerData(id);
}
```

## Property Injection Example
```cs
// Client class:
public class CustomerBusinessLogic 
{
    // This public property can be set with an instance of a class that implements ICustomerDataAccess:
    public ICustomerDataAccess DataAccess { get; set; }
    public CustomerBusinessLogic() { }

    public string GetCustomerName(int id) => return DataAccess.GetCustomerName(id);
}
interface ICustomerDataAccess 
{
    string GetCustomerName(int id);
}

// Service class:
public class CustomerDataAccess: ICustomerDataAccess 
{
    public CustomerDataAccess() { }

    public string GetCustomerName(int id) => return "Dummy Customer Name";
}

// Injector class:
public class CustomerService 
{
    CustomerBusinessLogic _customerBL;

    public CustomerService() 
    {
        _customerBL = new CustomerBusinessLogic();
        _customerBL.DataAccess = new CustomerDataAccess();
    }

    public string GetCustomerName(int id) => return _customerBL.GetCustomerName(id);
}
```

## Example of Method Injection with Interface Method
```cs
interface IDataAccessDependency 
{
    void SetDependency(ICustomerDataAccess customerDataAccess);
}

// By implementing IDataAccessDependency with SetDependency method:
public class CustomerBusinessLogic : IDataAccessDependency 
{
    ICustomerDataAccess _dataAccess;

    public CustomerBusinessLogic() { }

    public string GetCustomerName(int id) => _dataAccess.GetCustomerName(id);
    public void SetDependency(ICustomerDataAccess customerDataAccess)
    {
        _dataAccess = customerDataAccess;
    }
}

public class CustomerService 
{
    CustomerBusinessLogic _customerBL;

    public CustomerService() 
    {
        _customerBL = new CustomerBusinessLogic();
        ((IDataAccessDependency)_customerBL).SetDependency(new CustomerDataAccess());
    }

    public string GetCustomerName(int id) => return _customerBL.GetCustomerName(id);
}
```
