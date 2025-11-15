# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/Tables64kGcmMultiplier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/Tables64kGcmMultiplier.cs`
- **Size**: 2,186 bytes
- **Lines**: 81
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Crypto.Utilities;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Crypto.Modes.Gcm
{
    public class Tables64kGcmMultiplier
        : IGcmMultiplier
    {
        private byte[] H;
        private GcmUtilities.FieldElement[][] T;

        public void Init(byte[] H)
        {
            if (T == null)
            {
                T = new GcmUtilities.FieldElement[16][];
            }
            else if (Arrays.AreEqual(this.H, H))
            {
                return;
            }

            this.H = Arrays.Clone(H);

            for (int i = 0; i < 16; ++i)
            {
                GcmUtilities.FieldElement[] t = T[i] = new GcmUtilities.FieldElement[256];

                // t[0] = 0

                if (i == 0)
                {
                    // t[1] = H.p^7
                    GcmUtilities.AsFieldElement(this.H, out t[1]);
                    GcmUtilities.MultiplyP7(ref t[1]);
                }
                else
                {
                    // t[1] = T[i-1][1].p^8
                    GcmUtilities.MultiplyP8(ref T[i - 1][1], out t[1]);
                }

                for (int n = 1; n < 128; ++n)
                {
                    // t[2.n] = t[n].p^-1
                    GcmUtilities.DivideP(ref t[n], out t[n << 1]);

                    // t[2.n + 1] = t[2.n] + t[1]
                    GcmUtilities.Xor(ref t[n << 1], ref t[1], out t[(n << 1) + 1]);
                }
            }
        }

        public void MultiplyH(byte[] x)
        {
            //GcmUtilities.FieldElement z = T[15][x[15]];
            //for (int i = 14; i >= 0; --i)
            //{
            //    GcmUtilities.Xor(ref z, ref T[i][x[i]]);
            //}
            //GcmUtilities.AsBytes(ref z, x);

            GcmUtilities.FieldElement[] t = T[15];
            int tPos = x[15];
            ulong z0 = t[tPos].n0, z1 = t[tPos].n1;

            for (int i = 14; i >= 0; --i)
            {
                t = T[i];
                tPos = x[i];
                z0 ^= t[tPos].n0;
                z1 ^= t[tPos].n1;
            }

            GcmUtilities.AsBytes(z0, z1, x);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/modes/gcm/Tables64kGcmMultiplier.cs`.

**Classes defined**: Tables64kGcmMultiplier



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 56
- Comment lines: 11
- Blank lines: 14

### Main Components

**Classes** (1):
- `Tables64kGcmMultiplier`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

