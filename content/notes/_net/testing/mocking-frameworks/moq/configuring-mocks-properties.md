---
title: configuring mocks — properties
date: 2023-11-05T00:00:00-06:00
draft: false
weight: 1
---

# overview
> Credit: https://hamidmosalla.com/2017/08/03/moq-working-with-setupget-verifyget-setupset-verifyset-setupproperty/

Examples in these notes use this system:
```cs
public interface IPropertyManager
{
    string FirstName { get; set; }
    string LastName { get; set; }
    void MutateFirstName(string name);
}

public class PropertyManager : IPropertyManager
{
    public string FirstName { get; set; }
    public string LastName { get; set; }

    public void MutateFirstName(string name) => this.FirstName = name;
}

class PropertyManagerConsumer
{
    private readonly IPropertyManager _propertyManager;

    public PropertyManagerConsumer(IPropertyManager propertyManager) => _propertyManager = propertyManager;

    public void ChangeName(string name) => _propertyManager.FirstName = name;

    public string GetName() => return _propertyManager.FirstName;

    public void ChangeRemoteName(string name) => _propertyManager.MutateFirstName(name);
}
```

And this test arrangement:
```cs
var mock = new Mock<IPropertyManager>();

var sut = new PropertyManagerConsumer(mock.Object);
```

## property chains
Also known as *recursive mocks*:
```cs
var mock = new Mock<HttpContextBase>();
mock.SetupGet(p => p.Response.Request.UserAgent).Returns("My Browser");
```

## `SetupGet` (Getters)
Use `SetupGet()` to stub a property with a certain value and verify that the system under test sees it:
```cs
mock.SetupGet(m => m.FirstName).Returns("Jane");

Assert.IsTrue(sut.GetName() == "Jane");
```

A property stubbed with `SetupGet()` cannot later be changed. To do that, see `SetupProperty()` below.

## `SetupSet` (Setters)
Use `SetupSet()` to set the expectation that, when the system under test runs, it sets the `FirstName` property of the mocked type to `John` via that property's setter: 
```cs
mock.SetupSet(m => m.FirstName = "John").Verifiable();

sut.ChangeName("John");

// Verify that the IPropertyManager's FirstName property was set to "John" via a call to the system under test's ChangeName method:
mock.Verify();
```

Or, if we didn't call `SetupSet()`, we could use `VerifySet()` to the same effect:
```cs
sut.ChangeName("John");

// Verify that the IPropertyManager's FirstName property was set to "John" via a call to the system under test's ChangeName method:
mock.VerifySet(m => m.FirstName = "John");
```

## verify some method of the sut passes the correct argument
```cs
sut.ChangeRemoteName("Jack");

// ChangeRemoteName calls the PropertyManager's MutateFirstName method
// Verify that ChangeRemoteName sends the correct string to MutateFirstName
mock.Verify(m => m.MutateFirstName(It.Is<string>(a => a == "Jack")), Times.Once);
```

## `SetupProperty` for Tracking Auto Properties
Use `SetupProperty()` to start "tracking" the sets/gets on a property (useful for automatic properties):
```cs
mock.SetupProperty(m => m.FirstName);
mock.Object.FirstName = "Jill";

Assert.IsTrue(mock.Object.FirstName == "Jill");

mock.Object.FirstName = "Julia";
Assert.IsTrue(mock.Object.FirstName == "Julia");
```

Without the call to SetupProperty(), the above assertions would fail.

## `SetupAllProperties` to Track All Auto Properties
```cs
mock.SetupAllProperties();

mock.Object.FirstName = "John";
mock.Object.LastName = "Wick";

Assert.IsTrue(mock.Object.FirstName == "John");
Assert.IsTrue(mock.Object.LastName == "Wick");
```

Above, if we only used `mock.SetupProperty(m => m.FirstName)`, the second assertion would fail because only the `FirstName` property is being tracked.