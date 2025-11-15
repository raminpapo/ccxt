# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHPublicKey.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHPublicKey.cs`
- **Size**: 869 bytes
- **Lines**: 47
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X9
{
	public class DHPublicKey
		: Asn1Encodable
	{
		private readonly DerInteger y;

		public static DHPublicKey GetInstance(Asn1TaggedObject obj, bool isExplicit)
		{
			return GetInstance(DerInteger.GetInstance(obj, isExplicit));
		}

		public static DHPublicKey GetInstance(object obj)
		{
			if (obj == null || obj is DHPublicKey)
				return (DHPublicKey)obj;

			if (obj is DerInteger)
				return new DHPublicKey((DerInteger)obj);

			throw new ArgumentException("Invalid DHPublicKey: " + Platform.GetTypeName(obj), "obj");
		}

		public DHPublicKey(DerInteger y)
		{
			if (y == null)
				throw new ArgumentNullException("y");

			this.y = y;
		}

		public DerInteger Y
		{
			get { return this.y; }
		}

		public override Asn1Object ToAsn1Object()
		{
			return this.y;
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHPublicKey.cs`.

**Classes defined**: DHPublicKey



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 36
- Comment lines: 0
- Blank lines: 11

### Main Components

**Classes** (1):
- `DHPublicKey`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

