---
title: error handling
date: 2023-10-04T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/io/handling-io-errors

I/O methods throw these exceptions:
- `IOException` — the base class of all System.IO exceptions
- `FileNotFoundException`
- `DirectoryNotFoundException`
- `DriveNotFoundException`
- `PathTooLongException`
- `OperationCanceledException`
- `UnauthorizedAccessException`

I/O methods wrap calls to the underlying operating system. If an I/O error occurs in code executed by the OS, the OS 
returns error information to the .NET I/O method. This error maps to a .NET exception type. For example, on Windows, 
`ERROR_FILE_NOT_FOUND` (`0x02`) maps to `FileNotFoundException`. However, the precise conditions under which this mapping
succeeds varies. Always catch `IOException` last in your catch blocks. 

# `IOException`
`IOException` contains additional error information in its `HResult` property:
| HResult value           | Constant | Description                                                   |
| ----------------------- | -------- | ------------------------------------------------------------- |
| ERROR_SHARING_VIOLATION | 32       | The file name is missing, or the file or directory is in use. |
| ERROR_FILE_EXISTS       | 80       | The file already exists.                                      |
| ERROR_INVALID_PARAMETER | 87       | An argument supplied to the method is invalid.                |
| ERROR_ALREADY_EXISTS    | 183      | The file or directory already exists.                         |

The HResult value can be converted to a Win32 error code by stripping out the upper 16 bits of the 32-bit value:
```cs
// ...
catch (IOException e) when ((e.HResult & 0x0000FFFF) == 32)
{
    Console.WriteLine("There is a sharing violation.");
}
// ...
```