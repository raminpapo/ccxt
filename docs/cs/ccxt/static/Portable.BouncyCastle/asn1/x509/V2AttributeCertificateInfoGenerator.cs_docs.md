# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V2AttributeCertificateInfoGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V2AttributeCertificateInfoGenerator.cs`
- **Size**: 3,814 bytes
- **Lines**: 138
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * Generator for Version 2 AttributeCertificateInfo
     * <pre>
     * AttributeCertificateInfo ::= Sequence {
     *       version              AttCertVersion -- version is v2,
     *       holder               Holder,
     *       issuer               AttCertIssuer,
     *       signature            AlgorithmIdentifier,
     *       serialNumber         CertificateSerialNumber,
     *       attrCertValidityPeriod   AttCertValidityPeriod,
     *       attributes           Sequence OF Attr,
     *       issuerUniqueID       UniqueIdentifier OPTIONAL,
     *       extensions           Extensions OPTIONAL
     * }
     * </pre>
     *
     */
    public class V2AttributeCertificateInfoGenerator
    {
        internal DerInteger				version;
        internal Holder					holder;
        internal AttCertIssuer			issuer;
        internal AlgorithmIdentifier	signature;
        internal DerInteger				serialNumber;
//        internal AttCertValidityPeriod	attrCertValidityPeriod;
        internal Asn1EncodableVector	attributes;
        internal DerBitString			issuerUniqueID;
        internal X509Extensions			extensions;
        internal DerGeneralizedTime		startDate, endDate;

		public V2AttributeCertificateInfoGenerator()
        {
            this.version = new DerInteger(1);
            attributes = new Asn1EncodableVector();
        }

		public void SetHolder(
			Holder holder)
        {
            this.holder = holder;
        }

		public void AddAttribute(
			string			oid,
			Asn1Encodable	value)
        {
            attributes.Add(new AttributeX509(new DerObjectIdentifier(oid), new DerSet(value)));
        }

		/**
         * @param attribute
         */
        public void AddAttribute(AttributeX509 attribute)
        {
            attributes.Add(attribute);
        }

		public void SetSerialNumber(
            DerInteger serialNumber)
        {
            this.serialNumber = serialNumber;
        }

		public void SetSignature(
            AlgorithmIdentifier signature)
        {
            this.signature = signature;
        }

		public void SetIssuer(
            AttCertIssuer issuer)
        {
            this.issuer = issuer;
        }

		public void SetStartDate(
            DerGeneralizedTime startDate)
        {
            this.startDate = startDate;
        }

		public void SetEndDate(
            DerGeneralizedTime endDate)
        {
            this.endDate = endDate;
        }

		public void SetIssuerUniqueID(
            DerBitString issuerUniqueID)
        {
            this.issuerUniqueID = issuerUniqueID;
        }

		public void SetExtensions(
            X509Extensions extensions)
        {
            this.extensions = extensions;
        }

		public AttributeCertificateInfo GenerateAttributeCertificateInfo()
        {
            if ((serialNumber == null) || (signature == null)
                || (issuer == null) || (startDate == null) || (endDate == null)
                || (holder == null) || (attributes == null))
            {
                throw new InvalidOperationException("not all mandatory fields set in V2 AttributeCertificateInfo generator");
            }

			Asn1EncodableVector v = new Asn1EncodableVector(
				version, holder, issuer, signature, serialNumber);

			//
            // before and after dates => AttCertValidityPeriod
            //
            v.Add(new AttCertValidityPeriod(startDate, endDate));

			// Attributes
            v.Add(new DerSequence(attributes));

			if (issuerUniqueID != null)
            {
                v.Add(issuerUniqueID);
            }

			if (extensions != null)
            {
                v.Add(extensions);
            }

			return AttributeCertificateInfo.GetInstance(new DerSequence(v));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V2AttributeCertificateInfoGenerator.cs`.

**Classes defined**: V2AttributeCertificateInfoGenerator

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 138
- Code lines: 113
- Comment lines: 25
- Blank lines: 0

### Main Components

**Classes** (1):
- `V2AttributeCertificateInfoGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

