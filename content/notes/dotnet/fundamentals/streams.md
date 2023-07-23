---
title: notes > .net > fundamentals > streams
date: 2022-01-22T00:00:00-06:00
draft: false
weight: 1
---

# Streams
*Stream* – A sequence of bytes that can be read from and written to.

# `Stream` class
The abstract base class of all streams.
All streams implement `IDisposable`, giving them a `Dispose()` method to release unmanaged resources.

# Operations
Steams can be operated on as follows:
- `Read` – The transfer of data from a stream into a data structure.
- `Write` – The transfer or data from a data structure into a stream.
- `Seek` – Querying and modifying the current position within a stream.

# Bit Bucket
A stream with no backing store.  To create this, use the `Null` field to retrieve an instance of a stream.

# Writing to XML Streams
Use `WriteStartElement` and `WriteEndElement` when an element may have child elements.  
Use `WriteElementString` when an element does not have children.

```cs
FileStream? xmlFileStream = null;
XMLWriter? xml = null;

using (xmlFileStream = File.Create(file.xml)) // The using statement automatically generates a finally statement
{							// that calls Dipose on any object that implements IDisposable.
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
`Stream.Read()` may return less data than what is available in the Stream and less data than the buffer being passed in. `ReadExactly` and `ReadAtLeast` address this limitation.

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

<r>Note:</r> Throws an `EndOfStreamException` if the Stream ends before the requested bytes have been read.
