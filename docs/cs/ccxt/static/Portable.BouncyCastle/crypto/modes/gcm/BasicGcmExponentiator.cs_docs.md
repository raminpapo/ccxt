# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/BasicGcmExponentiator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/BasicGcmExponentiator.cs`
- **Size**: 932 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Crypto.Modes.Gcm
{
    public class BasicGcmExponentiator
        : IGcmExponentiator
    {
        private GcmUtilities.FieldElement x;

        public void Init(byte[] x)
        {
            GcmUtilities.AsFieldElement(x, out this.x);
        }

        public void ExponentiateX(long pow, byte[] output)
        {
            GcmUtilities.FieldElement y;
            GcmUtilities.One(out y);

            if (pow > 0)
            {
                GcmUtilities.FieldElement powX = x;
                do
                {
                    if ((pow & 1L) != 0)
                    {
                        GcmUtilities.Multiply(ref y, ref powX);
                    }
                    GcmUtilities.Square(ref powX);
                    pow >>= 1;
                }
                while (pow > 0);
            }

            GcmUtilities.AsBytes(ref y, output);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/BasicGcmExponentiator.cs`.

**Classes defined**: BasicGcmExponentiator



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 33
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `BasicGcmExponentiator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

