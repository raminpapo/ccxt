# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/PBEParameter.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/PBEParameter.cs`
- **Size**: 1,257 bytes
- **Lines**: 60
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Math;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.Pkcs
{
	public class PbeParameter
		: Asn1Encodable
	{
		private readonly Asn1OctetString	salt;
		private readonly DerInteger			iterationCount;

		public static PbeParameter GetInstance(object obj)
		{
			if (obj is PbeParameter || obj == null)
			{
				return (PbeParameter) obj;
			}

			if (obj is Asn1Sequence)
			{
				return new PbeParameter((Asn1Sequence) obj);
			}

			throw new ArgumentException("Unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

		private PbeParameter(Asn1Sequence seq)
		{
			if (seq.Count != 2)
				throw new ArgumentException("Wrong number of elements in sequence", "seq");

			salt = Asn1OctetString.GetInstance(seq[0]);
			iterationCount = DerInteger.GetInstance(seq[1]);
		}

		public PbeParameter(byte[] salt, int iterationCount)
		{
			this.salt = new DerOctetString(salt);
			this.iterationCount = new DerInteger(iterationCount);
		}

		public byte[] GetSalt()
		{
			return salt.GetOctets();
		}

		public BigInteger IterationCount
		{
			get { return iterationCount.Value; }
		}

		public override Asn1Object ToAsn1Object()
		{
			return new DerSequence(salt, iterationCount);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/PBEParameter.cs`.

**Classes defined**: PbeParameter



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 48
- Comment lines: 0
- Blank lines: 12

### Main Components

**Classes** (1):
- `PbeParameter`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

