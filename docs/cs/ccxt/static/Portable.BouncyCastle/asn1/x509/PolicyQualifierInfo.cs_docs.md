# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierInfo.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierInfo.cs`
- **Size**: 2,832 bytes
- **Lines**: 96
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * Policy qualifiers, used in the X509V3 CertificatePolicies
     * extension.
     *
     * <pre>
     *   PolicyQualifierInfo ::= Sequence {
     *       policyQualifierId  PolicyQualifierId,
     *       qualifier          ANY DEFINED BY policyQualifierId }
     * </pre>
     */
    public class PolicyQualifierInfo
        : Asn1Encodable
    {
        private readonly DerObjectIdentifier policyQualifierId;
        private readonly Asn1Encodable qualifier;

        /**
         * Creates a new <code>PolicyQualifierInfo</code> instance.
         *
         * @param policyQualifierId a <code>PolicyQualifierId</code> value
         * @param qualifier the qualifier, defined by the above field.
         */
        public PolicyQualifierInfo(
            DerObjectIdentifier	policyQualifierId,
            Asn1Encodable		qualifier)
        {
            this.policyQualifierId = policyQualifierId;
            this.qualifier = qualifier;
        }

        /**
         * Creates a new <code>PolicyQualifierInfo</code> containing a
         * cPSuri qualifier.
         *
         * @param cps the CPS (certification practice statement) uri as a
         * <code>string</code>.
         */
        public PolicyQualifierInfo(
            string cps)
        {
            policyQualifierId = PolicyQualifierID.IdQtCps;
            qualifier = new DerIA5String(cps);
        }

        /**
         * Creates a new <code>PolicyQualifierInfo</code> instance.
         *
         * @param as <code>PolicyQualifierInfo</code> X509 structure
         * encoded as an Asn1Sequence.
         */
        private PolicyQualifierInfo(
            Asn1Sequence seq)
        {
            if (seq.Count != 2)
                throw new ArgumentException("Bad sequence size: " + seq.Count, "seq");

            policyQualifierId = DerObjectIdentifier.GetInstance(seq[0]);
            qualifier = seq[1];
        }

        public static PolicyQualifierInfo GetInstance(
            object obj)
        {
            if (obj is PolicyQualifierInfo)
                return (PolicyQualifierInfo)obj;
            if (obj == null)
                return null;
            return new PolicyQualifierInfo(Asn1Sequence.GetInstance(obj));
        }

        public virtual DerObjectIdentifier PolicyQualifierId
        {
            get { return policyQualifierId; }
        }

        public virtual Asn1Encodable Qualifier
        {
            get { return qualifier; }
        }

        /**
         * Returns a Der-encodable representation of this instance.
         *
         * @return a <code>Asn1Object</code> value
         */
        public override Asn1Object ToAsn1Object()
        {
            return new DerSequence(policyQualifierId, qualifier);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierInfo.cs`.

**Classes defined**: PolicyQualifierInfo

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 96
- Code lines: 86
- Comment lines: 34
- Blank lines: -24

### Main Components

**Classes** (1):
- `PolicyQualifierInfo`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

