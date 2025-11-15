# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertPolicyId.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertPolicyId.cs`
- **Size**: 381 bytes
- **Lines**: 21
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * CertPolicyId, used in the CertificatePolicies and PolicyMappings
     * X509V3 Extensions.
     *
     * <pre>
     *     CertPolicyId ::= OBJECT IDENTIFIER
     * </pre>
     */
     public class CertPolicyID
		 : DerObjectIdentifier
    {
       public CertPolicyID(
		   string id)
		   : base(id)
       {
       }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/CertPolicyId.cs`.

**Classes defined**: CertPolicyID

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 20
- Comment lines: 8
- Blank lines: -7

### Main Components

**Classes** (1):
- `CertPolicyID`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

