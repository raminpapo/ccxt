# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECNamedDomainParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECNamedDomainParameters.cs`
- **Size**: 1,368 bytes
- **Lines**: 50
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

using Org.BouncyCastle.Asn1;
using Org.BouncyCastle.Asn1.X9;
using Org.BouncyCastle.Math;
using Org.BouncyCastle.Math.EC;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class ECNamedDomainParameters
        : ECDomainParameters
    {
        private readonly DerObjectIdentifier name;

        public DerObjectIdentifier Name
        {
            get { return name; }
        }

        public ECNamedDomainParameters(DerObjectIdentifier name, ECDomainParameters dp)
            : this(name, dp.Curve, dp.G, dp.N, dp.H, dp.GetSeed())
        {
        }

        public ECNamedDomainParameters(DerObjectIdentifier name, X9ECParameters x9)
            : base(x9)
        {
            this.name = name;
        }

        public ECNamedDomainParameters(DerObjectIdentifier name, ECCurve curve, ECPoint g, BigInteger n)
            : base(curve, g, n)
        {
            this.name = name;
        }

        public ECNamedDomainParameters(DerObjectIdentifier name, ECCurve curve, ECPoint g, BigInteger n, BigInteger h)
            : base(curve, g, n, h)
        {
            this.name = name;
        }

        public ECNamedDomainParameters(DerObjectIdentifier name, ECCurve curve, ECPoint g, BigInteger n, BigInteger h, byte[] seed)
            : base(curve, g, n, h, seed)
        {
            this.name = name;
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECNamedDomainParameters.cs`.

**Classes defined**: ECNamedDomainParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 41
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `ECNamedDomainParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

