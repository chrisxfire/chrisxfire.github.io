---
title: exceptions
date: 2021-11-09T00:00:00-06:00
draft: false
weight: 1
---
# Exceptions
All exceptions derive from `System.Exception`.

#Catch Exceptions
```cs
try { … }
catch (exception e) { // Catches a specific exception.  Stores it in e.
	// e.StackTrace contains the current call stack, file name, and line number where the exception was thrown.
	// e.Message contains the string describing the exception.
	// e.GetType() contains the type of the exception.
}
catch { … }	// Catches any exception.

catch { } // Use an empty catch block to catch errors, ignore them, and continue running.

finally { … } // This block is always executed, whether or not an exception is caught.
```

Notes:
- Order catch blocks from most specific to least specific.
		○ Example: `DirectoryNotFoundException –> FileNotFoundException –> IOException`
- If you catch `System.Exception`, rethrow it at the end of the catch block.

## Exception Filters
Exception Filters allow you to catch an exception only when a condition is true:
```cs
catch (Exception e) when (condition) { … }
```

# Throw Exceptions
```cs
throw new ExceptionType("Exception message");
```

## Rethrow Exceptions
If an exception is caught and you want to rethrow it up the stack use `throw.`
- If you `throw ex` to rethrow, the stack trace is lost.

If a catch block does nothing but rethrow exceptions, it is useless.  Remove it.

To wrap a caught exception in another with more information, throw a new exception and pass the caught exception as the `innerException` parameter:
```cs
catch (IOException ex) {
	…
	throw new InvalidOperationException(message: "This thing failed.", innerException: ex)
}
```
# Throwing Exceptions
## Throw These Exceptions
- `ArgumentException`
- `ArgumentNullException`
		○ Includes a second parameter, `ParamName`, that should be set to the name of the argument that caused the exception to be thrown.
		○ In a property setter, `ParamName` should be set to `value.`
- `ArgumentOutOfRangeException`
- `FormatException`
- `InvalidOperationException` – If the object is in an inappropriate state.
- `NotSupportedException`

## Do Not Throw These Exceptions
Don't throw or derive from:
- `AccessViolationException`
- `ApplicationException`
- `ComException`
- `ExecutionEngineException`
- `Exception` (why?)
- `IndexOutOfRangeException`
- `NullReferenceException`
- `OutOfMemoryException`
- `StackOverflowException`
- `SystemException`

# Create a Custom Exception [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/how-to-create-user-defined-exceptions)]  

Custom exception classes can be created.  They should have at least 4 constructors:
```cs
class CustomException : Exception {
	public CustomException() : base() { }
	
	// This constructor sets the message property only:
	public CustomException(string message) : base(message) { }
	
	// This constructor sets the message property and InnerException:
	public CustomException(string message, Exception inner) : base(message, inner) { }
	
	// This constructor creates serialization, which is needed when an exception propagates from a remote server to the client:
	public CustomException(System.Runtime.Serialization.SerializationInfo info, System.Runtime.Serialization.StreamingContext context) : base(info, context) { }
}

throw new CustomException("Exception message");
```

# Common Exception Classes
| Exception                     | Description                                                                                                                                                                   |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ArithmeticException`         | A base class for exceptions that occur during arithmetic operations, such as DivideByZeroException and OverflowException.                                                     |
| `ArrayTypeMismatchException`  | Thrown when an array can't store a given element because the actual type of the element is incompatible with the actual type of the array.                                    |
| `DivideByZeroException`       | Thrown when an attempt is made to divide an integral value by zero.                                                                                                           |
| `IndexOutOfRangeException`    | Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.                                                         |
| `InvalidCastException`        | Thrown when an explicit conversion from a base type to an interface or to a derived type fails at run time.                                                                   |
| `NullReferenceException`      | Thrown when an attempt is made to reference an object whose value is null.                                                                                                    |
| `OutOfMemoryException`        | Thrown when an attempt to allocate memory using the new operator fails. This exception indicates that the memory available to the common language runtime has been exhausted. |
| `OverflowException`           | Thrown when an arithmetic operation in a checked context overflows.                                                                                                           |
| `StackOverflowException`      | Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.                                    |
| `TypeInitializationException` | Thrown when a static constructor throws an exception and no compatible catch clause exists to catch it.                                                                       |
