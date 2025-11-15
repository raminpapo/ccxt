# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPrivateKeyParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPrivateKeyParameters.cs`
- **Size**: 976 bytes
- **Lines**: 54
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Math;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class DsaPrivateKeyParameters
		: DsaKeyParameters
    {
        private readonly BigInteger x;

		public DsaPrivateKeyParameters(
            BigInteger		x,
            DsaParameters	parameters)
			: base(true, parameters)
        {
			if (x == null)
				throw new ArgumentNullException("x");

			this.x = x;
        }

		public BigInteger X
        {
            get { return x; }
        }

		public override bool Equals(
			object obj)
        {
			if (obj == this)
				return true;

			DsaPrivateKeyParameters other = obj as DsaPrivateKeyParameters;

			if (other == null)
				return false;

			return Equals(other);
        }

		protected bool Equals(
			DsaPrivateKeyParameters other)
		{
			return x.Equals(other.x) && base.Equals(other);
		}

		public override int GetHashCode()
        {
            return x.GetHashCode() ^ base.GetHashCode();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaPrivateKeyParameters.cs`.

**Classes defined**: DsaPrivateKeyParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 42
- Comment lines: 0
- Blank lines: 12

### Main Components

**Classes** (1):
- `DsaPrivateKeyParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

