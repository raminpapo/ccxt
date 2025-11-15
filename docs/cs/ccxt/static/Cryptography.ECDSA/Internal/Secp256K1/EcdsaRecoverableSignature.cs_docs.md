# Documentation: cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/EcdsaRecoverableSignature.cs

## File Metadata

- **Path**: `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/EcdsaRecoverableSignature.cs`
- **Size**: 961 bytes
- **Lines**: 23
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
namespace Cryptography.ECDSA.Internal.Secp256K1
{
    /// <summary>
    /// Opaque data structured that holds a parsed ECDSA signature,
    /// supporting pubkey recovery.
    /// 
    /// The exact representation of data inside is implementation defined and not
    /// guaranteed to be portable between different platforms or versions. It is
    /// however guaranteed to be 65 bytes in size, and can be safely copied/moved.
    /// If you need to convert to a format suitable for storage or transmission, use
    /// the secp256k1_ecdsa_signature_serialize_* and
    /// secp256k1_ecdsa_signature_parse_* functions.
    /// 
    /// Furthermore, it is guaranteed that identical signatures (including their
    /// recoverability) will have identical representation, so they can be
    /// memcmp'ed.
    /// </summary>
    internal class EcdsaRecoverableSignature
    {
        public const int Size = 65;
        public byte[] Data = new byte[Size];
    }
}
```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Cryptography.ECDSA/Internal/Secp256K1/EcdsaRecoverableSignature.cs`.

**Classes defined**: EcdsaRecoverableSignature



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 8
- Comment lines: 15
- Blank lines: 0

### Main Components

**Classes** (1):
- `EcdsaRecoverableSignature`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

