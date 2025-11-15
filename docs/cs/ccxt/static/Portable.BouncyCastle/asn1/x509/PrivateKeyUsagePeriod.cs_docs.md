# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PrivateKeyUsagePeriod.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PrivateKeyUsagePeriod.cs`
- **Size**: 1,651 bytes
- **Lines**: 76
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
	/// <remarks>
	/// <pre>
	/// PrivateKeyUsagePeriod ::= SEQUENCE
	/// {
	/// notBefore       [0]     GeneralizedTime OPTIONAL,
	/// notAfter        [1]     GeneralizedTime OPTIONAL }
	/// </pre>
	/// </remarks>
	public class PrivateKeyUsagePeriod
		: Asn1Encodable
	{
		public static PrivateKeyUsagePeriod GetInstance(
			object obj)
		{
			if (obj is PrivateKeyUsagePeriod)
			{
				return (PrivateKeyUsagePeriod) obj;
			}

			if (obj is Asn1Sequence)
			{
				return new PrivateKeyUsagePeriod((Asn1Sequence) obj);
			}

			if (obj is X509Extension)
			{
				return GetInstance(X509Extension.ConvertValueToObject((X509Extension) obj));
			}

			throw new ArgumentException("unknown object in GetInstance: " + Platform.GetTypeName(obj), "obj");
		}

		private DerGeneralizedTime _notBefore, _notAfter;

		private PrivateKeyUsagePeriod(
			Asn1Sequence seq)
		{
			foreach (Asn1TaggedObject tObj in seq)
			{
				if (tObj.TagNo == 0)
				{
					_notBefore = DerGeneralizedTime.GetInstance(tObj, false);
				}
				else if (tObj.TagNo == 1)
				{
					_notAfter = DerGeneralizedTime.GetInstance(tObj, false);
				}
			}
		}

		public DerGeneralizedTime NotBefore
		{
			get { return _notBefore; }
		}

		public DerGeneralizedTime NotAfter
		{
			get { return _notAfter; }
		}

        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector();
            v.AddOptionalTagged(false, 0, _notBefore);
            v.AddOptionalTagged(false, 1, _notAfter);
            return new DerSequence(v);
        }
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PrivateKeyUsagePeriod.cs`.

**Classes defined**: PrivateKeyUsagePeriod



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 57
- Comment lines: 8
- Blank lines: 11

### Main Components

**Classes** (1):
- `PrivateKeyUsagePeriod`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

