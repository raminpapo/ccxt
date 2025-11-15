# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyInformation.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyInformation.cs`
- **Size**: 1,928 bytes
- **Lines**: 76
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    public class PolicyInformation
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier	policyIdentifier;
        private readonly Asn1Sequence			policyQualifiers;

		private PolicyInformation(
            Asn1Sequence seq)
        {
			if (seq.Count < 1 || seq.Count > 2)
			{
				throw new ArgumentException("Bad sequence size: " + seq.Count);
			}

			policyIdentifier = DerObjectIdentifier.GetInstance(seq[0]);

			if (seq.Count > 1)
			{
				policyQualifiers = Asn1Sequence.GetInstance(seq[1]);
			}
        }

		public PolicyInformation(
            DerObjectIdentifier policyIdentifier)
        {
            this.policyIdentifier = policyIdentifier;
        }

		public PolicyInformation(
            DerObjectIdentifier	policyIdentifier,
            Asn1Sequence		policyQualifiers)
        {
            this.policyIdentifier = policyIdentifier;
            this.policyQualifiers = policyQualifiers;
        }

		public static PolicyInformation GetInstance(
            object obj)
        {
            if (obj == null || obj is PolicyInformation)
            {
                return (PolicyInformation) obj;
            }

			return new PolicyInformation(Asn1Sequence.GetInstance(obj));
        }

		public DerObjectIdentifier PolicyIdentifier
		{
			get { return policyIdentifier; }
		}

		public Asn1Sequence PolicyQualifiers
		{
			get { return policyQualifiers; }
		}

		/*
         * PolicyInformation ::= Sequence {
         *      policyIdentifier   CertPolicyId,
         *      policyQualifiers   Sequence SIZE (1..MAX) OF
         *              PolicyQualifierInfo OPTIONAL }
         */
        public override Asn1Object ToAsn1Object()
        {
            Asn1EncodableVector v = new Asn1EncodableVector(policyIdentifier);
            v.AddOptional(policyQualifiers);
            return new DerSequence(v);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyInformation.cs`.

**Classes defined**: PolicyInformation

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 64
- Comment lines: 6
- Blank lines: 6

### Main Components

**Classes** (1):
- `PolicyInformation`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

