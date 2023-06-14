---
title: notes > .net > async programming > async io
date: "2022-02-16T00:00:00-06:00"
draft: false
---

# Async
Async reduces the need for threads in server-based applications.  If the app uses a dedicated thread per response and 1,000 requests are handled simultaneously, 1,000 threads are needed.  Async operations don't need to use a thread during the wait.  They use the existing I/O completion thread briefly at the end.

# Asynchronous I/O – Writing
## Write Example
```cs
public async Task SimpleWriteAsync() {
    string filePath = "simple.txt";
    string text = $"Hello World";

    await File.WriteAllTextAsync(filePath, text);
}
```

## Fine Control
For fine control, use the `FileStream` class with `options=FileOptions.Asynchronous` or `useAsync: true` in the constructor call instead of using `File.WriteAllTextAsync/File.ReadAllTextAsync`.
- This causes asynchronous I/O to occur at the OS level, which avoids blocking a thread pool thread.

If using `StreamReader` or `StreamWriter`, provide a `Stream` that `FileStream` opened.
```cs
public async Task ProcessWriteAsync() {
    string filePath = "temp.txt";
    string text = $"Hello World{Environment.NewLine}";

    await WriteTextAsync(filePath, text);
}

async Task WriteTextAsync(string filePath, string text) {
    byte[] encodedText = Encoding.Unicode.GetBytes(text);

    using var sourceStream =
        new FileStream(
            filePath,
            FileMode.Create, FileAccess.Write, FileShare.None,
            bufferSize: 4096, useAsync: true);

    await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
}
```

# Asynchronous I/O – Reading
## Read Example
```cs
public async Task SimpleReadAsync() {
    string filePath = "simple.txt";
    string text = await File.ReadAllTextAsync(filePath);

    Console.WriteLine(text);
}
```

## Fine Control
```cs
public async Task ProcessReadAsync() {
    try {
        string filePath = "temp.txt";
        if (File.Exists(filePath) != false) {
            string text = await ReadTextAsync(filePath);
            Console.WriteLine(text);
        }
        else {
            Console.WriteLine($"file not found: {filePath}");
        }
    } catch (Exception ex) {
        Console.WriteLine(ex.Message);
    }
}

async Task<string> ReadTextAsync(string filePath) {
    using var sourceStream =
        new FileStream(
            filePath,
            FileMode.Open, FileAccess.Read, FileShare.Read,
            bufferSize: 4096, useAsync: true);

    var sb = new StringBuilder();

    byte[] buffer = new byte[0x1000];
    int numRead;
    // Here, ReadAsync returns a Task<Int32>, so the await evaluation produces an Int32 value stored in numRead:
    while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0) {
        string text = Encoding.Unicode.GetString(buffer, 0, numRead);
        sb.Append(text);
    }

    return sb.ToString();
}
```
