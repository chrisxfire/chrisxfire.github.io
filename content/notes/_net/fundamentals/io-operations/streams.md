---
title: streams
date: 2022-01-22T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/io/

A *stream* is a sequence of bytes that can be read from and written to.  

Streams involve three fundamental operations:
- `Read` – The transfer of data from a stream into a data structure.
- `Write` – The transfer or data from a data structure into a stream.
- `Seek` – Querying and modifying the current position within a stream.

Depending on a stream's underlying data source, a stream may only support some subset of these operations. 
This can be tested with `CanRead`, `CanWrite`, and `CanSeek` properties.

# Overview of Types for Streams
See [here](../overview#overview-of-types-for-streams).

# Composing Streams
> Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.io.stream?view=net-6.0  
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/io/composing-streams

`Stream` is the abstract base class of all streams. All streams implement `IDisposable`.

A *backing store* is a storage medium such as disk or memory. Each backing store implements its own stream as an implementation
of the `Stream` class.  
A *base stream* is a stream that connect to a backing store. They have constructors with the necessary parameters to 
connect the stream to the backing store.

Base streams can be attached to one or more *pass-through streams* that provide specific functionality. In this example,
the base stream is a `FileStream` and the pass-through stream is a `StreamReader` composed of that base stream: 
```cs {hl_lines=[13,15]}
using System;
using System.IO;

public class CompBuf
{
    private const string FILE_NAME = "MyFile.txt";

    public static void Main()
    {
        if (!File.Exists(FILE_NAME))
			throw new Exception();

        FileStream fsIn = new FileStream(FILE_NAME, FileMode.Open, FileAccess.Read, FileShare.Read);
        
		using (StreamReader sr = new StreamReader(fsIn))
        {
            string input;
            // While not at the end of the file, read lines from the file.
            while (sr.Peek() > -1)
            {
                input = sr.ReadLine();
                Console.WriteLine(input);
            }
        }
    }
}
```

# Bit Bucket
A stream with no backing store.  To create this, use the `Null` field to retrieve an instance of a stream.

# Readers and Writers
The `System.IO` namespace contains types for reading encoded characters from and writing to streams. 
These types handle conversion of encoded characters to and from bytes. Each reader and writer class is associated 
with a stream accessible via its `BaseStream` property.

| Helper Class                      | Use                                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------------------- |
| `BinaryReader` and `BinaryWriter` | Reading and writing primitive data types as binary values                                         |
| `StreamReader` and `StreamWriter` | Reading and writing characters by using an encoding value to convert the characters to/from bytes |
| `StringReader` and `StringWriter` | Reading and writing characters to/from strings                                                    |
| `TextReader` and `TextWriter`     | The abstract base class for other readers and writers of text data (but not binary data)          |

# Stream Helpers
## StreamReader 
A `TextReader` that reads characters (not bytes) from a stream in a particular encoding (like UTF-8).
- Implements `IDisposable`.
- <r>Warning</r>: Not thread safe. See `TextReader.Synchronized`.

```cs
StreamWriter tw = File.CreateText(PATH_TO_TEXT_FILE); // TextWriter
tw.WriteLine("*some text*");
tw.Close(); // Close the file and release resources.
```

## StreamWriter
A `TextWriter` that writes characters (not bytes) from a stream in a particular encoding (like UTF-8).  
- Implements `IDisposable`.
- <r>Warning</r>: Not thread safe. See `TextWriter.Synchronized`.

```cs
StreamReader tr = File.OpenText(PATH_TO_TEXT_FILE); // TextReader
WriteLine(tr.ReadToEnd());
tr.Close();
```

# Writing to XML Streams
Use `WriteStartElement` and `WriteEndElement` when an element may have child elements.  
Use `WriteElementString` when an element does not have children.

```cs
FileStream? xmlFileStream = null;
XMLWriter? xml = null;

using (xmlFileStream = File.Create(file.xml)) // The using statement automatically generates a finally statement
{							// that calls Dispose on any object that implements IDisposable.
	using (xml = XmlWriter.Create(xmlFileStream, // Wrap the file stream in an XML writer stream helper.
	  new XmlWriterSettings { Indent = true} ))  // Automatically indent nested elements.
	{
		try 
		{
			xml.WriteStartDocument(); // Write the XML declaration.
			
			xml.WriteStartElement("callsigns"); // Write a root element.
			xml.WriteElementString("callsign", "Maverick");
			xml.WriteElementString("callsign", "Iceman");
			
			xml.WriteEndElement(); // Write the close root element.
			
			xml.Close(); // Close the helper.
			xmlFileStream.Close(); // Close the file stream.
		}
		catch (Exception ex) {
			…
		}
	} // Automatically calls xml.Dispose() if the object is not null.
} // Automatically calls xmlFileStream.Dispose() if the object is not null.
```

Output:
```xml
<?xml version="1.0" encoding="utf-8"?>
<callsigns>
	<callsign>Maverick</callsign>
	<callsign>Iceman</callsign>
</callsigns>
```

# Reading from XML Streams
```cs
using (XmlReader reader = XmlReader.Create(xmlFilestream))
{
	while (reader.Read()) // Read the nextXML node.
	{
		if ((reader.NodeType = XmlNodeType.Element) // Check if we are on an element node named "callsign".
		  && (read.Name == "callsign"))
		{
			reader.Read(); // Move to the text inside the element.
			Console.WriteLine($"{reader.Value}"); // Read this element's value.
		}
	}
}
```

# Compressing Streams
```cs
using System.IO.Compression; // BrotliStream, GZipStream, CompressionMode 
// Performance-wise, Brotli is like GZip/Deflate but 20% denser.
FileStream file = File.Create(filePath);

Stream compressor = new GZipStream(file, CompressionMode.Compress); // Compress file.

using (compressor)
{
	using (XmlWriter xml = XmlWriter.Create(compressor))
	{
		xml.WriteStartDocument();
		xml.WriteStartElement("callsigns");
		xml.WriteElementString("callsign", "Maverick");
		xml.WriteElementString("callsign", "Iceman");
		
		// Due to the using statement on XmlWriter, the normal call to WriteEndElement is not necessary.  When
		// XmlWriter disposes, it will automatically end all elements of any depth.
	}
}
```

# Encoding / Decoding Streams
Example
```cs
StreamReader r = new(stream, Encoding.Encoding); // Text will be decoded as bytes are read from the stream.
StreamWriter w = new(stream, Encoding.Encoding); // Text will be encoded as bytes are written to the stream.
```

# `ReadExactly` and `ReadAtLeast`
`Stream.Read()` may return less data than what is available in the stream and less data than the buffer being passed in. `ReadExactly` and `ReadAtLeast` address this limitation.

## `ReadExactly`
Guaranteed to read exactly the number of bytes requested:
```cs
using FileStream f = File.Open("readme.md");
byte[] buffer = new byte[100];
f.ReadExactly(buffer); // guaranteed to read 100 bytes from the file
```

## `ReadAtLeast`
Guaranteed to read at least the number of bytes requested:
```cs
using FileStream f = File.Open("readme.md");
byte[] buffer = new byte[100];
int bytesRead = f.ReadAtLeast(buffer, 10);
// 10 <= bytesRead <= 10
```

<r>Warning:</r> Throws an `EndOfStreamException` if the stream ends before the requested bytes have been read.
