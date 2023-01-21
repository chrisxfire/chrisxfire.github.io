---
layout: post
title: "sucky api"
date: 
categories: rants
---
<style>
r { color: Red }
o { color: Orange }
g { color: Green }
b { color: Blue }
</style>

* The API doc says to use `FileService`'s `ListFolders(string parentFolder)` method to get a list of subfolders under the specified folder.
* The API doc claims that `ListFolders` will return a `List<FolderInfo>` (it doesn't; it returns a `FolderInfo[]`.)
* A `FolderInfo` object has these properties:

```C#
bool HasChildren
string Name
string Owner
```

Notice that `ListFolders` requires a `parentFolder` string and, while it returns a `FolderInfo` array of the subfolders under `parentFolder`, the resulting `FolderInfo` object only tells you whether it `HasChildren` (translation: subfolders) but does not tell you what those subfolders actually are.