# Documentation: cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureResult.cs

## File Metadata

- **Path**: `cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureResult.cs`
- **Size**: 838 bytes
- **Lines**: 37
- **Type**: C#
- **Extension**: .cs


## Original Source Code

```csharp
﻿using System;

namespace Org.BouncyCastle.Crypto.Operators
{
    public class DefaultSignatureResult
        : IBlockResult
    {
        private readonly ISigner mSigner;

        public DefaultSignatureResult(ISigner signer)
        {
            this.mSigner = signer;
        }

        public byte[] Collect()
        {
            return mSigner.GenerateSignature();
        }

        public int Collect(byte[] sig, int sigOff)
        {
            byte[] signature = Collect();
            signature.CopyTo(sig, sigOff);
            return signature.Length;
        }

#if NETCOREAPP2_1_OR_GREATER || NETSTANDARD2_1_OR_GREATER
        public int Collect(Span<byte> destination)
        {
            byte[] result = Collect();
            result.CopyTo(destination);
            return result.Length;
        }
#endif
    }
}

```

## High-Level Overview

This is a C# file located at `cs/ccxt/static/Portable.BouncyCastle/crypto/operators/DefaultSignatureResult.cs`.

**Classes defined**: DefaultSignatureResult



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 29
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `DefaultSignatureResult`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this C# file:**

