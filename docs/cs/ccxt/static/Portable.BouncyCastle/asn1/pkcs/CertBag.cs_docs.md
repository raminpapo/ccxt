# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/CertBag.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/CertBag.cs`
- **Size**: 1,268 bytes
- **Lines**: 53
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.Pkcs
{
    public class CertBag
        : Asn1Encodable
    {
        public static CertBag GetInstance(object obj)
        {
            if (obj is CertBag)
                return (CertBag)obj;
            if (obj == null)
                return null;
            return new CertBag(Asn1Sequence.GetInstance(obj));
        }

        private readonly DerObjectIdentifier certID;
        private readonly Asn1Object certValue;

		private CertBag(Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Wrong number of elements in sequence", "seq");

            this.certID = DerObjectIdentifier.GetInstance(seq[0]);
            this.certValue = Asn1TaggedObject.GetInstance(seq[1]).GetObject();
        }

		public CertBag(
            DerObjectIdentifier	certID,
            Asn1Object			certValue)
        {
            this.certID = certID;
            this.certValue = certValue;
        }

		public virtual DerObjectIdentifier CertID
		{
			get { return certID; }
		}

		public virtual Asn1Object CertValue
		{
			get { return certValue; }
		}

		public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(certID, new DerTaggedObject(0, certValue));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/pkcs/CertBag.cs`.

**Classes defined**: CertBag



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 44
- Comment lines: 0
- Blank lines: 9

### Main Components

**Classes** (1):
- `CertBag`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

