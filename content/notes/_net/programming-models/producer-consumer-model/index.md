---
title: producer-consumer model
date: 2023-07-15T00:00:00-06:00
draft: false
weight: 1
---

# Overview
- Channels, from the `System.Threading.Channels` namespace, are an implementation of the producer/consumer model in .NET.  
- This namespace provides synchronization data structures for passing data between producers and consumers asynchronously.
- Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/channels 

# Channels
Channels can be thought of as any other common generic collection type such as `List<T>`. This collection manages synchronization and provides various 
consumption models through factory creation options.

Depending on how a `Channel<T>` is created, its reader and writer behave differently.  
- <o>Regardless of how it is created, a channel will always throw a `ChannelClosedException` if it is used after it has been closed.</o>
- Whenever a `Channel<TWrite,TRead>.Writer` produces faster than a `Channel<TWrite,TRead>.Reader` can consume, the channel experiences *back pressure*.

# Bounding
To create a channel that specifies at maximum capacity, call `Channel.CreateBounded`. Optionally, include `BoundedChannelOptions`.
To create a channel that is used by any number of readers and writers concurrently, call `Channel.CreateUnbounded`. Optionally, include `UnboundedChannelOptions`.

## Unbounded Channels
The channel's capacity is unbounded and all writes are performed synchronously.  

### Creating
```cs
var channel = Channel.CreateUnbounded<T>();
```

### Example
Assume you're creating a solution for a GPS device to track the coordinates of a device over time:
```cs
public readonly record struct Coordinates (Guid DeviceId, double Latitude, double Longitude);


// Create an unbounded channel with multiple producers and consumers:
var channel = Channel.CreateUnbounded<Coordinates>(
    new UnboundedChannelOptions { 
        SingleWriter = false, 
        SingleReader = false, 
        AllowSynchronousContinuations = true 
    });
```

Since this channel is unbounded, it always has room for a write, so all writes are synchronous.

## Bounded Channels
When the bound is reached, the default behavior is that the channel asynchronously blocks the producer until space becomes available.  

### Creating
```cs
var channel = Channel.CreateBounded<T>(7);
```

### Full Mode Behavior
Specify the `BoundedChannelFullMode` value to determine how the channel behaves when its bound is reached.  
The default is `BoundedChannelFullMode.Wait` which waits for space to become available to complete the write operation.

### Example
Using the same example from above:
```cs
var channel = Channel.CreateBounded<Coordinates>(
    new BoundedChannelOptions(1_000)
    {
        SingleWriter = true, // one writer...
        SingleReader = false, // ...but many readers.
        AllowSynchronousContinuations = false,
        FullMode = BoundedChannelFullMode.DropWrite // drop the item being written if the channel is full
    });
```

To do something with the writes that are dropped, use an overload of CreateBounded that accepts a callback that gets invoked 
whenever the channel is full and a new item is added:
```cs
var channel = Channel.CreateBounded(
    new BoundedChannelOptions(10){
        AllowSynchronousContinuations = true,
        FullMOde = BoundedChannelFullMode.DropOldest
    },
    static void (Coordinates droppedCoords) =>
        Console.WriteLine($"Coordinates dropped: {droppedCoords}"));
```

# See Also
[An introduction to System.Threading.Channels](https://devblogs.microsoft.com/_net/an-introduction-to-system-threading-channels/)
