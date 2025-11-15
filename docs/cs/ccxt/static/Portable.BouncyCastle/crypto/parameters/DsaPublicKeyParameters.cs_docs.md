# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPublicKeyParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPublicKeyParameters.cs`
- **Size**: 1,614 bytes
- **Lines**: 69
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Math;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class DsaPublicKeyParameters
		: DsaKeyParameters
    {
        private static BigInteger Validate(BigInteger y, DsaParameters parameters)
        {
            // we can't validate without params, fortunately we can't use the key either...
            if (parameters != null)
            {
                if (y.CompareTo(BigInteger.Two) < 0
                    || y.CompareTo(parameters.P.Subtract(BigInteger.Two)) > 0
                    || !y.ModPow(parameters.Q, parameters.P).Equals(BigInteger.One))
                {
                    throw new ArgumentException("y value does not appear to be in correct group");
                }
            }

            return y;
        }

        private readonly BigInteger y;

		public DsaPublicKeyParameters(
            BigInteger		y,
            DsaParameters	parameters)
			: base(false, parameters)
        {
			if (y == null)
				throw new ArgumentNullException("y");

			this.y = Validate(y, parameters);
        }

		public BigInteger Y
        {
            get { return y; }
        }

		public override bool Equals(object obj)
        {
			if (obj == this)
				return true;

			DsaPublicKeyParameters other = obj as DsaPublicKeyParameters;

			if (other == null)
				return false;

			return Equals(other);
        }

		protected bool Equals(
			DsaPublicKeyParameters other)
		{
			return y.Equals(other.y) && base.Equals(other);
		}

		public override int GetHashCode()
        {
			return y.GetHashCode() ^ base.GetHashCode();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPublicKeyParameters.cs`.

**Classes defined**: DsaPublicKeyParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 54
- Comment lines: 1
- Blank lines: 14

### Main Components

**Classes** (1):
- `DsaPublicKeyParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

