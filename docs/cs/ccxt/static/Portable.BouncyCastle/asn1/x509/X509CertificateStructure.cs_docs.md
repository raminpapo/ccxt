# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509CertificateStructure.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509CertificateStructure.cs`
- **Size**: 3,470 bytes
- **Lines**: 133
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1.Pkcs;

namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * an X509Certificate structure.
     * <pre>
     *  Certificate ::= Sequence {
     *      tbsCertificate          TbsCertificate,
     *      signatureAlgorithm      AlgorithmIdentifier,
     *      signature               BIT STRING
     *  }
     * </pre>
     */
    public class X509CertificateStructure
        : Asn1Encodable
    {
        private readonly TbsCertificateStructure	tbsCert;
        private readonly AlgorithmIdentifier		sigAlgID;
        private readonly DerBitString				sig;

        public static X509CertificateStructure GetInstance(
            Asn1TaggedObject	obj,
            bool				explicitly)
        {
            return GetInstance(Asn1Sequence.GetInstance(obj, explicitly));
        }

        public static X509CertificateStructure GetInstance(
            object obj)
        {
            if (obj is X509CertificateStructure)
                return (X509CertificateStructure)obj;
            if (obj == null)
                return null;
            return new X509CertificateStructure(Asn1Sequence.GetInstance(obj));
        }

        public X509CertificateStructure(
            TbsCertificateStructure	tbsCert,
            AlgorithmIdentifier		sigAlgID,
            DerBitString			sig)
        {
            if (tbsCert == null)
                throw new ArgumentNullException("tbsCert");
            if (sigAlgID == null)
                throw new ArgumentNullException("sigAlgID");
            if (sig == null)
                throw new ArgumentNullException("sig");

            this.tbsCert = tbsCert;
            this.sigAlgID = sigAlgID;
            this.sig = sig;
        }

        private X509CertificateStructure(
            Asn1Sequence seq)
        {
            if (seq.Count != 3)
                throw new ArgumentException("sequence wrong size for a certificate", "seq");

            //
            // correct x509 certficate
            //
            tbsCert = TbsCertificateStructure.GetInstance(seq[0]);
            sigAlgID = AlgorithmIdentifier.GetInstance(seq[1]);
            sig = DerBitString.GetInstance(seq[2]);
        }

        public TbsCertificateStructure TbsCertificate
        {
            get { return tbsCert; }
        }

        public int Version
        {
            get { return tbsCert.Version; }
        }

        public DerInteger SerialNumber
        {
            get { return tbsCert.SerialNumber; }
        }

        public X509Name Issuer
        {
            get { return tbsCert.Issuer; }
        }

        public Time StartDate
        {
            get { return tbsCert.StartDate; }
        }

        public Time EndDate
        {
            get { return tbsCert.EndDate; }
        }

        public X509Name Subject
        {
            get { return tbsCert.Subject; }
        }

        public SubjectPublicKeyInfo SubjectPublicKeyInfo
        {
            get { return tbsCert.SubjectPublicKeyInfo; }
        }

        public AlgorithmIdentifier SignatureAlgorithm
        {
            get { return sigAlgID; }
        }

        public DerBitString Signature
        {
            get { return sig; }
        }

        public byte[] GetSignatureOctets()
        {
            return sig.GetOctets();
        }

        public override Asn1Object ToAsn1Object()
        {
            return new DerSequence(tbsCert, sigAlgID, sig);
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509CertificateStructure.cs`.

**Classes defined**: X509CertificateStructure

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 133
- Code lines: 109
- Comment lines: 13
- Blank lines: 11

### Main Components

**Classes** (1):
- `X509CertificateStructure`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
