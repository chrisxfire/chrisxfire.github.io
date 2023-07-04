---
title: notes > code > .net > fundamentals > file io
date: 2021-11-10T00:00:00-06:00
draft: false
---

# Iterator method to return sequence for lazy evaluation:
```cs
static IEnumerable<string> ReadFrom(string file) 
{
// The using statement manages resource cleanup; implements IDisposable interface; calls Dispose() to release resource even if an exception is thrown:
	using (var reader = File.OpenText(file)) 
    {		
		while ((line = reader.ReadLine()) != null) 
        {
			yield return line;
			
			// Or, return words instead of lines:
			var words = line.Split(' ');
			foreach (var word in words) 
            {
				yield return word + " ";
			}
			yield return Environment.NewLine
		}
	}
}
```

# StreamReader Method
```cs
using (var sr = new StreamReader(path)) 
{ 
	string contents = sr.ReadToEnd();
}
```

# File class
- Methods of `File` are static: it is more efficient to use these for a single operation than a `FileInfo` instance.

# Reading (Synchronous)
## Reading an Entire File
```cs
string text = System.IO.File.ReadAllText(@"path");

// Or, to read each line into a string array:
string[] lines = System.IO.File.ReadAllLines(@"path");
```

## Reading a File Line by Line
```cs
string path = @"path";
using (StreamReader sr = File.OpenText(Path)) 
{
	string s;
	while (s = sr.ReadLine() != null) 
	{
		…
	}
}
```

# Methods
- `File.AppendAllText(…)`
- `File.Copy(sourceFileName: filename, destFileName: filename, overwrite: bool)`
- `File.Delete(filename)`
- `File.Open(pathToFile, FileMode.<FileMode>, FileAccess.<FileAccess>)` 
- `File.ReadAllText(…)`
- `File.WriteAllText(…)`
