# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/IVerifier.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/IVerifier.cs`
- **Size**: 1,156 bytes
- **Lines**: 26
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿namespace Org.BouncyCastle.Crypto
{
    /// <summary>
    /// Operators that reduce their input to the validation of a signature produce this type.
    /// </summary>
    public interface IVerifier
    {
        /// <summary>
        /// Return true if the passed in data matches what is expected by the verification result.
        /// </summary>
        /// <param name="data">The bytes representing the signature.</param>
        /// <returns>true if the signature verifies, false otherwise.</returns>
        bool IsVerified(byte[] data);

        /// <summary>
        /// Return true if the length bytes from off in the source array match the signature
        /// expected by the verification result.
        /// </summary>
        /// <param name="source">Byte array containing the signature.</param>
        /// <param name="off">The offset into the source array where the signature starts.</param>
        /// <param name="length">The number of bytes in source making up the signature.</param>
        /// <returns>true if the signature verifies, false otherwise.</returns>
        bool IsVerified(byte[] source, int off, int length);
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/IVerifier.cs`.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 8
- Comment lines: 16
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

