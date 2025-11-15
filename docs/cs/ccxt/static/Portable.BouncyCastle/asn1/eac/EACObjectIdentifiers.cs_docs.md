# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/eac/EACObjectIdentifiers.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/eac/EACObjectIdentifiers.cs`
- **Size**: 2,779 bytes
- **Lines**: 51
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
using System;

using Org.BouncyCastle.Asn1;

namespace Org.BouncyCastle.Asn1.Eac
{
	public abstract class EacObjectIdentifiers
	{
		// bsi-de OBJECT IDENTIFIER ::= {
		//         itu-t(0) identified-organization(4) etsi(0)
		//         reserved(127) etsi-identified-organization(0) 7
		//     }
		public static readonly DerObjectIdentifier bsi_de = new DerObjectIdentifier("0.4.0.127.0.7");

		// id-PK OBJECT IDENTIFIER ::= {
		//         bsi-de protocols(2) smartcard(2) 1
		//     }
		public static readonly DerObjectIdentifier id_PK = new DerObjectIdentifier(bsi_de + ".2.2.1");

		public static readonly DerObjectIdentifier id_PK_DH = new DerObjectIdentifier(id_PK + ".1");
		public static readonly DerObjectIdentifier id_PK_ECDH = new DerObjectIdentifier(id_PK + ".2");

		// id-CA OBJECT IDENTIFIER ::= {
		//         bsi-de protocols(2) smartcard(2) 3
		//     }
		public static readonly DerObjectIdentifier id_CA = new DerObjectIdentifier(bsi_de + ".2.2.3");
		public static readonly DerObjectIdentifier id_CA_DH = new DerObjectIdentifier(id_CA + ".1");
		public static readonly DerObjectIdentifier id_CA_DH_3DES_CBC_CBC = new DerObjectIdentifier(id_CA_DH + ".1");
		public static readonly DerObjectIdentifier id_CA_ECDH = new DerObjectIdentifier(id_CA + ".2");
		public static readonly DerObjectIdentifier id_CA_ECDH_3DES_CBC_CBC = new DerObjectIdentifier(id_CA_ECDH + ".1");

		//
		// id-TA OBJECT IDENTIFIER ::= {
		//     bsi-de protocols(2) smartcard(2) 2
		// }
		public static readonly DerObjectIdentifier id_TA = new DerObjectIdentifier(bsi_de + ".2.2.2");

		public static readonly DerObjectIdentifier id_TA_RSA = new DerObjectIdentifier(id_TA + ".1");
		public static readonly DerObjectIdentifier id_TA_RSA_v1_5_SHA_1 = new DerObjectIdentifier(id_TA_RSA + ".1");
		public static readonly DerObjectIdentifier id_TA_RSA_v1_5_SHA_256 = new DerObjectIdentifier(id_TA_RSA + ".2");
		public static readonly DerObjectIdentifier id_TA_RSA_PSS_SHA_1 = new DerObjectIdentifier(id_TA_RSA + ".3");
		public static readonly DerObjectIdentifier id_TA_RSA_PSS_SHA_256 = new DerObjectIdentifier(id_TA_RSA + ".4");
		public static readonly DerObjectIdentifier id_TA_ECDSA = new DerObjectIdentifier(id_TA + ".2");
		public static readonly DerObjectIdentifier id_TA_ECDSA_SHA_1 = new DerObjectIdentifier(id_TA_ECDSA + ".1");
		public static readonly DerObjectIdentifier id_TA_ECDSA_SHA_224 = new DerObjectIdentifier(id_TA_ECDSA + ".2");
		public static readonly DerObjectIdentifier id_TA_ECDSA_SHA_256 = new DerObjectIdentifier(id_TA_ECDSA + ".3");
		public static readonly DerObjectIdentifier id_TA_ECDSA_SHA_384 = new DerObjectIdentifier(id_TA_ECDSA + ".4");
		public static readonly DerObjectIdentifier id_TA_ECDSA_SHA_512 = new DerObjectIdentifier(id_TA_ECDSA + ".5");
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/eac/EACObjectIdentifiers.cs`.

**Classes defined**: EacObjectIdentifiers



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 29
- Comment lines: 14
- Blank lines: 8

### Main Components

**Classes** (1):
- `EacObjectIdentifiers`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

