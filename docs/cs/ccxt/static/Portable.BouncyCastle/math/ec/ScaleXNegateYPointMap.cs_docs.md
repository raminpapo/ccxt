# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/ScaleXNegateYPointMap.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/ScaleXNegateYPointMap.cs`
- **Size**: 400 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC
{
    public class ScaleXNegateYPointMap
        : ECPointMap
    {
        protected readonly ECFieldElement scale;

        public ScaleXNegateYPointMap(ECFieldElement scale)
        {
            this.scale = scale;
        }

        public virtual ECPoint Map(ECPoint p)
        {
            return p.ScaleXNegateY(scale);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/ScaleXNegateYPointMap.cs`.

**Classes defined**: ScaleXNegateYPointMap



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 17
- Comment lines: 0
- Blank lines: 4

### Main Components

**Classes** (1):
- `ScaleXNegateYPointMap`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

