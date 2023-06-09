---
title: "notes > dotnet > system io > stream > streamreader"
date: 2022-05-16T15:13:33-0600
draft: false
---
# [StreamReader](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamreader?view=net-6.0)
`Object` –> `MarshalByRefObject` –> `TextReader` –> `StreamReader`  

- A `TextReader` that reads characters (not bytes) from a stream in a particular encoding (like UTF-8).
- Implements `IDisposable`.

- Not thread safe. See `TextReader.Synchronized`.

# Encoding
`StreamReader` defaults to UTF-8.

# Fields
`Null` — Create an empty stream (a bit bucket).

# Properties
`BaseStream` — Returns the underlying stream.  
`CurrentEncoding` — Returns the current encoding.  
- Note: The value of this property is not reliable until after the first Read call.  
`EndOfStream` — Boolean if the current stream position is at the end of the stream.  

# Common Methods
`Dispose`  
`Peek` — Return the next available character, but do not consume it.  
`Read` & `ReadAsync` — Read the next character or set of characters.  
`ReadBlock` & `ReadBlockAsync` — Read characters and write them to a buffer.  
`ReadLine` & `ReadLineAsync` — Read the next line from the stream and return it as a string.  
- Note:  — Returns `null` if EOL.  
`ReadToEnd` & `ReadToEndAsync` — Read the rest of the stream and return it as a string.  
