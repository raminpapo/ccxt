# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/GlvMultiplier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/GlvMultiplier.cs`
- **Size**: 1,269 bytes
- **Lines**: 42
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Math.EC.Endo;

namespace Org.BouncyCastle.Math.EC.Multiplier
{
    public class GlvMultiplier
        :   AbstractECMultiplier
    {
        protected readonly ECCurve curve;
        protected readonly GlvEndomorphism glvEndomorphism;

        public GlvMultiplier(ECCurve curve, GlvEndomorphism glvEndomorphism)
        {
            if (curve == null || curve.Order == null)
                throw new ArgumentException("Need curve with known group order", "curve");

            this.curve = curve;
            this.glvEndomorphism = glvEndomorphism;
        }

        protected override ECPoint MultiplyPositive(ECPoint p, BigInteger k)
        {
            if (!curve.Equals(p.Curve))
                throw new InvalidOperationException();

            BigInteger n = p.Curve.Order;
            BigInteger[] ab = glvEndomorphism.DecomposeScalar(k.Mod(n));
            BigInteger a = ab[0], b = ab[1];

            if (glvEndomorphism.HasEfficientPointMap)
            {
                return ECAlgorithms.ImplShamirsTrickWNaf(glvEndomorphism, p, a, b);
            }

            ECPoint q = EndoUtilities.MapPoint(glvEndomorphism, p);

            return ECAlgorithms.ImplShamirsTrickWNaf(p, a, q, b);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/GlvMultiplier.cs`.

**Classes defined**: GlvMultiplier



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 32
- Comment lines: 0
- Blank lines: 10

### Main Components

**Classes** (1):
- `GlvMultiplier`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

