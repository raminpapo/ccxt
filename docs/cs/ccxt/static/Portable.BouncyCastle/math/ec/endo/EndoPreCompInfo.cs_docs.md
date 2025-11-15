# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/EndoPreCompInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/EndoPreCompInfo.cs`
- **Size**: 582 bytes
- **Lines**: 27
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Math.EC.Multiplier;

namespace Org.BouncyCastle.Math.EC.Endo
{
    public class EndoPreCompInfo
        : PreCompInfo
    {
        protected ECEndomorphism m_endomorphism;

        protected ECPoint m_mappedPoint;

        public virtual ECEndomorphism Endomorphism
        {
            get { return m_endomorphism; }
            set { this.m_endomorphism = value; }
        }

        public virtual ECPoint MappedPoint
        {
            get { return m_mappedPoint; }
            set { this.m_mappedPoint = value; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/EndoPreCompInfo.cs`.

**Classes defined**: EndoPreCompInfo



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 21
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `EndoPreCompInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

