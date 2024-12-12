---
title: thread local and partition local variables
date: 2023-02-16T15:07:11-0700
draft: false
weight: 1
---

# Thread-Local Variables
Stores and retrieves *state* in each separate task that is created by a `Parallel.For` loop. Instead of writing to a shared resource on each iteration, you compute and store the value until all iterations for the task are complete.

# Parallel.For w/Thread-Local Variables
Example
```cs
int[] nums = Enumerable.Range(0, 1_000_000).ToArray();
long total = 0;

Parallel.For<long>( // By default, the type parameter would be int, so this makes it `long`
    0, // Starting element index
    nums.Length, // Ending element index
    () => 0, // Initialize a thread-local variable to 0. Variable is of type `long`.
    ( // The logic loop of type `Func<Int, ParallelLoopState, long, long>` as a delegate or lambda.
        j, // Loop counter for current iteration
        loop, // a ParallelLoopState object (provided by TPL) that can be used to break out of the loop
        subtotal // a thread-local variable (provided by the runtime)
    ) =>
    {
        subtotal + nums[j]
        return subtotal;
    },
    (x) => Interlocked.Add(ref total, x);
);
```
# Partition-Local Variables
Similar to a thread-local variable except that multiple partitions can run on a single thread and is created by a `Parallel.ForEach` loop.

Example
```cs
int[] nums = Enumerable.Range(0, 1_000_000).ToArray();
long total = 0;

Parallel.ForEach<int, long>( // int = type of source elements, long = type of thread-local variable
    nums, // source collection
    () => 0, // initialize a thread-local variable (of type long) to 0
    (j, loop, subtotal) => // the logic loop (explained above)
    {
        subttoal += j; // modify the local variable
        return subtotal; // value to be passed to next iteration
    },
    (finalResult) => // the final value of subtotal for a particular partition
        Interlocked.Add(ref total, finalResult) // method to execute when each partition completes
);
```
