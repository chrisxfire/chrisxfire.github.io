---
title: "notes > dotnet > system io > stream > streamreader"
date: 2022-05-16T15:13:33-0600
draft: true
---
# [StreamReader](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamreader?view=net-6.0)
Object –> MarshalByRefObject –> TextReader –> StreamReader
- A `TextReader` that reads characters (not bytes) from a stream in a particular encoding (like UTF-8).
- Implements `IDisposable`.

- Not thread safe. See `TextReader.Synchronized`.

# Encoding
`StreamReader` defaults to UTF-8.

# Fields
NullCreate an empty stream (a bit bucket).

# Properties
BaseStreamReturns the underlying stream.
CurrentEncodingReturns the current encoding.
- Note: The value of this property is not reliable until after the first Read call.
EndOfStreamBoolean if the current stream position is at the end of the stream.

# Common Methods
Dispose
PeekReturn the next available character, but do not consume it.
Read & ReadAsyncRead the next character or set of characters.
ReadBlock & ReadBlockAsyncRead characters and write them to a buffer.
ReadLine & ReadLineAsyncRead the next line from the stream and return it as a string.
- Note: Returns `null` if EOL.
ReadToEnd & ReadToEndAsyncRead the rest of the stream and return it as a string.
