# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/collections/StoreImpl.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/collections/StoreImpl.cs`
- **Size**: 609 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;

namespace Org.BouncyCastle.Utilities.Collections
{
    internal sealed class StoreImpl<T>
        : IStore<T>
    {
        private readonly List<T> m_contents;

        internal StoreImpl(IEnumerable<T> e)
        {
            m_contents = new List<T>(e);
        }

        IEnumerable<T> IStore<T>.EnumerateMatches(ISelector<T> selector)
        {
            foreach (T candidate in m_contents)
            {
                if (selector == null || selector.Match(candidate))
                    yield return candidate;
            }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/collections/StoreImpl.cs`.

**Classes defined**: StoreImpl



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 22
- Comment lines: 0
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

