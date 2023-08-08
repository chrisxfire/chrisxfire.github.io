---
title: processing tasks
date: 2022-11-23T10:36:13-0700
draft: false
weight: 1
---
# Processing Tasks as They Complete
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
