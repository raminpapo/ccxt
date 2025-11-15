# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaParameters.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaParameters.cs`
- **Size**: 1,660 bytes
- **Lines**: 86
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Math;

namespace Org.BouncyCastle.Crypto.Parameters
{
    public class DsaParameters
		: ICipherParameters
    {
        private readonly BigInteger p, q , g;
        private readonly DsaValidationParameters validation;

		public DsaParameters(
            BigInteger	p,
            BigInteger	q,
            BigInteger	g)
			: this(p, q, g, null)
        {
        }

		public DsaParameters(
            BigInteger				p,
            BigInteger				q,
            BigInteger				g,
            DsaValidationParameters	parameters)
        {
			if (p == null)
				throw new ArgumentNullException("p");
			if (q == null)
				throw new ArgumentNullException("q");
			if (g == null)
				throw new ArgumentNullException("g");

			this.p = p;
            this.q = q;
			this.g = g;
			this.validation = parameters;
        }

        public BigInteger P
        {
            get { return p; }
        }

		public BigInteger Q
        {
            get { return q; }
        }

		public BigInteger G
        {
            get { return g; }
        }

		public DsaValidationParameters ValidationParameters
        {
			get { return validation; }
        }

		public override bool Equals(
			object obj)
        {
			if (obj == this)
				return true;

			DsaParameters other = obj as DsaParameters;

			if (other == null)
				return false;

			return Equals(other);
        }

		protected bool Equals(
			DsaParameters other)
		{
			return p.Equals(other.p) && q.Equals(other.q) && g.Equals(other.g);
		}

		public override int GetHashCode()
        {
			return p.GetHashCode() ^ q.GetHashCode() ^ g.GetHashCode();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/parameters/DsaParameters.cs`.

**Classes defined**: DsaParameters



## Detailed Walkthrough

### Code Structure

- Total lines: 86
- Code lines: 70
- Comment lines: 0
- Blank lines: 16

### Main Components

**Classes** (1):
- `DsaParameters`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

