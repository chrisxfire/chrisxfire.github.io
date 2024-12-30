---
title: overview
date: 2023-10-04T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/io/common-i-o-tasks)]  

The `System.IO` namespace contains types to:
* Read or write files
* Read or modify directories
* Read or write data streams
* Compress or decompress files
* Communicate via pipes and serial ports

<o>Asynchronous I/O</o>: Synchronous I/O operations block the UI thread until complete. Use asynchronous operations to prevent this.  

# Overview of Types for Files/Directories
| Type            | Static or Instance methods | Description                                           |
| --------------- | -------------------------- | ----------------------------------------------------- |
| `File`          | static                     | For manipulating files, creating `FileStream` objects |
| `FileInfo`      | instance                   | For manipulating files, creating `FileStream` objects |
| `Directory`     | static                     | For manipulating directories                          |
| `DirectoryInfo` | instance                   | For manipulating directories                          |
| `Path`          | both                       | For manipulating paths                                |

See [Notes on File IO](../file-io).

# overview of types for streams
| Type                        | Use                                                   |
| --------------------------- | ----------------------------------------------------- |
| `FileStream`                | Reading/writing a file                                |
| `IsolatedStorageFileStream` | Reading/writing a file in isolated storage            |
| `MemoryStream`              | Reading/writing to memory as a backing store          |
| `BufferedStream`            | Improving performance of read/write operations        |
| `NetworkStream`             | Reading/Writing over network sockets                  |
| `PipeStream`                | Reading/writing over anonymous and named pipes        |
| `CryptoStream`              | Linking data streams to cryptographic transformations |

See [Notes on Streams](../streams).

# overview of types for compression
From the `System.IO.Compression` namespace:
| Type                | Use                                                               |
| ------------------- | ----------------------------------------------------------------- |
| `ZipArchive`        | Creating and retrieving compressed files in a zip archive         |
| `ZipArchiveEntry`   | Representing a compressed file                                    |
| `ZipFile`           | Creating, extracting and opening a compressed file                |
| `ZipFileExtensions` | Extensions for the above                                          |
| `DeflateStream`     | Compressing and decompressing streams using the Deflate algorithm |
| `GZipStream`        | Compressing and decompressing streams using the gzip data format  |

See [Notes on Compression and Decompression](../file-io#compression-and-decompression)

# Convenience vs. Control
Many of the APIs in the `System.IO` namespace can be placed on a spectrum of *convenience* vs *control*. 
These APIs are listed from low level (most control) to high level (most convenient)

## reading a text file
1. `File.OpenHandle` + `RandomAccess.Read` (most control)
2. `File.Open` + `FileStream`.Read`
3. `File.OpenText` + `StreamReader.ReadLine`
4. `File.ReadLines` + `IEnumerable<string>`
5. `File.ReadAllLines` + `string[]`
6. `File.ReadAllText` + `string` (most convenient)

## reading json text
1. `Utf8JsonReader` + `Pipelines` or `Stream` (most control)
2. `JsonDocument` + `Stream`
3. `JsonSerializer` + `Stream`
4. `JsonSerializer` + `string` (most convenient)