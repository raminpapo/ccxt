# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECPrivateKeyParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECPrivateKeyParameters.cs`
- **Size**: 1,659 bytes
- **Lines**: 70
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;
using System.Globalization;

using Org.BouncyCastle.Asn1;
using Org.BouncyCastle.Math;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class ECPrivateKeyParameters
        : ECKeyParameters
    {
        private readonly BigInteger d;

        public ECPrivateKeyParameters(
            BigInteger			d,
            ECDomainParameters	parameters)
            : this("EC", d, parameters)
        {
        }

        public ECPrivateKeyParameters(
            string				algorithm,
            BigInteger			d,
            ECDomainParameters	parameters)
            : base(algorithm, true, parameters)
        {
            this.d = Parameters.ValidatePrivateScalar(d);
        }

        public ECPrivateKeyParameters(
            string				algorithm,
            BigInteger			d,
            DerObjectIdentifier publicKeyParamSet)
            : base(algorithm, true, publicKeyParamSet)
        {
            this.d = Parameters.ValidatePrivateScalar(d);
        }

        public BigInteger D
        {
            get { return d; }
        }

        public override bool Equals(
            object obj)
        {
            if (obj == this)
                return true;

            ECPrivateKeyParameters other = obj as ECPrivateKeyParameters;

            if (other == null)
                return false;

            return Equals(other);
        }

        protected bool Equals(
            ECPrivateKeyParameters other)
        {
            return d.Equals(other.d) && base.Equals(other);
        }

        public override int GetHashCode()
        {
            return d.GetHashCode() ^ base.GetHashCode();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/ECPrivateKeyParameters.cs`.

**Classes defined**: ECPrivateKeyParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 70
- Code lines: 57
- Comment lines: 0
- Blank lines: 13

### Main Components

**Classes** (1):
- `ECPrivateKeyParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

