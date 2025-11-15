# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/AbstractECMultiplier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/AbstractECMultiplier.cs`
- **Size**: 942 bytes
- **Lines**: 30
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Org.BouncyCastle.Math.EC.Multiplier
{
    public abstract class AbstractECMultiplier
        : ECMultiplier
    {
        public virtual ECPoint Multiply(ECPoint p, BigInteger k)
        {
            int sign = k.SignValue;
            if (sign == 0 || p.IsInfinity)
                return p.Curve.Infinity;

            ECPoint positive = MultiplyPositive(p, k.Abs());
            ECPoint result = sign > 0 ? positive : positive.Negate();

            /*
             * Although the various multipliers ought not to produce invalid output under normal
             * circumstances, a final check here is advised to guard against fault attacks.
             */
            return CheckResult(result);
        }

        protected abstract ECPoint MultiplyPositive(ECPoint p, BigInteger k);

        protected virtual ECPoint CheckResult(ECPoint p)
        {
            return ECAlgorithms.ImplCheckResult(p);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/multiplier/AbstractECMultiplier.cs`.

**Classes defined**: AbstractECMultiplier

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 25
- Comment lines: 4
- Blank lines: 1

### Main Components

**Classes** (1):
- `AbstractECMultiplier`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

