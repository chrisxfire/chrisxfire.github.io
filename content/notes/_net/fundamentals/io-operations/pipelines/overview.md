---
title: pipelines
date: 2023-11-05T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/io/pipelines)]  

Pipelines are designed to simplify high performance I/O operations with .NET.

Pipelines are available in `System.IO.Pipelines` Nuget package.

# pipe
Pipe is used to create a `PipeReader`/`PipeWriter` pair, accessible via properties on the `Pipe`. All data written in the `PipeWriter` is available in the `PipeReader`:
```cs
var pipe = new Pipe();
PipeReader reader = pipe.Reader;
PipeWriter writer = pipe.Writer;
```

```cs
async Task ProcessLinesAsync(Socket socket)
{

    var pipe = new Pipe();
    Task writing = FillPipeAsync(socket, pipe.Writer);
    Task reading = ReadPipeAsync(pipe.Reader);

    await Task.WhenAll(reading, writing);
}

// Reads from the Socket and writes to the PipeWriter:
async Task FillPipeAsync(Socket socket, PipeWriter writer)
{
    const int minimumBufferSize = 512;

    while (true)
    {
        // Allocate at least 512 bytes of memory from the Writer:
        Memory<byte> memory = writer.GetMemory(minimumBufferSize);
        try
        {
            int bytesRead = await socket.ReceiveAsync(memory, SocketFlags.None);
            if (bytesRead == 0)
            {
                break;
            }
            // Tell the PipeWriter how much was read from the Socket and written to the buffer:
            writer.Advance(bytesRead);
        }
        catch (Exception ex)
        {
            LogError(ex);
            break;
        }

        // Make the data available to the PipeReader:
        FlushResult result = await writer.FlushAsync();

        if (result.IsCompleted)
        {
            break;
        }
    }

     // By completing PipeWriter, tell the PipeReader that there's no more data coming.
    await writer.CompleteAsync();
}

// Reads from the PipeReader:
async Task ReadPipeAsync(PipeReader reader)
{
    while (true)
    {
        ReadResult result = await reader.ReadAsync();
        // This buffer holds the data that was read:
        ReadOnlySequence<byte> buffer = result.Buffer;

        while (TryReadLine(ref buffer, out ReadOnlySequence<byte> line))
        {
            // Process the line.
            ProcessLine(line);
        }

        // Tell the PipeReader how much of the buffer has been consumed and examined:
        reader.AdvanceTo(buffer.Start, buffer.End);

        // True if EOF reached:
        if (result.IsCompleted)
        {
            break;
        }
    }

    // Mark the PipeReader as complete and release the allocated memory:
    await reader.CompleteAsync();
}

bool TryReadLine(ref ReadOnlySequence<byte> buffer, out ReadOnlySequence<byte> line)
{
    // Look for a EOL in the buffer.
    SequencePosition? position = buffer.PositionOf((byte)'\n');

    if (position == null)
    {
        line = default;
        return false;
    }

    // Skip the line + the \n.
    line = buffer.Slice(0, position.Value);
    buffer = buffer.Slice(buffer.GetPosition(1, position.Value));
    return true;
}
```

# pipereader and pipewriter
See [Notes on PipeReader](../pipereader) and [Notes on PipeWriter](../pipewriter).

## best practices for using pipereader and pipewriter
- Always complete the `PipeReader` and `PipeWriter` or throw an exception.
- Always call `PipeReader.AdvanceTo` and `PipeReader.ReadAsync`.
- Periodically `await` `PipeWriter.FlushAsync` while writing.
  - Always check `FlushResult.IsCompleted`.
    - Abort writing if `IsCompleted` is `true` (since the reader has completed and is no longer listening).
- Always call `PipeWriter.FlushAsync` after writing something you want the `PipeReader` to access.
- <r>Do not</r> call `FlushAsync` if the reader cannot start until `FlushAsync` finishes. This may cause a deadlock.
- <r>Do not</r> access `ReadResult.Buffer` after calling `AdvanceTo` or completing the `PipeReader.`
- <o>Caution</o>: These types are not thread safe.

# backpressure and flow control
When reading and parsing:
* The reading thread consumes data from the network and puts it in buffers.
* The parsing thread constructs data structures.

Parsing takes more time, so the reading thread gets ahead of the parsing thread, so it must either:
* Pause, or;
* Allocate more memory to store the data for the parsing thread.

This is *backpressure*.  

The `Pipe` has two settings that adjust flow control:
1. `PauseWriterThreshold` — determines how much data should be buffered before calls to `PipeWriter.FlushAsync` are paused.
2. `ResumeWriterThreshold` — determines how much data the reader has to consume before calls to `PipeWriter.FlushAsync` resume.

When the amount of data in the `Pipe` crosses the `PauseWriterThreshold`, `PipeWriter.FlushAsync` returns an incomplete `ValueTask<FlushResult>`.
When the amount of data becomes lower than `ResumeWriterThreshold`, `PipeWriter.FlushAsync` completes the `ValueTask<FlushResult>`.

## example
```cs
// The Pipe will start returning incomplete tasks from FlushAsync until the reader examines at least 5 bytes:
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

# pipescheduler
When using `async`/`await`, asynchronous code resumes on either a `TaskScheduler` or the current `SynchronizationContext`. 
`PipeScheduler` provides fine-grained control over where the asynchronous callbacks run.

By default, the `SynchronizationContext` is used. If there isn't one, the thread pool is used to run callbacks. In this second case,
`PipeScheduler.ThreadPool` is the PipeScheduler implementation that queues callbacks to the thread pool.

<o>Avoid using `PipeScheduler.Inline`</o>. This can cause deadlocks.

# iduplexpipe
`IDuplexPipe` is a contract for types that support both reading and writing, such as a network connection.

`IDuplexPipe` represents one side (reading or writing) of a full duplex connection. What is written to the `PipeWriter` will
not be read from the `PipeReader` of an `IDuplexPipe`.

# streams
See [this page](https://learn.microsoft.com/en-us/dotnet/standard/io/pipelines#streams) for more information on reading and writing streaming data.