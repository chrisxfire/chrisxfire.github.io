---
title: notes > .net > namespaces > system io > stream > stream
date: 2022-05-16T15:01:46-0600
draft: false
---
# [Stream](https://docs.microsoft.com/en-us/dotnet/api/system.io.stream?view=net-6.0)
A generic view of a sequence of bytes (not characters). The abstract base class of all streams.  
All streams implement `IDisposable`, giving them a Dispose() method to release unmanaged resources.  

# Operations
Steams can be operated on as follows:
- `Read` – The transfer of data from a stream into a data structure.
- `Write` – The transfer or data from a data structure into a stream.
- `Seek` – Querying and modifying the current position within a stream.

# Concrete Stream Classes
Concrete (instantiable) classes that inherit the `Stream` class include:  
- `BufferedStream` for wrapping a buffered stream around another to improve read/write performance.
- `FileStream` for bytes stored in a filesystem.
  - Reads from, writes to, opens, and closes files on a filesystem.
  - Buffers input/output automatically.
- `MemoryStream` for bytes stored in memory in the current process.
- `System.Net.Sockets.NetworkStream` for bytes stored at a network location.

# Function Stream Classes
Function streams cannot exist on their own but can only be "plugged onto" other streams to add functionality:
`System.Security.Cryptography.CryptoStream`Encrypts/decrypts a stream.
`System.IO.Compression.GZipStream`Compresses a stream.
`System.IO.Compression.DeflateStream`Decompresses a stream.
`System.Net.Security.AuthenticatedStream`Sends credentials across a stream.

# Stream Helpers
## `StreamReader` & `StreamWriter`
For reading and writing characters by using an encoding value to convert characters to/from bytes.

## `BinaryReader` & `BinaryWriter`
For reading and writing primitive data (but not character strings) as binary values.

## `StringReader` & `StringWriter`
For reading and writing characters to/from strings.

## XML
`System.Xml.XmlReader` — Reads from the underlying stream in XML format.  
`System.Xml.XmlWriter` — Writes to the underlying stream in XML format.  

# Properties
`CanRead` — Boolean if the stream is readable.  
`CanSeek` — Boolean if the Seek method can be used.  
`CanWrite` — Boolean if the stream is writable.  
`Length` — Total number of bytes in the stream.  
`Position` — Current position within the stream.  

# Methods
## Reading
`Read` — Read a specified number of bytes from the stream into a byte array.  
`ReadAsync`  
`ReadByte` — Read the next byte from the stream and advance the position.  

## Writing
`Write` — Write the contents of a byte array into the stream.  
`WriteAsync`  
`WriteByte` — Write a single byte to the stream.  

## Seeking
`Seek` — Move the current position to the one specified in the parameter.  
`SetLength`  

## Other
`Dispose` — Close the stream and release its (unmanaged) resources.  
`Flush` — If the stream has a buffer, write the bytes in the buffer to the stream (thereby "flushing" it).  
