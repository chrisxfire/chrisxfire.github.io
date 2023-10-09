---
title: processing tasks
date: 2022-11-23T10:36:13-0700
draft: false
weight: 1
---

# Processing Tasks as They Complete
> Documentation: https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/start-multiple-async-tasks-and-process-them-as-they-complete

`Task.WhenAny` allows for starting multiple tasks at the same time and processing them one by one in the
order in which they complete instead of the order in which they are started.

```cs
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery = from url in s_urlList
                                                select ProcessUrlAsync(url, s_client);

    // Start each Task since LINQ uses deferred execution otherwise:
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;

    while (downloadTasks.Any())
    {
        // Hold the next Task that finishes:
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);

        downloadTasks.Remove(finishedTask); // Remove that Task from the list
        
        total += await finishedTask; // Unwrap the int from the Task, or, if faulted, throw the first child Exception
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned: {total:#,#}");
    Console.WriteLine($"Elapsed time: {stopwatch.Elapsed}\n");
}
```

# See Also
https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/