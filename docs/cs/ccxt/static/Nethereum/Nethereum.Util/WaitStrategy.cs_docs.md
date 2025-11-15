# Documentation: cs/ccxt/static/Nethereum/Nethereum.Util/WaitStrategy.cs

## File Metadata

- **Path**: `cs/ccxt/static/Nethereum/Nethereum.Util/WaitStrategy.cs`
- **Size**: 474 bytes
- **Lines**: 19
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System.Linq;
using System.Threading.Tasks;

namespace Nethereum.Util
{
#if !NET35
    public class WaitStrategy : IWaitStrategy
    {
        private static readonly int[] WaitIntervals = {1000, 2000, 5000, 10000, 15000};

        public Task ApplyAsync(uint retryCount)
        {
            var intervalMs = retryCount >= WaitIntervals.Length ? WaitIntervals.Last() : WaitIntervals[retryCount];

            return Task.Delay(intervalMs);
        }
    }
#endif
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Nethereum/Nethereum.Util/WaitStrategy.cs`.

**Classes defined**: WaitStrategy



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 14
- Comment lines: 2
- Blank lines: 3

### Main Components

**Classes** (1):
- `WaitStrategy`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

