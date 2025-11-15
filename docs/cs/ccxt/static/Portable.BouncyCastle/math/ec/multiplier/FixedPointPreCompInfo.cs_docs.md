# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/FixedPointPreCompInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/FixedPointPreCompInfo.cs`
- **Size**: 1,141 bytes
- **Lines**: 44
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC.Multiplier
{
    /**
     * Class holding precomputation data for fixed-point multiplications.
     */
    public class FixedPointPreCompInfo
        : PreCompInfo
    {
        protected ECPoint m_offset = null;

        /**
         * Lookup table for the precomputed <code>ECPoint</code>s used for a fixed point multiplication.
         */
        protected ECLookupTable m_lookupTable = null;

        /**
         * The width used for the precomputation. If a larger width precomputation
         * is already available this may be larger than was requested, so calling
         * code should refer to the actual width.
         */
        protected int m_width = -1;

        public virtual ECLookupTable LookupTable
        {
            get { return m_lookupTable; }
            set { this.m_lookupTable = value; }
        }

        public virtual ECPoint Offset
        {
			get { return m_offset; }
			set { this.m_offset = value; }
		}

        public virtual int Width
        {
            get { return m_width; }
            set { this.m_width = value; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/FixedPointPreCompInfo.cs`.

**Classes defined**: FixedPointPreCompInfo

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 37
- Comment lines: 11
- Blank lines: -4

### Main Components

**Classes** (1):
- `FixedPointPreCompInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

