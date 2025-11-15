# Documentation: cs/ccxt/static/Portable.BouncyCastle/util/collections/IStore.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/util/collections/IStore.cs`
- **Size**: 689 bytes
- **Lines**: 16
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Collections.Generic;

namespace Org.BouncyCastle.Utilities.Collections
{
    /// <summary>A generic interface describing a simple store of objects.</summary>
    /// <typeparam name="T">The covariant type of stored objects.</typeparam>
    public interface IStore<out T>
    {
        /// <summary>Enumerate the (possibly empty) collection of objects matched by the given selector.</summary>
        /// <param name="selector">The <see cref="ISelector{T}"/> used to select matching objects.</param>
        /// <returns>An <see cref="IEnumerable{T}"/> of the matching objects.</returns>
        IEnumerable<T> EnumerateMatches(ISelector<T> selector);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/util/collections/IStore.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 9
- Comment lines: 5
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

