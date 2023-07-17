---
title: notes > .net > programming models > parallel programming > parallel invoke
date: 2023-02-17T09:58:06-0700
draft: false
weight: 1
---
Overview
Use `Parallel.Invoke` to execute operations in parallel on a data source.
The runtime handles scheduling and scales automatically to the number of cores on the host.
Warning: None of the operations must modify the data source (risk of race condition).
```cs
string words[] = // some array of words here

Parallel.Invoke(() =>
    {
        GetLongestWord(words);
    },
    () =>
        {
            GetMostCommonWords(words);
        },
        {
            GetCountForWrod(words, "booger");
        },
    …
); // close Parallel.Invoke
```
