# Documentation: cs/ccxt/static/Portable.BouncyCastle/asn1/x509/ReasonFlags.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/ReasonFlags.cs`
- **Size**: 1,325 bytes
- **Lines**: 46
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Org.BouncyCastle.Asn1.X509
{
    /**
     * The ReasonFlags object.
     * <pre>
     * ReasonFlags ::= BIT STRING {
     *    unused(0),
     *    keyCompromise(1),
     *    cACompromise(2),
     *    affiliationChanged(3),
     *    superseded(4),
     *    cessationOfOperation(5),
     *    certficateHold(6)
     * }
     * </pre>
     */
    public class ReasonFlags
        : DerBitString
    {
        public const int Unused                 = (1 << 7);
        public const int KeyCompromise          = (1 << 6);
        public const int CACompromise           = (1 << 5);
        public const int AffiliationChanged     = (1 << 4);
        public const int Superseded             = (1 << 3);
        public const int CessationOfOperation   = (1 << 2);
        public const int CertificateHold        = (1 << 1);
        public const int PrivilegeWithdrawn     = (1 << 0);
        public const int AACompromise           = (1 << 15);

		/**
         * @param reasons - the bitwise OR of the Key Reason flags giving the
         * allowed uses for the key.
         */
        public ReasonFlags(int reasons)
             : base(reasons)
        {
        }

        public ReasonFlags(
            DerBitString reasons)
             : base(reasons.GetBytes(), reasons.PadBits)
        {
        }
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/asn1/x509/ReasonFlags.cs`.

**Classes defined**: ReasonFlags

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 43
- Comment lines: 18
- Blank lines: -15

### Main Components

**Classes** (1):
- `ReasonFlags`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

