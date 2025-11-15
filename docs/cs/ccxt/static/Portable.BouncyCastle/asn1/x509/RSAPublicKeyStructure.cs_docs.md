# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/RSAPublicKeyStructure.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/RSAPublicKeyStructure.cs`
- **Size**: 2,578 bytes
- **Lines**: 92
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Math;
using Org.BouncyCastle.Utilities;

namespace Org.BouncyCastle.Asn1.X509
{
    public class RsaPublicKeyStructure
        : Asn1Encodable
    {
        private BigInteger modulus;
        private BigInteger publicExponent;

		public static RsaPublicKeyStructure GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

		public static RsaPublicKeyStructure GetInstance(
            object obj)
        {
            if (obj == null || obj is RsaPublicKeyStructure)
            {
                return (RsaPublicKeyStructure) obj;
            }

			if (obj is Asn1Sequence)
            {
                return new RsaPublicKeyStructure((Asn1Sequence) obj);
            }

            throw new ArgumentException("Invalid RsaPublicKeyStructure: " + Platform.GetTypeName(obj));
        }

		public RsaPublicKeyStructure(
            BigInteger	modulus,
            BigInteger	publicExponent)
        {
			if (modulus == null)
				throw new ArgumentNullException("modulus");
			if (publicExponent == null)
				throw new ArgumentNullException("publicExponent");
			if (modulus.SignValue <= 0)
				throw new ArgumentException("Not a valid RSA modulus", "modulus");
			if (publicExponent.SignValue <= 0)
				throw new ArgumentException("Not a valid RSA public exponent", "publicExponent");

            this.modulus = modulus;
            this.publicExponent = publicExponent;
        }

		private RsaPublicKeyStructure(
            Asn1Sequence seq)
        {
			if (seq.Count != 2)
				throw new ArgumentException("Bad sequence size: " + seq.Count);

			// Note: we are accepting technically incorrect (i.e. negative) values here
			modulus = DerInteger.GetInstance(seq[0]).PositiveValue;
			publicExponent = DerInteger.GetInstance(seq[1]).PositiveValue;
		}

		public BigInteger Modulus
        {
            get { return modulus; }
        }

		public BigInteger PublicExponent
        {
            get { return publicExponent; }
        }

		/**
         * This outputs the key in Pkcs1v2 format.
         * <pre>
         *      RSAPublicKey ::= Sequence {
         *                          modulus Integer, -- n
         *                          publicExponent Integer, -- e
         *                      }
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
			return new DerSequence(
				new DerInteger(Modulus),
				new DerInteger(PublicExponent));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/RSAPublicKeyStructure.cs`.

**Classes defined**: RsaPublicKeyStructure

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 92
- Code lines: 77
- Comment lines: 10
- Blank lines: 5

### Main Components

**Classes** (1):
- `RsaPublicKeyStructure`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

