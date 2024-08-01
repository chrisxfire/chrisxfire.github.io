---
title: pipereader
date: 2023-11-08T00:00:00-06:00
draft: false
weight: 1
---

# Overview
`PipeReader` manages memory on the caller's behalf. 

**<o>Always</o> call `PipeReader.AdvanceTo` after calling `PipeReader.ReadAsync`**:
- `ReadAsync` returns a `ReadOnlySequence<byte>` that is only valid until the call to `AdvanceTo`.
- Using the return value *after* the call to `AdvanceTo` throws an exception.

`PipeReader.AdvanceTo` takes two `SequencePosition` arguments: one that marks how much data was *consumed*, and one that marks how much of the
buffer was *observed*. 

Consumed — When data is marked as *consumed*, the pipe returns the memory to the underlying buffer pool.  
Observed — When data is marked as *observed*, the next call to ReadAsync either:
1. won't return until there's more data written to the pipe (assuming all day was marked as observed).
2. return immediately with the observed *and* unobserved data (but not data already consumed).

# Patterns for Reading Data with PipeReader
For examples below, consider this helper method:
```cs
bool TryParseLines(ref ReadOnlySequence<byte> buffer, out Message message);
```

## Reading a Single Message
Read a single message from a `PipeReader` and return it to the caller:
```cs
async ValueTask<Message?> ReadSingleMessageAsync(PipeReader reader, CancellationToken cancellationToken = default)
{
    while (true)
    {
        ReadResult result = await reader.ReadAsync(cancellationToken);
        ReadOnlySequence<byte> buffer = result.Buffer;

        // In the event that no message is parsed successfully, mark consumed as nothing and examined as the entire buffer.
        SequencePosition consumed = buffer.Start;
        SequencePosition examined = buffer.End;

        try
        {
            if (TryParseLines(ref buffer, out Message message))
            {
                // A single message was successfully parsed so mark the start of the parsed buffer as consumed. 
                // TryParseLines trims the buffer to point to the data after the message was parsed.
                consumed = buffer.Start;

                // Examined is marked the same as consumed here, so the next call to ReadSingleMessageAsync will 
                // process the next message if there is one.
                examined = consumed;

                return message;
            }

            // There's no more data to be processed.
            if (result.IsCompleted)
            {
                if (buffer.Length > 0)
                {
                    // The message is incomplete and there's no more data to process.
                    throw new InvalidDataException("Incomplete message.");
                }

                break;
            }
        }
        finally
        {
            reader.AdvanceTo(consumed, examined);
        }
    }

    return null;
}
```

## Reading Multiple Messages
Read all messages from a `PipeReader` and call `ProcessMessageAsync` on each:
```cs
async Task ProcessMessagesAsync(PipeReader reader, CancellationToken cancellationToken = default)
{
    try
    {
        while (true)
        {
            ReadResult result = await reader.ReadAsync(cancellationToken);
            ReadOnlySequence<byte> buffer = result.Buffer;

            try
            {
                // Process all messages from the buffer, modifying the input buffer on each iteration.
                while (TryParseLines(ref buffer, out Message message))
                {
                    await ProcessMessageAsync(message);
                }

                // There's no more data to be processed.
                if (result.IsCompleted)
                {
                    if (buffer.Length > 0)
                    {
                        // The message is incomplete and there's no more data to process.
                        throw new InvalidDataException("Incomplete message.");
                    }
                    break;
                }
            }
            finally
            {
                // Since all messages in the buffer are being processed, you can use the
                // remaining buffer's Start and End position to determine consumed and examined.
                reader.AdvanceTo(buffer.Start, buffer.End);
            }
        }
    }
    finally
    {
        await reader.CompleteAsync();
    }
}
```

# Cancellation with PipeReader
`PipeReader.ReadAsync` accepts a `CancellationToken`. However, `PipeReader.CancelPendingRead` cancels the current read operation without throwing
an exception. It causes the current or next call to `ReadAsync` to return a `ReadResult` with `IsCanceled` set to `true`. to This approach may be favorable in some cases.

# Common Problems with PipeReader
See [this page](https://learn.microsoft.com/en-us/dotnet/standard/io/pipelines#pipereader-common-problems) for more information.