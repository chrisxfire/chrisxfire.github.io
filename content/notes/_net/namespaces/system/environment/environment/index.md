---
title: notes > .net > namespaces > system > environment > environment
date: 2021-11-28T12:31:13-0700
draft: false
---
# [System.Environment](https://docs.microsoft.com/en-us/dotnet/api/system.environment?view=net-6.0)
`Object` –> `Environment`  

Information about and manipulation of the current environment and platform.

# Properties
- `CommandLine` Returns the command line arguments as a string where the first term is the command itself
- `Current` DirectoryGets or sets the CWD
- `ExitCode`
- `Is64BitOperatingSystem` Boolean if OS is 64-bit
- `Is64BitProcess` Boolean if the current process if 64-bit
- `MachineName` Returns the system's name
- `NewLine` Returns a platform-independent newline (\r\n for non-Unix platforms; \n for Unix platforms)
- `OSVersion` Returns an OperatingSystem OSVersion object. See also: OSVersion.VersionString
- `ProcessId` Returns the PID of the current process as an int
- `ProcessorCount` Returns the number of processors available to the current process
- `ProcessPath` Returns the path of the executable that started the current process
- `StackTrace` Returns current stack trace information
- `SystemDirectory` Returns the path of the system directory
- `TickCount64` Returns the number of milliseconds elapsed since the system started
- `UserDomainName` Returns the domain username of the current user
- `UserName` Returns the username of the current process

# Methods
- `Exit(int)` Terminate this process and return exit code int to the OS
- `FailFast(string)` Terminate this process immediately (do not run Catch blocks), and write string to Application event log
- `GetCommandLineArgs()` Returns the command line arguments as a string[]. `[0]` is the executable name
- `GetEnvironmentVariable(string)` Return environment variable string or null if not found
- `GetEnvironmentVariables()` Return all environment variables as a Dictionary
- `GetFolderPath(Environment.SpecialFolder)` Return the path of SpecialFolder
- `GetLogicalDrives()` Return all logical drives as an array of strings
- `SetEnvironmentVariable(string variable, string value)` Set environment variable to value.
