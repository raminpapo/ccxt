# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509ObjectIdentifiers.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509ObjectIdentifiers.cs`
- **Size**: 2,958 bytes
- **Lines**: 62
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1.X509
{
    public abstract class X509ObjectIdentifiers
    {
        //
        // base id
        //
        internal const string ID = "2.5.4";

		public static readonly DerObjectIdentifier CommonName              = new DerObjectIdentifier(ID + ".3");
        public static readonly DerObjectIdentifier CountryName             = new DerObjectIdentifier(ID + ".6");
        public static readonly DerObjectIdentifier LocalityName            = new DerObjectIdentifier(ID + ".7");
        public static readonly DerObjectIdentifier StateOrProvinceName     = new DerObjectIdentifier(ID + ".8");
        public static readonly DerObjectIdentifier Organization            = new DerObjectIdentifier(ID + ".10");
        public static readonly DerObjectIdentifier OrganizationalUnitName  = new DerObjectIdentifier(ID + ".11");

		public static readonly DerObjectIdentifier id_at_telephoneNumber   = new DerObjectIdentifier(ID + ".20");
		public static readonly DerObjectIdentifier id_at_name              = new DerObjectIdentifier(ID + ".41");

        public static readonly DerObjectIdentifier id_at_organizationIdentifier = new DerObjectIdentifier("2.5.4.97");

        // id-SHA1 OBJECT IDENTIFIER ::=
        //   {iso(1) identified-organization(3) oiw(14) secsig(3) algorithms(2) 26 }    //
        public static readonly DerObjectIdentifier IdSha1 = new DerObjectIdentifier("1.3.14.3.2.26");

		//
        // ripemd160 OBJECT IDENTIFIER ::=
        //      {iso(1) identified-organization(3) TeleTrust(36) algorithm(3) hashAlgorithm(2) RipeMD-160(1)}
        //
        public static readonly DerObjectIdentifier RipeMD160 = new DerObjectIdentifier("1.3.36.3.2.1");

		//
        // ripemd160WithRSAEncryption OBJECT IDENTIFIER ::=
        //      {iso(1) identified-organization(3) TeleTrust(36) algorithm(3) signatureAlgorithm(3) rsaSignature(1) rsaSignatureWithripemd160(2) }
        //
        public static readonly DerObjectIdentifier RipeMD160WithRsaEncryption = new DerObjectIdentifier("1.3.36.3.3.1.2");

		public static readonly DerObjectIdentifier IdEARsa = new DerObjectIdentifier("2.5.8.1.1");

		// id-pkix
		public static readonly DerObjectIdentifier IdPkix = new DerObjectIdentifier("1.3.6.1.5.5.7");

		//
		// private internet extensions
		//
		public static readonly DerObjectIdentifier IdPE = new DerObjectIdentifier(IdPkix + ".1");

		//
		// authority information access
		//
		public static readonly DerObjectIdentifier IdAD = new DerObjectIdentifier(IdPkix + ".48");
		public static readonly DerObjectIdentifier IdADCAIssuers = new DerObjectIdentifier(IdAD + ".2");
		public static readonly DerObjectIdentifier IdADOcsp = new DerObjectIdentifier(IdAD + ".1");

		//
		// OID for ocsp and crl uri in AuthorityInformationAccess extension
		//
		public static readonly DerObjectIdentifier OcspAccessMethod = IdADOcsp;
		public static readonly DerObjectIdentifier CrlAccessMethod = IdADCAIssuers;
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/X509ObjectIdentifiers.cs`.

**Classes defined**: X509ObjectIdentifiers



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 27
- Comment lines: 23
- Blank lines: 12

### Main Components

**Classes** (1):
- `X509ObjectIdentifiers`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

