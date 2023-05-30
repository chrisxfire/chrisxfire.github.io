---
title: "notes > dotnet > linq > linq and strings"
date: 2022-11-14T20:11:32-0700
draft: true
---
For all examples:

string startFolder = @"*path*";

System.IO.DirectoryInfo dir = new(startFolder);

IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);

# Query for Files by Attribute or Name
var fileQuery = from file in fileList
where file.Extension == ".txt"
orderby file.Name
select file;

## <u>Find the Newest File</u>
var newestFile = (from file in fileQuery
orderby file.CreationTime
select new { file.FullName, file.CreationTime })
.Last();

# Group Files by Extension
int trimLength = startFolder.Length;

var queryGroupByExt = from file in fileList
group file by File.Extensions.ToLower() into fileGroup
orderby fileGroup.Key
select fileGroup;

# Query for the Largest File(s) in a Directory Tree
long maxSize = (from file in fileList
select file.Length)
.Max();

var longestFile = (from file in fileList
where file.Len > 0
orderby file.Len descending
select file)
.First();

var tenLongestFiles - (from file in fileList
orderby file.Len descending
select file).Take(10);

# Query for Duplicate Files in a Directory Tree
int charsToSkip = startFolder.Length;

var queryDupNames = from file in fileList
group file.FullName.Substring(charsToSkip) by file.Name into fileGroup
where fileGroup.Count() > 1
select fileGroup;