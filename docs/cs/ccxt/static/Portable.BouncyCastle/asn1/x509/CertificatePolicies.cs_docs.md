# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertificatePolicies.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertificatePolicies.cs`
- **Size**: 3,295 bytes
- **Lines**: 106
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;
using System.Text;

namespace Org.BouncyCastle.Asn1.X509
{
    public class CertificatePolicies
        : Asn1Encodable
    {
        private static PolicyInformation[] Copy(PolicyInformation[] policyInfo)
        {
            return (PolicyInformation[])policyInfo.Clone();
        }

        public static CertificatePolicies GetInstance(object obj)
        {
            if (obj is CertificatePolicies)
                return (CertificatePolicies)obj;
            if (obj == null)
                return null;
            return new CertificatePolicies(Asn1Sequence.GetInstance(obj));
        }

        public static CertificatePolicies GetInstance(Asn1TaggedObject obj, bool isExplicit)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, isExplicit));
        }

        public static CertificatePolicies FromExtensions(X509Extensions extensions)
        {
            return GetInstance(X509Extensions.GetExtensionParsedValue(extensions, X509Extensions.CertificatePolicies));
        }

        private readonly PolicyInformation[] policyInformation;

        /**
         * Construct a CertificatePolicies object containing one PolicyInformation.
         * 
         * @param name the name to be contained.
         */
        public CertificatePolicies(PolicyInformation name)
        {
            this.policyInformation = new PolicyInformation[] { name };
        }

        public CertificatePolicies(PolicyInformation[] policyInformation)
        {
            this.policyInformation = Copy(policyInformation);
        }

        private CertificatePolicies(Asn1Sequence seq)
        {
            this.policyInformation = new PolicyInformation[seq.Count];

            for (int i = 0; i < seq.Count; ++i)
            {
                policyInformation[i] = PolicyInformation.GetInstance(seq[i]);
            }
        }

        public virtual PolicyInformation[] GetPolicyInformation()
        {
            return Copy(policyInformation);
        }

        public virtual PolicyInformation GetPolicyInformation(DerObjectIdentifier policyIdentifier)
        {
            for (int i = 0; i != policyInformation.Length; i++)
            {
                if (policyIdentifier.Equals(policyInformation[i].PolicyIdentifier))
                {
                    return policyInformation[i];
                }
            }

            return null;
        }

        /**
         * Produce an object suitable for an ASN1OutputStream.
         * <pre>
         * CertificatePolicies ::= SEQUENCE SIZE {1..MAX} OF PolicyInformation
         * </pre>
         */
        public override Asn1Object ToAsn1Object()
        {
            return new DerSequence(policyInformation);
        }

        public override string ToString()
        {
            StringBuilder sb = new StringBuilder("CertificatePolicies:");
            if (policyInformation != null && policyInformation.Length > 0)
            {
                sb.Append(' ');
                sb.Append(policyInformation[0]);
                for (int i = 1; i < policyInformation.Length; ++i)
                {
                    sb.Append(", ");
                    sb.Append(policyInformation[i]);
                }
            }
            return sb.ToString();
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertificatePolicies.cs`.

**Classes defined**: CertificatePolicies

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 106
- Code lines: 91
- Comment lines: 11
- Blank lines: 4

### Main Components

**Classes** (1):
- `CertificatePolicies`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

