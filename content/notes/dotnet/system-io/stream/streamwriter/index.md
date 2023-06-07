---
title: "notes > dotnet > system io > stream > streamwriter"
date: 2022-01-12T20:23:00-0700
draft: true
---
# [StreamWriter Class (System.IO) | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamwriter?view=net-6.0)
Object –> MarshalByRefObject –> TextWriter –> StreamWriter
- A `TextWriter` that writes characters (not bytes) from a stream in a particular encoding (like UTF-8).
- Implements `IDisposable`.

- Not thread safe. See `TextWriter.Synchronized`.

# Example
StreamWriter tw = File.CreateText(*textfile*); // TextWriter
tw.WriteLine("*some text*");
tw.Close(); // Close the file and release resources.

StreamReader tr = File.OpenText(*textfile*); // TextReader
WriteLine(tr.ReadToEnd());
tr.Close();

# Fields
CoreNewLineStores the newline characters used for this TextWriter.
Null

# Properties
AutoFlushBoolean if this StreamWriter should flush its buffer after every call to Write().
BaseStreamGets the underlying stream.
EncodingGets the encoding in which output will be written.
NewLineGets or sets the linte terminator string.

# Common Methods
Flush & FlushAsyncClear all buffers and write any buffered data.
Write & WriteAsyncWrite data to the stream.
WriteLine & WriteLineAsyncWrite a formatting string and newline to the stream.