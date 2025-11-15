# Documentation: cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/ScalarSplitParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/ScalarSplitParameters.cs`
- **Size**: 1,635 bytes
- **Lines**: 70
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Math;

namespace Org.BouncyCastle.Math.EC.Endo
{
    public class ScalarSplitParameters
    {
        private static void CheckVector(BigInteger[] v, string name)
        {
            if (v == null || v.Length != 2 || v[0] == null || v[1] == null)
                throw new ArgumentException("Must consist of exactly 2 (non-null) values", name);
        }

        protected readonly BigInteger m_v1A, m_v1B, m_v2A, m_v2B;
        protected readonly BigInteger m_g1, m_g2;
        protected readonly int m_bits;

        public ScalarSplitParameters(BigInteger[] v1, BigInteger[] v2, BigInteger g1,
            BigInteger g2, int bits)
        {
            CheckVector(v1, "v1");
            CheckVector(v2, "v2");

            this.m_v1A = v1[0];
            this.m_v1B = v1[1];
            this.m_v2A = v2[0];
            this.m_v2B = v2[1];
            this.m_g1 = g1;
            this.m_g2 = g2;
            this.m_bits = bits;
        }

        public virtual BigInteger V1A
        {
            get { return m_v1A; }
        }

        public virtual BigInteger V1B
        {
            get { return m_v1B; }
        }

        public virtual BigInteger V2A
        {
            get { return m_v2A; }
        }

        public virtual BigInteger V2B
        {
            get { return m_v2B; }
        }

        public virtual BigInteger G1
        {
            get { return m_g1; }
        }

        public virtual BigInteger G2
        {
            get { return m_g2; }
        }

        public virtual int Bits
        {
            get { return m_bits; }
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/math/ec/endo/ScalarSplitParameters.cs`.

**Classes defined**: ScalarSplitParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 57
- Comment lines: 0
- Blank lines: 13

### Main Components

**Classes** (1):
- `ScalarSplitParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

