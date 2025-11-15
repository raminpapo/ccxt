# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttributeCertificate.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttributeCertificate.cs`
- **Size**: 2,270 bytes
- **Lines**: 87
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1;

namespace Org.BouncyCastle.Asn1.X509
{
    public class AttributeCertificate
        : Asn1Encodable
    {
        private readonly AttributeCertificateInfo	acinfo;
        private readonly AlgorithmIdentifier		signatureAlgorithm;
        private readonly DerBitString				signatureValue;

		/**
         * @param obj
         * @return
         */
        public static AttributeCertificate GetInstance(
			object obj)
        {
            if (obj is AttributeCertificate)
                return (AttributeCertificate) obj;

			if (obj != null)
				return new AttributeCertificate(Asn1Sequence.GetInstance(obj));

			return null;
		}

		public AttributeCertificate(
            AttributeCertificateInfo	acinfo,
            AlgorithmIdentifier			signatureAlgorithm,
            DerBitString				signatureValue)
        {
            this.acinfo = acinfo;
            this.signatureAlgorithm = signatureAlgorithm;
            this.signatureValue = signatureValue;
        }

		private AttributeCertificate(
            Asn1Sequence seq)
        {
			if (seq.Count != 3)
				throw new ArgumentException("Bad sequence size: " + seq.Count);

			this.acinfo = AttributeCertificateInfo.GetInstance(seq[0]);
            this.signatureAlgorithm = AlgorithmIdentifier.GetInstance(seq[1]);
            this.signatureValue = DerBitString.GetInstance(seq[2]);
        }

		public AttributeCertificateInfo ACInfo
		{
			get { return acinfo; }
		}

		public AlgorithmIdentifier SignatureAlgorithm
		{
			get { return signatureAlgorithm; }
		}

		public DerBitString SignatureValue
		{
			get { return signatureValue; }
		}

        public byte[] GetSignatureOctets()
        {
            return signatureValue.GetOctets();
        }

        /**
         * Produce an object suitable for an Asn1OutputStream.
         * <pre>
         *  AttributeCertificate ::= Sequence {
         *       acinfo               AttributeCertificateInfo,
         *       signatureAlgorithm   AlgorithmIdentifier,
         *       signatureValue       BIT STRING
         *  }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(acinfo, signatureAlgorithm, signatureValue);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/AttributeCertificate.cs`.

**Classes defined**: AttributeCertificate

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 73
- Comment lines: 14
- Blank lines: 0

### Main Components

**Classes** (1):
- `AttributeCertificate`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

