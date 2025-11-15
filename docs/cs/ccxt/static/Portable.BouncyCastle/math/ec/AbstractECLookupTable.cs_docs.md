# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/AbstractECLookupTable.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/AbstractECLookupTable.cs`
- **Size**: 341 bytes
- **Lines**: 17
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC
{
    public abstract class AbstractECLookupTable
        : ECLookupTable
    {
        public abstract ECPoint Lookup(int index);
        public abstract int Size { get; }

        public virtual ECPoint LookupVar(int index)
        {
            return Lookup(index);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/AbstractECLookupTable.cs`.

**Classes defined**: AbstractECLookupTable



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
- Comment lines: 0
- Blank lines: 3

### Main Components

**Classes** (1):
- `AbstractECLookupTable`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

