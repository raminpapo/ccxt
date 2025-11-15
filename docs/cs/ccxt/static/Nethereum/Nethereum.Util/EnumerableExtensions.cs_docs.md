# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/EnumerableExtensions.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/EnumerableExtensions.cs`
- **Size**: 788 bytes
- **Lines**: 35
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Collections.Generic;
using System.Linq;

namespace Nethereum.Util
{
    public static class EnumerableExtensions
    {
        public static IEnumerable<IEnumerable<T>> Batch<T>(
            this IEnumerable<T> source, int size)
        {
            T[] bucket = null;
            var count = 0;

            foreach (var item in source)
            {
                if (bucket == null)
                    bucket = new T[size];


                bucket[count++] = item;

                if (count != size)
                    continue;

                yield return bucket;

                bucket = null;
                count = 0;
            }

            if (bucket != null && count > 0)
                yield return bucket.Take(count).ToArray();
        }
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/EnumerableExtensions.cs`.

**Classes defined**: EnumerableExtensions



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 27
- Comment lines: 0
- Blank lines: 8

### Main Components

**Classes** (1):
- `EnumerableExtensions`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

