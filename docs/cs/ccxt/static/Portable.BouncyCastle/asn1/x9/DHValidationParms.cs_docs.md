# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHValidationParms.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHValidationParms.cs`
- **Size**: 1,499 bytes
- **Lines**: 65
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X9
{
	public class DHValidationParms
		: Asn1Encodable
	{
		private readonly DerBitString seed;
		private readonly DerInteger pgenCounter;

		public static DHValidationParms GetInstance(Asn1TaggedObject obj, bool isExplicit)
		{
			return GetInstance(Asn1Sequence.GetInstance(obj, isExplicit));
		}

		public static DHValidationParms GetInstance(object obj)
		{
			if (obj == null || obj is DHValidationParms)
				return (DHValidationParms)obj;

			if (obj is Asn1Sequence)
				return new DHValidationParms((Asn1Sequence)obj);

			throw new ArgumentException("Invalid DHValidationParms: " + Platform.GetTypeName(obj), "obj");
		}
		
		public DHValidationParms(DerBitString seed, DerInteger pgenCounter)
		{
			if (seed == null)
				throw new ArgumentNullException("seed");
			if (pgenCounter == null)
				throw new ArgumentNullException("pgenCounter");

			this.seed = seed;
			this.pgenCounter = pgenCounter;
		}

		private DHValidationParms(Asn1Sequence seq)
		{
			if (seq.Count != 2)
				throw new ArgumentException("Bad sequence size: " + seq.Count, "seq");

			this.seed = DerBitString.GetInstance(seq[0]);
			this.pgenCounter = DerInteger.GetInstance(seq[1]);
		}

		public DerBitString Seed
		{
			get { return this.seed; }
		}

		public DerInteger PgenCounter
		{
			get { return this.pgenCounter; }
		}

		public override Asn1Object ToAsn1Object()
		{
			return new DerSequence(seed, pgenCounter);
		}
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x9/DHValidationParms.cs`.

**Classes defined**: DHValidationParms



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 51
- Comment lines: 0
- Blank lines: 14

### Main Components

**Classes** (1):
- `DHValidationParms`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

