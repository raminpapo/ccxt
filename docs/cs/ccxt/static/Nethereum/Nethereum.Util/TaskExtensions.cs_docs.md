# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/TaskExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/TaskExtensions.cs`
- **Size**: 1,482 bytes
- **Lines**: 42
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Nethereum.Util
{
    /// <summary>
    /// https://stackoverflow.com/a/15136833/4993930
    /// </summary>
    public static class TaskExtensions
    {
#if !DOTNET35
        /// <summary>
        /// Enumerates a collection in parallel and calls an async method on each item. Useful for making 
        /// parallel async calls, e.g. independent web requests when the degree of parallelism needs to be
        /// limited.
        /// </summary>
        public static Task ForEachAsync<T>(this IEnumerable<T> source, int degreeOfParalellism, Func<T, Task> action)
        {
            return Task.WhenAll(Partitioner.Create(source).GetPartitions(degreeOfParalellism).Select(partition => Task.Run(async () =>
            {
                using (partition)
                    while (partition.MoveNext())
                        await action(partition.Current);
            })));
        }
        public static Task ForEachAsync<T>(this IEnumerable<T> source, Func<T, Task> action)
        {
            return Task.WhenAll(Partitioner.Create(source).GetPartitions(Environment.ProcessorCount).Select(partition => Task.Run(async () =>
            {
                using (partition)
                    while (partition.MoveNext())
                        await action(partition.Current);
            })));
        }
#endif
    }

}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/TaskExtensions.cs`.

**Classes defined**: TaskExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 29
- Comment lines: 10
- Blank lines: 3

### Main Components

**Classes** (1):
- `TaskExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

