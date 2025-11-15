# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/KeyPurposeId.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/KeyPurposeId.cs`
- **Size**: 1,595 bytes
- **Lines**: 39
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * The KeyPurposeID object.
     * <pre>
     *     KeyPurposeID ::= OBJECT IDENTIFIER
     * </pre>
     */
    public sealed class KeyPurposeID
        : DerObjectIdentifier
    {
        private const string IdKP = "1.3.6.1.5.5.7.3";

		private KeyPurposeID(
			string id)
			: base(id)
        {
        }

		public static readonly KeyPurposeID AnyExtendedKeyUsage = new KeyPurposeID(X509Extensions.ExtendedKeyUsage.Id + ".0");
        public static readonly KeyPurposeID IdKPServerAuth = new KeyPurposeID(IdKP + ".1");
        public static readonly KeyPurposeID IdKPClientAuth = new KeyPurposeID(IdKP + ".2");
        public static readonly KeyPurposeID IdKPCodeSigning = new KeyPurposeID(IdKP + ".3");
        public static readonly KeyPurposeID IdKPEmailProtection = new KeyPurposeID(IdKP + ".4");
        public static readonly KeyPurposeID IdKPIpsecEndSystem = new KeyPurposeID(IdKP + ".5");
        public static readonly KeyPurposeID IdKPIpsecTunnel = new KeyPurposeID(IdKP + ".6");
        public static readonly KeyPurposeID IdKPIpsecUser = new KeyPurposeID(IdKP + ".7");
        public static readonly KeyPurposeID IdKPTimeStamping = new KeyPurposeID(IdKP + ".8");
        public static readonly KeyPurposeID IdKPOcspSigning = new KeyPurposeID(IdKP + ".9");

		//
        // microsoft key purpose ids
        //
        public static readonly KeyPurposeID IdKPSmartCardLogon = new KeyPurposeID("1.3.6.1.4.1.311.20.2.2");

        public static readonly KeyPurposeID IdKPMacAddress = new KeyPurposeID("1.3.6.1.1.1.1.22");
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/KeyPurposeId.cs`.

**Classes defined**: KeyPurposeID

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 31
- Comment lines: 9
- Blank lines: -1

### Main Components

**Classes** (1):
- `KeyPurposeID`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

