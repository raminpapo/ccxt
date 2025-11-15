# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V1TBSCertificateGenerator.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V1TBSCertificateGenerator.cs`
- **Size**: 2,888 bytes
- **Lines**: 109
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * Generator for Version 1 TbsCertificateStructures.
     * <pre>
     * TbsCertificate ::= Sequence {
     *      version          [ 0 ]  Version DEFAULT v1(0),
     *      serialNumber            CertificateSerialNumber,
     *      signature               AlgorithmIdentifier,
     *      issuer                  Name,
     *      validity                Validity,
     *      subject                 Name,
     *      subjectPublicKeyInfo    SubjectPublicKeyInfo,
     *      }
     * </pre>
     *
     */
    public class V1TbsCertificateGenerator
    {
        internal DerTaggedObject		version = new DerTaggedObject(0, new DerInteger(0));
        internal DerInteger				serialNumber;
        internal AlgorithmIdentifier	signature;
        internal X509Name				issuer;
        internal Time					startDate, endDate;
        internal X509Name				subject;
        internal SubjectPublicKeyInfo	subjectPublicKeyInfo;

		public V1TbsCertificateGenerator()
        {
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
            X509Name issuer)
        {
            this.issuer = issuer;
        }

		public void SetStartDate(
            Time startDate)
        {
            this.startDate = startDate;
        }

		public void SetStartDate(
            DerUtcTime startDate)
        {
            this.startDate = new Time(startDate);
        }

		public void SetEndDate(
            Time endDate)
        {
            this.endDate = endDate;
        }

		public void SetEndDate(
            DerUtcTime endDate)
        {
            this.endDate = new Time(endDate);
        }

		public void SetSubject(
            X509Name subject)
        {
            this.subject = subject;
        }

		public void SetSubjectPublicKeyInfo(
            SubjectPublicKeyInfo pubKeyInfo)
        {
            this.subjectPublicKeyInfo = pubKeyInfo;
        }

		public TbsCertificateStructure GenerateTbsCertificate()
        {
            if ((serialNumber == null) || (signature == null)
                || (issuer == null) || (startDate == null) || (endDate == null)
                || (subject == null) || (subjectPublicKeyInfo == null))
            {
                throw new InvalidOperationException("not all mandatory fields set in V1 TBScertificate generator");
            }

			return new TbsCertificateStructure(
				new DerSequence(
					//version, - not required as default value
					serialNumber,
					signature,
					issuer,
					new DerSequence(startDate, endDate), // before and after dates
					subject,
					subjectPublicKeyInfo));
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/V1TBSCertificateGenerator.cs`.

**Classes defined**: V1TbsCertificateGenerator

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 109
- Code lines: 94
- Comment lines: 16
- Blank lines: -1

### Main Components

**Classes** (1):
- `V1TbsCertificateGenerator`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

