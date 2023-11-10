---
title: file io
date: 2021-11-10T00:00:00-06:00
draft: false
weight: 1
---

# Overview of Types for Files/Directories
See [here](../overview#overview-of-types-for-filesdirectories).

# File & Directory IO
All methods return `void` unless otherwise specified.

## Files
| Goal                             | Use                                                        |
| -------------------------------- | ---------------------------------------------------------- |
| Check for a file                 | `File.Exists` (returns `bool`)                             |
| Copy a file                      | `File.Copy` <br />  `FileInfo.CopyTo` (returns `FileInfo`) |
| Delete a file                    | `File.Delete`, `FileInfo.Delete`                           |
| Move/rename a file               | `File.Move`, `FileInfo.MoveTo`                             |
| Retrieve a full path             | `Path.GetFullPath`                                         |
| Retrieve file name and extension | `Path.GetFileName`                                         |
| Retrieve a file extension        | `Path.GetExtension`                                        |
| Change a file extension          | `Path.ChangeExtension`                                     |

## Text Files
| Goal                  | Use                                                                                                                                                                                          |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Create a text file    | `File.CreateText` (returns `StreamWriter`) <br /> `File.Create` (returns `FileStream`) <br /> `FileInfo.CreateText` (returns `StreamWriter`) <br /> `FileInfo.Create` (returns `FileStream`) |
| Write to a text file  | `StreamWriter` (`Write{Async}`, `WriteLine{Async}`) <br /> File (`WriteAllLines{Async}`, `WriteAllText{Async}`)                                                                              |
| Append to a text file | `File.AppendText` (returns `StreamWriter`) <br /> `FileInfo.AppendText` (returns `StreamWriter`)                                                                                             |
| Read from a text file | `StreamReader`                                                                                                                                                                               |

## Binary Files
| Goal      | Use            |
| --------- | -------------- |
| Read from | `BinaryReader` |
| Write to  | `BinaryWriter` |

## Directories
| Goal                    | Use                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| Check for a directory   | `Directory.Exists` (returns `bool`)                                                                  |
| Create a directory      | `Directory.CreateDirectory` (returns `DirectoryInfo`)                                                |
| Create a subdirectory   | `DirectoryInfo.CreateSubdirectory` (returns `DirectoryInfo`)                                         |
| Copy a directory        | Directories are copied by creating the directory in the new destination and then copying files to it |
| Delete a directory      | `Directory.Delete`, `DirectoryInfo.Delete`                                                           |
| Move/rename a directory | `Directory.Move`, `DirectoryInfo.MoveTo`                                                             |

# Enumerating Files and Directories [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/io/how-to-enumerate-directories-and-files)]  

Enumerable collections provide superior performance vs arrays when working with large collections. The `Directory` and
`DirectoryInfo` classes have enumeration methods that return enumerable collections:
| To retrieve              | Use                                      |
| ------------------------ | ---------------------------------------- |
| Directory names          | `Directory.EnumerateDirectories`         |
| DirectoryInfo objects    | `DirectoryInfo.EnumerateDirectories`     |
| File names               | `Directory.EnumerateFiles`               |
| FileInfo objects         | `DirectoryInfo.EnumerateFiles`           |
| Directory and file names | `Directory.EnumerateFileSystemEntries`   |
| FileSystemInfo objects   | `DirectoryInfo.EnumerateFileSystemInfos` |

# Compression and Decompression
For all examples:
```cs
using System.IO.Compression;
```

## Compression and Decompression For zip files
Compression (Creating a zip file):
```cs
var startPath = "/source/directory";
var zipFilePath = "/destination/compressed.zip";
zipFile.CreateFromDirectory(startPath, zipFilePath);)
```

Decompression (Extracting Contents of a zip file):
```cs
var zipFilePath = "/destination/compressed.zip";
var destinationPath = "/destination/directory";

// Normalize the destination path:
destinationPath = Path.GetFullPath(destinationPath);

// If the destinationPath does not end with the directory separator character, a path traversal attack is possible:
if (!destinationPath.EndsWith(Path.DirectorySeparatorChar.ToString(), StringComparison.Ordinal))
    destinationPath += Path.DirectorySeparatorChar;

zipFile.ExtractToDirectory(zipFilePath, destinationPath);
```

## Adding to a zip file
```cs
var zipFilePath = "/destination/compressed.zip";

using FileStream zipFilePath = new FileStream(zipFilePath, FileMode.Open);

using ZipArchive archive = new ZipArchive(zipFilePath, ZipArchiveMode.Update);
var fileEntry = archive.CreateEntry("SomeFile.txt");

using StreamWriter writer = new StreamWriter(fileEntry.Open());
writer.WriteLine("Some text...");
```

## Compression and Decompression for GZip
Compression:
```cs
var fileToCompress = new FileInfo("/source/file.txt");
using FileStream originalFileStream = fileToCompress.OpenRead();
using FileStream compressedFileStream = File.Create(fileToCompress.FullName + ".gz");
using GZipStream compressionStream = new GZipStream(compressedFileStream, CompressionMode.Compress);
originalFileStream.CopyTo(compressionStream);
```

Decompression:
```cs
var fileToDecompress = new FileInfo("/source/compressed.gz");
using FileStream originalFileStream = fileToDecompress.OpenRead();
using FileStream decompressedFileStream = File.Create("/destination/decompressed.txt");
using GZipStream decompressionStream = new GZipStream(originalFileStream, CompressionMode.Decompress);
decompressionStream.CopyTo(decompressedFileStream);
```