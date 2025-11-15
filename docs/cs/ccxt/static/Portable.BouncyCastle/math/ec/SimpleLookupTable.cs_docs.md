# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/SimpleLookupTable.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/SimpleLookupTable.cs`
- **Size**: 963 bytes
- **Lines**: 41
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC
{
    public class SimpleLookupTable
        : AbstractECLookupTable
    {
        private static ECPoint[] Copy(ECPoint[] points, int off, int len)
        {
            ECPoint[] result = new ECPoint[len];
            for (int i = 0; i < len; ++i)
            {
                result[i] = points[off + i];
            }
            return result;
        }

        private readonly ECPoint[] points;

        public SimpleLookupTable(ECPoint[] points, int off, int len)
        {
            this.points = Copy(points, off, len);
        }

        public override int Size
        {
            get { return points.Length; }
        }

        public override ECPoint Lookup(int index)
        {
            throw new NotSupportedException("Constant-time lookup not supported");
        }

        public override ECPoint LookupVar(int index)
        {
            return points[index];
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/SimpleLookupTable.cs`.

**Classes defined**: SimpleLookupTable



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 34
- Comment lines: 0
- Blank lines: 7

### Main Components

**Classes** (1):
- `SimpleLookupTable`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

