---
title: pipewriter
date: 2023-11-08T00:00:00-06:00
draft: false
weight: 1
---

# Overview
`PipeWriter` manages buffers for writing on the caller's behalf. It implements `IBufferWriter<byte>` to get access to buffers to perform
writes without extra buffer copies:

```cs
async Task WriteHelloAsync(PipeWriter writer, CancellationToken cancellationToken = default)
{
    // Request a buffer of at least 5 bytes from the PipeWriter.
    Memory<byte> memory = writer.GetMemory(5);

    // Write directly into the buffer.
    int written = Encoding.ASCII.GetBytes("Hello".AsSpan(), memory.Span);

    // Tell the writer how many bytes were written.
    writer.Advance(written);

    // Send the bytes to the underlying device.
    await writer.FlushAsync(cancellationToken);
}
```

Using `PipeWriter.WriteAsync` instead of the buffers provided by `PipeWriter` is easier. `WriteAsync` calls `GetSpan` and `Advance` as needed
and finishes by calling `FlushAsync`:
```cs
async Task WriteHelloAsync(PipeWriter writer, CancellationToken cancellationToken = default)
{
    byte[] helloBytes = Encoding.ASCII.GetBytes("Hello");

    // Write helloBytes to the writer; there's no need to call Advance here (Write does that).
    await writer.WriteAsync(helloBytes, cancellationToken);
}
```

# Cancellation with PipeWriter
`PipeWriter.FlushAsync` accepts a `CancellationToken`. However, `PipeWriter.CancelPendingFlush` cancels the flush operation without raising
an exception. It causes the current or next call to `FlushAsync` or `WriteAsync` to return a `FlushResult` with `IsCanceled` set to `true`.

# Common Problems with PipeWriter
See [this page](https://learn.microsoft.com/en-us/dotnet/standard/io/pipelines#pipewriter-common-problems) for more information.