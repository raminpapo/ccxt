# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeAEndomorphism.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeAEndomorphism.cs`
- **Size**: 1,145 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Math.EC.Endo
{
    public class GlvTypeAEndomorphism
        :   GlvEndomorphism
    {
        protected readonly GlvTypeAParameters m_parameters;
        protected readonly ECPointMap m_pointMap;

        public GlvTypeAEndomorphism(ECCurve curve, GlvTypeAParameters parameters)
        {
            /*
             * NOTE: 'curve' MUST only be used to create a suitable ECFieldElement. Due to the way
             * ECCurve configuration works, 'curve' will not be the actual instance of ECCurve that the
             * endomorphism is being used with.
             */

            this.m_parameters = parameters;
            this.m_pointMap = new ScaleYNegateXPointMap(curve.FromBigInteger(parameters.I));
        }

        public virtual BigInteger[] DecomposeScalar(BigInteger k)
        {
            return EndoUtilities.DecomposeScalar(m_parameters.SplitParams, k);
        }

        public virtual ECPointMap PointMap
        {
            get { return m_pointMap; }
        }

        public virtual bool HasEfficientPointMap
        {
            get { return true; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/GlvTypeAEndomorphism.cs`.

**Classes defined**: GlvTypeAEndomorphism

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 32
- Comment lines: 5
- Blank lines: 2

### Main Components

**Classes** (1):
- `GlvTypeAEndomorphism`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

