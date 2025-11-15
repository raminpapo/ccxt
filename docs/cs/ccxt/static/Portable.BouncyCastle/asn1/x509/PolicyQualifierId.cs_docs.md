# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierId.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierId.cs`
- **Size**: 776 bytes
- **Lines**: 29
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1.X509
{
	/**
	 * PolicyQualifierId, used in the CertificatePolicies
	 * X509V3 extension.
	 *
	 * <pre>
	 *    id-qt          OBJECT IDENTIFIER ::=  { id-pkix 2 }
	 *    id-qt-cps      OBJECT IDENTIFIER ::=  { id-qt 1 }
	 *    id-qt-unotice  OBJECT IDENTIFIER ::=  { id-qt 2 }
	 *  PolicyQualifierId ::=
	 *       OBJECT IDENTIFIER ( id-qt-cps | id-qt-unotice )
	 * </pre>
	 */
	public sealed class PolicyQualifierID : DerObjectIdentifier
	{
		private const string IdQt = "1.3.6.1.5.5.7.2";

		private PolicyQualifierID(
			string id)
			: base(id)
		{
		}

		public static readonly PolicyQualifierID IdQtCps = new PolicyQualifierID(IdQt + ".1");
		public static readonly PolicyQualifierID IdQtUnotice = new PolicyQualifierID(IdQt + ".2");
	}
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/PolicyQualifierId.cs`.

**Classes defined**: PolicyQualifierID

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 26
- Comment lines: 12
- Blank lines: -9

### Main Components

**Classes** (1):
- `PolicyQualifierID`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

