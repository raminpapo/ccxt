# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/IssuerSerial.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/IssuerSerial.cs`
- **Size**: 2,197 bytes
- **Lines**: 95
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    public class IssuerSerial
        : Asn1Encodable
    {
        internal readonly GeneralNames	issuer;
        internal readonly DerInteger	serial;
        internal readonly DerBitString	issuerUid;

		public static IssuerSerial GetInstance(
            object obj)
        {
            if (obj == null || obj is IssuerSerial)
            {
                return (IssuerSerial) obj;
            }

			if (obj is Asn1Sequence)
            {
                return new IssuerSerial((Asn1Sequence) obj);
            }

            throw new ArgumentException("unknown object in factory: " + Platform.GetTypeName(obj), "obj");
		}

        public static IssuerSerial GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

		private IssuerSerial(
            Asn1Sequence seq)
        {
			if (seq.Count != 2 && seq.Count != 3)
			{
				throw new ArgumentException("Bad sequence size: " + seq.Count);
			}

			issuer = GeneralNames.GetInstance(seq[0]);
			serial = DerInteger.GetInstance(seq[1]);

			if (seq.Count == 3)
            {
				issuerUid = DerBitString.GetInstance(seq[2]);
			}
        }

		public IssuerSerial(
			GeneralNames	issuer,
			DerInteger		serial)
		{
			this.issuer = issuer;
			this.serial = serial;
		}

		public GeneralNames Issuer
		{
			get { return issuer; }
		}

		public DerInteger Serial
		{
			get { return serial; }
		}

		public DerBitString IssuerUid
		{
			get { return issuerUid; }
		}

		/**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         *  IssuerSerial  ::=  Sequence {
         *       issuer         GeneralNames,
         *       serial         CertificateSerialNumber,
         *       issuerUid      UniqueIdentifier OPTIONAL
         *  }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector(issuer, serial);
            v.AddOptional(issuerUid);
            return new DerSequence(v);
        }
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/IssuerSerial.cs`.

**Classes defined**: IssuerSerial

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 95
- Code lines: 80
- Comment lines: 10
- Blank lines: 5

### Main Components

**Classes** (1):
- `IssuerSerial`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

