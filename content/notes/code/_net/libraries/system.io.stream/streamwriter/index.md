---
title: notes > code > .net > libraries > system.io.stream > streamwriter
date: 2022-01-12T20:23:00-0700
draft: false
weight: 1
---
# [StreamWriter Class (System.IO) | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamwriter?view=net-6.0)
`Object` –> `MarshalByRefObject` –> `TextWriter` –> `StreamWriter`  

- A `TextWriter` that writes characters (not bytes) from a stream in a particular encoding (like UTF-8).  
- Implements `IDisposable`.

- Not thread safe. See `TextWriter.Synchronized`.

# Example
```cs
StreamWriter tw = File.CreateText(*textfile*); // TextWriter
tw.WriteLine("*some text*");
tw.Close(); // Close the file and release resources.

StreamReader tr = File.OpenText(*textfile*); // TextReader
WriteLine(tr.ReadToEnd());
tr.Close();
```

# Fields
`CoreNewLine` — Stores the newline characters used for this TextWriter.  
`Null`  

# Properties
`AutoFlush` — Boolean if this StreamWriter should flush its buffer after every call to Write().  
`BaseStream` — Gets the underlying stream.  
`Encoding` — Gets the encoding in which output will be written.  
`NewLine` — Gets or sets the linte terminator string.  

# Common Methods
`Flush` & `FlushAsync` — Clear all buffers and write any buffered data.  
`Write` & `WriteAsync` — Write data to the stream.  
`WriteLine` & `WriteLineAsync` — Write a formatting string and newline to the stream.  
