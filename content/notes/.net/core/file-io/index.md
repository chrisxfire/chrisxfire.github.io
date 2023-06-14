---
title: notes > .net > core > file io
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
