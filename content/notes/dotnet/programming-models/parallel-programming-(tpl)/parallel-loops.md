---
title: parallel loops
ate: 2023-02-16T15:06:39-0700
draft: false
weight: 1
---
# `Parallel.For`
Note: Use `Interlocked` to execute atomic operations which will avoid multiple threads modifying a variable simultaneously.

`Parallel.For`
- Returns a `System.Threading.Tasks.ParallelLoopResult` object that includes information such as last iteration completed
- Throws `System.AggregateException` if one or more exceptions occur on the threads.
```cs
long totalSize = 0;
string[] files = Directory.GetFiles(path);


var result = Parallel.For(0, // The starting element index
    files.Length, // The ending element index
    // An `Action<int>` delegate that takes the current iteration (supplied by the runtime) as its value
    index => 
    {
        FileInfo fi = new(files[index]);
        long size = fi.Length;
        Interlocked.Add(ref totalSize, size);
    });
```
# `Parallel.ForEach`
Example
```cs
var primeNumbers = new ConcurrentBag<int>();

Parallel.ForEach(numbers, number =>
{
    if (isPrime(number))
    primeNumbers.Add(number);
});
```
To use `Parallel.ForEach` with a non-generic collection, use `Enumerable.Cast` to convert the collection to generic:
```cs
Parallel.ForEach(somenon-genericCollection.Cast<object>(), currentElement =>
{
    // …
});
```
# `Parallel.ForEachAsync`
Example:
```cs
public class GitHubUser
{
    public string Name { get; set; }
    public string Bio { get; set; }
}

var userHandlers = new[] { "users/okyrylchuk", "users/shanselman", "users/jaredpar", "users/davidfowl" };

using HttpClient client = new() { BaseAddress = new Uri("api.github.com") };

client.DefaultRequestHeaders.UserAgent.Add(new ProductInfoHeaderValue("DotNet", "6"));

ParallelOptions parallelOptions = new() { MaxDegreeOfParallelism = 3 };

await Parallel.ForEachAsync(userHandlers, parallelOptions, async (uri, token) =>
{
    var user = await client.GetFromJsonAsync<GitHubUser>(uri, token);
    Console.WriteLine($"Name: {user.Name}\nBio: {user.Bio}\n");
});
```
